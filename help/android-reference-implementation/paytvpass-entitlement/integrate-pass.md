---
description: Passen Sie Ihre Referenzimplementierung an, um die Adobe Primetime-Authentifizierung für Ihre Produktionsversion zu integrieren.
title: Primetime-Authentifizierung integrieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---


# Primetime-Authentifizierung integrieren {#integrate-primetime-authentication}

Passen Sie Ihre Referenzimplementierung an, um die Adobe Primetime-Authentifizierung für Ihre Produktionsversion zu integrieren.

Die Integration der Referenzimplementierung des Primetime-Authentifizierungsdienstes funktioniert standardmäßig als Demonstration. Um die Integration jedoch in einem produktionsfertigen Player zu verwenden, müssen Sie die folgenden Anpassungen implementieren:

1. Aktivieren oder deaktivieren Sie Berechtigungsabläufe.

   Das `EntitlementManager` muss zunächst initialisieren und eine Instanz des Primetime-Authentifizierungs-SDK abrufen, damit diese aktiviert werden kann. Wenn `EntitlementManager` diese Bibliothek nicht initialisiert, wird der Manager deaktiviert.
1. Aktivieren Sie `EntitlementManger` aus Ihrer Hauptanwendungsklasse:

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. Verwenden Sie die `ManagerFactory`-Klasse, um eine Instanz von `EntitlementManager` abzurufen.

   Sie müssen immer `ManagerFactory` verwenden, um eine Instanz von `EntitlementManager` abzurufen, da `ManagerFactory` eine Instanz von EntitlementManager für Ihre Anwendung unterhält. Instanziieren Sie niemals die Klassen `EntitlementManager` oder `EntitlementManagerOn`, indem Sie ihre Konstruktoren verwenden.

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   `ManagerFactory` gibt eine Instanz von `EntitlementManagerOn` zurück, bei der die Berechtigungsabläufe aktiviert sind, wenn Sie zuvor `EntitlementManager.initializeAccessEnabler` genannt haben. Wenn Sie `EntitlementManager.initializeAccessEnabler` nicht zum ersten Mal aufrufen, gibt `ManagerFactory` eine Instanz von `EntitlementManager` zurück, wobei die Berechtigungsabläufe deaktiviert sind. 1. Konfigurieren Sie die Anforderungs-ID.

   Die Referenz-Implementierung ist vorkonfiguriert und die Test-Anforderer-ID ist auf Folgendes eingestellt: &quot;REF&quot;. Mit dieser Anforderungs-ID können Sie Ihre Anwendung testen. Wenn Sie bereit sind, die Anforderungs-ID zu verwenden, die Ihnen Ihr Primetime-Authentifizierungsbeauftragter genannt hat, aktualisieren Sie die [!DNL res/values/strings.xml]-Datei der Anwendung mit Ihrer Anforderer-ID.

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

   Darüber hinaus müssen Sie möglicherweise die URLs ändern, die Ihre Anwendung zum Herstellen einer Verbindung mit den Primetime-Authentifizierungsdiensten verwendet. Dazu gehören die Primetime-Authentifizierungs-Staging- und Produktions-Server-URLs sowie eine URL zu einem Token-Verifizierungsdienst. Weitere Informationen erhalten Sie von Ihrem Adobe Primetime-Kundenbetreuer. 1. Unterschreiben Sie die Anforderungs-ID.

   Um die Identität des Programmierers im Primetime-Authentifizierungssystem festzustellen, wird die Anforderungs-ID des Programmierers an das Primetime-Authentifizierungssystem gesendet. Als zusätzliche Sicherheitsebene muss die Anforderungs-ID vom Programmierer signiert werden, bevor sie an die Adobe gesendet wird. Adobe empfiehlt, dass der Programmierer einen Dienst zum Signieren der Anforderungs-ID in einem vertrauenswürdigen Netzwerk eingerichtet hat.

   Die Primetime-Referenzimplementierung zeigt, wie die Anforderungs-ID signiert wird, jedoch nur zu Demonstrationszwecken. Adobe empfiehlt dringend, dass das Unterschriftszertifikat und der Unterschriftsgenerator-Code unter `com.adobe.primetime.reference.crypto` nicht in eine Produktionsanwendung aufgenommen werden sollten. Stattdessen sollten Sie ihn in einen vertrauenswürdigen vernetzten Dienst verschieben.

