---
title: Amazon FireOS-SDK mit dynamischer Client-Registrierung
description: Amazon FireOS-SDK mit dynamischer Client-Registrierung
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 0%

---


# Amazon FireOS-SDK mit dynamischer Client-Registrierung {#amazon-fireos-sdk-with-dynamic-client-registration}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

</br>

## <span id=""></span>Einführung {#Intro}

Das FireOS AccessEnabler SDK für FireTV wurde geändert, um die Authentifizierung zu aktivieren, ohne Sitzungs-Cookies zu verwenden. Da immer mehr Browser den Zugriff auf Cookies einschränken, war eine andere Methode erforderlich, um die Authentifizierung zu ermöglichen.

**FireOS-SDK 3.0.4** ersetzt den aktuellen App-Registrierungsmechanismus basierend auf der signierten Anfrage-ID und der Sitzungs-Cookie-Authentifizierung durch [Dynamische Kundenregistrierung](/help/authentication/dynamic-client-registration.md).
 

## API-Änderungen {#API}

### Factory.getInstance

**Beschreibung:** Instanziiert das Objekt Access Enabler . Pro Anwendungsinstanz sollte eine einzige Access Enabler -Instanz vorhanden sein.

| API-Aufruf: Konstruktor |
| --- |
| public static AccessEnabler getInstance(Context appContext, String softwareStatement, String redirectUrl)<br>        gibt AccessEnablerException aus |

**Verfügbarkeit:** v3.0+

**Parameter:**

- *appContext*: Android-Anwendungskontext
- *softwareStatement*: Wert, der vom TVE-Dashboard abgerufen wurde oder *null* wenn &quot;software\_statement&quot;in strings.xml festgelegt ist
- *redirectUrl* : für FireTV-Implementierungen sollte dieser Parameter null sein. Alle Einstellungen für dieses Attribut werden ignoriert. 

**Hinweise**

- Eine ungültige softwareStatement führt dazu, dass die Anwendung AccessEnabler nicht initialisiert oder die Anwendung für Adobe Pass-Authentifizierung und -Autorisierung registriert.
- Der Parameter redirectUrl für FireTV wird vom SDK auf adobepass://android.app as Authentifizierung festgelegt und wird von der eindeutigen AccessEnabler-Instanz verarbeitet.

### setRequestor

**Beschreibung:** Legt die Identität des Kanals fest. Jedem Kanal wird bei der Registrierung bei Adobe für das Adobe Primetime-Authentifizierungssystem eine eindeutige ID zugewiesen. Bei SSO- und Remote-Token kann sich der Authentifizierungsstatus ändern, wenn sich die Anwendung im Hintergrund befindet. setRequestor kann erneut aufgerufen werden, wenn die Anwendung in den Vordergrund gestellt wird, um mit dem Systemstatus zu synchronisieren (Abrufen eines Remote-Tokens, wenn SSO aktiviert ist, oder Löschen des lokalen Tokens, wenn in der Zwischenzeit ein Abmelden stattgefunden hat).

Die Server-Antwort enthält eine Liste von MVPDs sowie einige Konfigurationsinformationen, die an die Identität des Kanals angehängt sind. Die Server-Antwort wird intern vom Access Enabler-Code verwendet. Nur der Status des Vorgangs (d. h. SUCCESS/FAIL) wird Ihrer Anwendung über den Rückruf setRequestorComplete() angezeigt.

Wenn die Variable *urls* nicht verwendet wird, wird der resultierende Netzwerkaufruf auf die Standard-Service-Provider-URL ausgerichtet: die Adobe Release-Produktionsumgebung.

Wenn ein Wert für *urls* festgelegt ist, werden alle in der *urls* Parameter. Alle Konfigurationsanfragen werden gleichzeitig in separaten Threads ausgelöst. Der erste Antwortsender hat beim Kompilieren der Liste der MVPDs Vorrang. Für jeden MVPD in der Liste speichert der Access Enabler die URL des zugehörigen Dienstleisters. Alle nachfolgenden Berechtigungsanfragen werden an die URL weitergeleitet, die dem Dienstanbieter zugeordnet ist, der während der Konfigurationsphase mit dem Ziel-MVPD gepaart wurde.

