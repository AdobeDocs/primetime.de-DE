---
description: Passen Sie Ihre Referenzimplementierung an, um die Adobe Primetime-Authentifizierung für Ihre Produktionsumgebung zu integrieren.
title: Integrieren der Primetime-Authentifizierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Integrieren der Primetime-Authentifizierung {#integrate-primetime-authentication}

Passen Sie Ihre Referenzimplementierung an, um die Adobe Primetime-Authentifizierung für Ihre Produktionsumgebung zu integrieren.

Die Integration der Referenzimplementierung des Primetime-Authentifizierungsdienstes funktioniert standardmäßig als Demonstration. Um die Integration jedoch in einem produktionsbereiten Player zu verwenden, müssen Sie die folgenden Anpassungen implementieren:

1. Berechtigungsflüsse aktivieren oder deaktivieren.

   Die `EntitlementManager` muss zuerst initialisieren und eine Instanz des Primetime-Authentifizierungs-SDK abrufen, damit sie aktiviert werden kann. Wenn die Variable `EntitlementManager` diese Bibliothek nicht initialisiert, wird der Manager deaktiviert.
1. Aktivieren Sie die `EntitlementManger`, aus Ihrer Hauptanwendungsklasse:

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. Verwenden Sie die `ManagerFactory` -Klasse, um eine Instanz der `EntitlementManager`.

   Sie müssen immer die `ManagerFactory` , um eine Instanz der `EntitlementManager`als `ManagerFactory` verwaltet eine einzelne Instanz des EntitlementManager für Ihre Anwendung. Instanziieren Sie niemals die `EntitlementManager` oder `EntitlementManagerOn` -Klassen durch Verwendung ihrer -Konstruktoren.

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   Die `ManagerFactory` gibt eine Instanz von `EntitlementManagerOn`, wobei die Berechtigungsflüsse aktiviert sind, falls Sie zuvor `EntitlementManager.initializeAccessEnabler`. Wenn Sie nicht den ersten Aufruf `EntitlementManager.initializeAccessEnabler`, dann die `ManagerFactory` gibt eine Instanz von `EntitlementManager`, wobei die Berechtigungsflüsse deaktiviert sind. 1. Konfigurieren Sie die Anforderer-ID.

   Die Referenzimplementierung ist vorkonfiguriert und die Test-Anforderer-ID ist auf &quot;REF&quot;festgelegt. Sie können diese Anforderer-ID verwenden, um Ihre Anwendung zu testen. Wenn Sie die Anforderer-ID verwenden möchten, die Ihnen Ihr Primetime-Authentifizierungsagent zur Verfügung stellt, aktualisieren Sie die [!DNL res/values/strings.xml] -Datei mit Ihrer Anforderer-ID.

   ```xml
   <!-- Programmer Requestor ID, change to ID provided by your Adobe  
        Primetime pay-TV pass representative --> 
   <string name="adobepass_requestor_id">REF</string> 
   
   <!-- Adobe Primetime pay-TV pass service provider endpoint for production 
        environment --> 
   <string name="adobepass_sp_url_production">sp.auth.adobe.com</string> 
   
   <!-- Adobe Primetime pay-TV pass service provider endpoint for staging  
        environment --> 
   <string name="adobepass_sp_url_staging">sp.auth-staging.adobe.com</string>
   ```

   Darüber hinaus müssen Sie möglicherweise die URLs ändern, die Ihre Anwendung verwendet, um eine Verbindung zu den Primetime-Authentifizierungsdiensten herzustellen. Dazu gehören die Primetime-Authentifizierungs-Staging- und Produktionsserver-URLs sowie eine URL zu einem Token Verification Service. Weitere Informationen erhalten Sie von Ihrem Adobe Primetime-Support-Mitarbeiter. 1. Unterschreiben Sie die Anforderer-ID.

   Um die Identität des Programmierers im Primetime-Authentifizierungssystem zu ermitteln, wird die Anforderungs-ID des Programmierers an das Primetime-Authentifizierungssystem gesendet. Als zusätzliche Sicherheitsschicht muss die Anforderer-ID vom Programmierer signiert werden, bevor sie an Adobe gesendet wird. Adobe empfiehlt dem Programmierer, einen Dienst zum Signieren der Anforderer-ID in einem vertrauenswürdigen Netzwerk einzurichten.

   Die Primetime-Referenzimplementierung zeigt, wie die Anforderer-ID signiert wird. Dies dient jedoch nur zu Demonstrationszwecken. Adobe empfiehlt dringend, dass das Signaturzertifikat und der Signaturgeneratorcode unter `com.adobe.primetime.reference.crypto`, sollte nicht in eine Produktionsanwendung einbezogen werden. Stattdessen sollten Sie ihn in einen vertrauenswürdigen Netzwerkdienst verschieben.

1. Konfigurieren Sie die Serverumgebung.

   Der Primetime-Authentifizierungsdienst kann in zwei separaten Umgebungen ausgeführt werden:

   * Staging : Die Staging-Umgebung wird zum Testen Ihrer Anwendung verwendet.
   * Produktion - Die Produktionsumgebung wird für Live-Bereitstellungen Ihrer Anwendung verwendet.

   Sie legen die URIs sowohl für die Staging- als auch für die Produktionsumgebung mit der Anwendung fest. Sie müssen jedoch festlegen, welche dieser URIs von der Anwendung im Code verwendet wird. Im `com.adobe.primetime.reference.manager.EntitlementManger` -Klasse, legen Sie die `environmentUri` entweder `STAGING_URI` oder `PRODUCTION_URI` je nachdem, welche Primetime-Authentifizierungsdienst-Umgebung Sie verwenden.

   >[!NOTE]
   >
   >Die bereitgestellte Anforderer-ID (&quot;REF&quot;) sollte nur in der Staging-Umgebung verwendet werden.

   `com.adobe.primetime.reference.manager.EntitlementManager`:

   ```java
     // Adobe Primetime authentication service provider endpoint for production environment 
     PRODUCTION_URI = 
         application.getResources().getString(R.string.adobepass_sp_url_production); 
   
     // Adobe Primetime authentication service provider endpoint for staging environment 
     STAGING_URI = 
       application.getResources().getString(R.string.adobepass_sp_url_staging); 
   
     // Set to STAGING_URI when testing against the staging/test environment 
     // Set to PRODUCTION_URI when deploying the application for production use 
     String environmentUri = STAGING_URI; 
   
     // Adobe Primetime authentication service URI used by this application 
     PAYTV_PASS_URI = environmentUri + "/adobe-services"; 
   
     // Token Verification Service URL 
     TVS_URL = "https://" + environmentUri + "/tvs/v1/validate";
   ```

1. Anpassen des MVPD-Auswahlrasters.

   Auf der Seite zur Auswahl des Inhaltsanbieters wird eine Tabelle der neun wichtigsten MVPDs angezeigt, aus denen der Benutzer auswählen kann. Die Anwendung ruft die neun wichtigsten MVPDs aus einer geordneten Liste innerhalb der Anwendung ab, die mit den verfügbaren MVPDs übereinstimmen, die mit dem Programmer im Primetime-Authentifizierungssystem integriert sind. Die geordnete Liste der primären MVPDs wird auf der MVPD-ID innerhalb des Primetime-Authentifizierungs-Systems und nicht auf dem MVPD-Anzeigenamen angegeben. Es ist wichtig zu überprüfen, ob die MVPD-IDs in der Liste der primären MVPDs mit den MVPD-IDs übereinstimmen, die mit dem -Konto des Programmierers integriert sind, da die IDs in einigen Fällen von Integrationen unterschiedlich sein können. Nachstehend finden Sie die geordnete Liste der primären MVPDs, die in der Klasse zu finden sind. `com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment`.

   ```java
   /* Array of MVPDs to display in a Grid of icons 
   When displaying a grid, only the MVPDs which intersect this array and the 
   ArrayList of all MVPDs are displayed. 
   The array contents are ordered by display preference as only a maximum of 
   MAX_DISPLAY_ICONS are displayed. 
   */ 
   private static final String[] PRIMARY_MVPDS = { 
   "Comcast_SSO",                         // Comcast XFINITY 
   "DTV",                                 // DirectTV 
   "Dish",                                // Dish 
   "TWC",                                 // Time Warner Cable 
   "Cox",                                 // Cox 
   "Charter_Direct",                      // Charter 
   "Verizon",                             // Verizon FiOS 
   "Cablevision",                         // Cablevision Optimum 
   "ATT",                                 // AT&T U-verse 
   "Brighthouse",                         // Brighthouse 
   "Suddenlink",                          // Suddenlink 
   "Mediacom",                            // Mediacom 
   "CableOne",                            // CableOne 
   "WOW",                                 // WOW! 
   "RCN",                                 // RCN 
   "auth_atlanticbb_net",                 // Atlantic Broadband 
   "auth_armstrongmywire_com",            // Armstrong 
   "knology_auth-gateway_net",            // KNOLOGY 
   "serviceelectric_auth-gateway_net",    // Service Electric Cablevision 
   "msauth_midco_net",                    // Midcontinent Communications 
   "auth_metrocast_net",                  // MetroCast 
   "www_websso_mybrctv_com",              // Blue Ridge Communications 
   };
   ```

   Die folgende Tabelle zeigt ein Beispiel dafür, wie die geordnete Liste der primären MVPDs verwendet wird. In der ersten Spalte werden die mit dem Programmierer integrierten MVPDs aufgeführt. Die zweite Spalte ist die (gekürzte) geordnete Liste von MVPDs. Die dritte Spalte ist die Ergebnisliste, die verwendet wird, um dem Benutzer die sechs wichtigsten MVPDs anzuzeigen.

   In diesem Beispiel werden die sechs wichtigsten MVPDs anstelle der tatsächlichen neun verwendet, nur um das Beispiel einfach zu halten. Beachten Sie, dass die Ergebnisliste die Schnittmenge der ersten beiden Listen enthält und dieselbe Reihenfolge wie die zweite Liste aufweist. Beachten Sie auch, dass AT&amp;T U-verse nicht in der endgültigen Liste enthalten ist, da nur die ersten übereinstimmenden sechs MVPDs aufgenommen werden.

| Verfügbare MVPDs | Primäre MVPDs | Angezeigte 6 MVPDs |
|--- |--- |--- |
| <ol><li>Comcast XFINITY</li><li>TWW</li><li>MediaAcom</li><li>RCN</li><li>Dish</li><li>AT&amp;T U-verse</li><li>CableOne</li><li>Brighthouse</li><li>Atlantischer Breitband</li><li>WOW!</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>Cablevision Optimum</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>Dish</li><li> TWW</li><li>Cox</li><li>Charta</li><li>Verizon FiOS</li><li>Cablevision Optimum</li><li>AT&amp;T U-verse</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>Dish</li><li>TWW</li><li>Cox</li><li>Cablevision Optimum</li></ol> |