1. Konfigurieren Sie die Server-Umgebung.

   Der Primetime-Authentifizierungsdienst kann in zwei verschiedenen Umgebung ausgeführt werden:

   * Staging - Die Staging-Umgebung wird zum Testen der Anwendung verwendet.
   * Produktion - Die Produktions-Umgebung wird für Live-Implementierungen Ihrer Applikation verwendet.

   Sie legen die URIs sowohl für die Staging- als auch für die Produktions-Umgebung mithilfe der Anwendung fest. Sie müssen jedoch festlegen, welche dieser URIs von der Anwendung im Code verwendet werden. Stellen Sie in der `com.adobe.primetime.reference.manager.EntitlementManger`-Klasse die Variable `environmentUri` auf `STAGING_URI` oder `PRODUCTION_URI` ein, je nachdem, welche Primetime-Authentifizierungsdienst-Umgebung Sie verwenden.

   >[!NOTE]
   >
   >Die angegebene Anforderungs-ID (&quot;REF&quot;) sollte nur mit der Staging-Umgebung verwendet werden.

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

1. Passen Sie das MVPD-Auswahlraster an.

   Auf der Seite zur Auswahl des Content Providers wird eine Tabelle der neun wichtigsten MVPDs angezeigt, aus denen der Benutzer auswählen kann. Die Anwendung ruft die neun wichtigsten MVPDs aus einer bestellten Liste innerhalb der Anwendung ab, die mit den verfügbaren MVPDs übereinstimmt, die mit dem Programmierer im Primetime-Authentifizierungssystem integriert sind. Die bestellte Liste der primären MVPDs wird auf der MVPD-ID innerhalb des Primetime-Authentifizierungs-Systems und nicht auf dem MVPD-Anzeigenamen gezählt. Es ist wichtig zu überprüfen, ob die MVPD-IDs in der primären MVPD-Liste mit den MVPD-IDs übereinstimmen, die mit dem Programmiererkonto integriert sind, da die IDs in einigen Fällen von Integrationen verschieden sein können. Nachstehend finden Sie die geordnete Liste der primären MVPDs, die in der Klasse `com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment` enthalten ist.

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

   Die folgende Tabelle zeigt ein Beispiel dafür, wie die geordnete Liste der primären MVPDs verwendet wird. Die erste Spalte Liste die in den Programmierer integrierten MVPDs. Die zweite Spalte ist die (gekürzte) geordnete Liste von MVPDs. Die dritte Spalte ist die Ergebnisspalte, die verwendet wird, um dem Benutzer die sechs wichtigsten MVPDs anzuzeigen.

   Dieses Beispiel verwendet die sechs besten MVPDs anstelle der eigentlichen neun, nur um das Beispiel einfach zu halten. Beachten Sie, dass die Liste result den Schnittpunkt der ersten beiden Listen enthält und dieselbe Reihenfolge wie die zweite Liste hat. Beachten Sie auch, dass AT&amp;T U-verse nicht in der endgültigen Liste ist, da nur die ersten übereinstimmenden sechs MVPDs genommen werden.

| Verfügbare MVPDs | Primär-MVPDs | Angezeigte 6 MVPDs |
|--- |--- |--- |
| <ol><li>Comcast XFINITY</li><li>TWC</li><li>Mediacom</li><li>RCN</li><li>Dish</li><li>AT&amp;T U-verse</li><li>CableOne</li><li>Brighthouse</li><li>Atlantischer Breitband</li><li>WOW!</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>Cablevision Optimum</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>Dish</li><li> TWC</li><li>Cox</li><li>Charta</li><li>Verizon FiOS</li><li>Cablevision Optimum</li><li>AT&amp;T U-verse</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>Dish</li><li>TWC</li><li>Cox</li><li>Cablevision Optimum</li></ol> |