| API-Aufruf: Anfragenkonfiguration |
| --- |
| public void setRequestor(String requestorId) |

**Verfügbarkeit:** v3.0+

| API-Aufruf: Anfragenkonfiguration |
| --- |
| ```public void setRequestor(String requestorId, ArrayList<String> urls)``` |

**Verfügbarkeit:** v3.0+

**Parameter:**

- *requestorID*: Die eindeutige ID, die dem Kanal zugeordnet ist. Übergeben Sie die eindeutige, von Adobe zugewiesene ID an Ihre Site, wenn Sie sich zum ersten Mal beim Adobe Primetime-Authentifizierungsdienst registrieren.
- *urls*: Optionaler Parameter; Standardmäßig wird der Adobe-Dienstleister verwendet (http://sp.auth.adobe.com/). Mit diesem Array können Sie Endpunkte für Authentifizierungs- und Autorisierungsdienste angeben, die von Adobe bereitgestellt werden (verschiedene Instanzen können zum Debugging verwendet werden). Sie können dies verwenden, um mehrere Adobe Primetime-Authentifizierungsdienst-Provider-Instanzen anzugeben. Dabei setzt sich die MVPD-Liste aus den Endpunkten aller Dienstleister zusammen. Jeder MVPD ist mit dem schnellsten Dienstleister verbunden. d. h. der Provider, der zuerst reagiert hat und dieser MVPD unterstützt.

Veraltet:

- *signedRequestorID*: Eine Kopie der Anforderer-ID, die digital mit Ihrem privaten Schlüssel signiert ist. <!--For more details, see [Registering Native Clients](http://tve.helpdocsonline.com/registering-native-clients)-->.

**Ausgelöste Rückrufe:** `setRequestorComplete()`

</br>

### Abmelden

**Beschreibung:** Verwenden Sie diese Methode, um den Abmeldefluss zu starten. Die Abmeldung ist das Ergebnis einer Reihe von HTTP-Weiterleitungsvorgängen, da der Benutzer sowohl von den Adobe Primetime-Authentifizierungsservern als auch von den MVPD-Servern abgemeldet werden muss. Daher öffnet dieser Fluss ein ChromeCustomTab-Fenster, um die Abmeldung auszuführen.

| API-Aufruf: Abmeldefluss starten |
| --- |
| public void logout() |

**Verfügbarkeit:** v3.0+

**Parameter:** Keines

**Ausgelöste Rückrufe:** `setAuthenticationStatus()`

## Programmierer-Implementierungsfluss {#Progr}

### **1. Registrierungsanwendung** 

1. Abrufen der Software\_statement von Adobe Pass ( TVE-Dashboard )
1. Es gibt zwei Optionen, um diese Werte an das Adobe Pass SDK zu übergeben:
   - Fügen Sie in strings.xml Folgendes hinzu: 

      ```
      <string name>"software\_statement">[softwarestatement value]</string>
      ```

   - Rufen Sie AccessEnabler.getInstance(appContext,softwareStatement, null) auf.

 

### **2. Anwendung konfigurieren**

- a.  setRequestor(requestor\_id) 

   Das SDK führt die folgenden Vorgänge aus: 

   - Registrierungsanwendung: using **software\_statement**, erhält das SDK eine **client\_id, client\_secret, client\_id\_issued\_at, redirect\_uris, grant\_types**. Diese Informationen werden im internen Speicher der Anwendung gespeichert.
   - eine **access\_token** Verwenden Sie client\_id, client\_secret und grant\_type=&quot;client\_credentials&quot;. Dieser access\_token wird für jeden Aufruf verwendet, den das SDK an Adobe Pass-Server sendet.

| Token-Fehlerantworten : |  |  |
|--- | --- | --- |
| HTTP 400 (ungültige Anforderung) | {&quot;error&quot;: &quot;invalid\_request&quot;} | Der Anfrage fehlt ein erforderlicher Parameter, enthält einen nicht unterstützten Parameterwert (außer dem Grant-Typ), wiederholt einen Parameter, enthält mehrere Anmeldeinformationen, verwendet mehr als einen Mechanismus zur Authentifizierung des Clients oder ist anderweitig fehlerhaft. |
| HTTP 400 (ungültige Anforderung) | {&quot;error&quot;: &quot;invalid\_client&quot;} | Die Client-Authentifizierung schlug fehl, da der Client unbekannt war. Das SDK *MUST* sich erneut beim Autorisierungsserver registrieren. |
| HTTP 400 (ungültige Anforderung) | {&quot;error&quot;: &quot;unauthorized\_client&quot;} | Der authentifizierte Client ist nicht berechtigt, diesen Autorisierungstyp zu verwenden. |

- Wenn ein MVPD eine passive Authentifizierung erfordert, wird eine WebView geöffnet, um passiv mit diesem MVPD auszuführen, und wird nach Abschluss geschlossen.

- b. checkAuthentication()

   - *true* : Gehen Sie zur Autorisierung
   - *false* : Wechseln Sie zu Select MVPD

- c. getAuthentication : Das SDK enthält **access_token** in Aufrufparametern 

   - mvpd gespeichert : go to setSelectedProvider(mvpd\_id)
   - mvpd nicht ausgewählt : displayProviderDialog
   - mvpd selected : go to setSelectedProvider(mvpd\_id)

- d. setSelectedProvider

   - mvpd\_id-Authentifizierungs-URL wird in ChromeCustomTabs geladen
   - Anmeldung erfolgreich : delegate.setAuthenticationStatus ( SUCCESS )
   - Anmeldung abgebrochen : Zurücksetzen der MVPD-Auswahl
   - Das URL-Schema wird als &quot;adobepass://android.app&quot;festgelegt, um zu erfassen, wenn die Authentifizierung abgeschlossen ist.

- e. get/checkAuthorization : Das SDK enthält die Kopfzeile **access\_token **als Autorisierung: Bearer **access\_token**

- Wenn die Autorisierung erfolgreich ist, wird zum Abrufen des Medien-Tokens aufgerufen.

- f. abmelden : 

   - SDK löscht gültiges Token für den aktuellen Anforderer (Authentifizierungen, die von anderen Anwendungen und nicht über SSO abgerufen wurden, bleiben gültig)
   - Das SDK öffnet benutzerdefinierte Chrome-Tabs, um den mvpd\_id-Abmelde-Endpunkt zu erreichen. Nach Abschluss werden die benutzerdefinierten Registerkarten für Chrome geschlossen
   - Das URL-Schema wird als &quot;adobepass://logout&quot;festgelegt, um den Zeitpunkt zu erfassen, zu dem die Abmeldung abgeschlossen ist.
   - logout Trigger einen sendTrackingData(new Event(EVENT\_LOGOUT,USER\_NOT\_AUTHENTICATED\_ERROR) und einen Callback : setAuthenticationStatus(0,&quot;Logout&quot;)

 

**Hinweis:** da jeder Aufruf **access_token**, werden mögliche Fehlercodes unten im SDK verarbeitet. 

| Fehlerantworten |  |  |
|--- | --- | --- |
| invalid_request | 400 | Die Anfrage ist fehlerhaft. Das SDK sollte Aufrufe an den Server nicht mehr durchführen. |
| invalid_client | 403 | Die Client-ID darf keine Anfragen mehr ausführen. Das SDK MUSS die Kundenregistrierung erneut durchführen. |
| access_denied | 401 | Das access_token ist ungültig. Das SDK MUSS ein neues access_token anfordern. |

