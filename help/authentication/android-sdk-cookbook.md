---
title: Android SDK Cookbook
description: Android SDK Cookbook
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 0%

---

# Android SDK Cookbook {#android-sdk-cookbook}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

</br>

## Einführung {#intro}

In diesem Dokument werden die Berechtigungs-Workflows beschrieben, die die Anwendung eines Programmierers auf oberster Ebene über die APIs implementieren kann, die von der Android AccessEnabler-Bibliothek bereitgestellt werden.


Die Adobe Primetime-Authentifizierungsberechtigungslösung für Android ist letztendlich in zwei Domänen unterteilt:

- Die UI-Domäne - dies ist die Anwendungsebene der obersten Ebene, die die Benutzeroberfläche implementiert und die von der AccessEnabler-Bibliothek bereitgestellten Dienste verwendet, um Zugriff auf eingeschränkte Inhalte zu ermöglichen.
- In der AccessEnabler-Domäne werden die Berechtigungs-Workflows in folgender Form implementiert:
   - Netzwerkaufrufe an Adobe-Backend-Server
   - Geschäftslogikregeln für die Authentifizierungs- und Autorisierungs-Workflows
   - Verwaltung verschiedener Ressourcen und Verarbeitung des Workflow-Status (z. B. Token-Cache)

Ziel der AccessEnabler-Domäne ist es, alle Komplexität der Berechtigungs-Workflows auszublenden und der oberen Ebene (über die AccessEnabler-Bibliothek) eine Reihe einfacher Berechtigungs-Primitive bereitzustellen, mit denen Sie die Berechtigungs-Workflows implementieren:

1. Anfragenidentität festlegen
1. Überprüfen und Abrufen der Authentifizierung für einen bestimmten Identitäts-Provider
1. Prüfen und Autorisieren einer bestimmten Ressource
1. Abmelden

Die Netzwerkaktivität von AccessEnabler erfolgt in einem anderen Thread, sodass der UI-Thread nie blockiert wird. Daher muss der bidirektionale Kommunikationskanal zwischen den beiden Anwendungsdomänen einem vollständig asynchronen Muster folgen:

- Die Anwendungsebene der Benutzeroberfläche sendet Nachrichten über die API-Aufrufe, die von der AccessEnabler-Bibliothek verfügbar gemacht werden, an die AccessEnabler-Domäne.
- Der AccessEnabler antwortet auf die UI-Ebene über die Callback-Methoden, die im AccessEnabler -Protokoll enthalten sind und die die UI-Ebene mit der AccessEnabler -Bibliothek registriert.

## Berechtigungsflüsse {#entitlement}

1. [Voraussetzungen](#prereqs)
1. [Startup-Fluss](#startup_flow)
1. [Authentifizierungsfluss](#authn_flow)
1. [Autorisierungsfluss](#authz_flow)
1. [Medienfluss anzeigen](#media_flow)
1. [Abmeldefluss](#logout_flow)



### A. Voraussetzungen {#prereqs}

1. Erstellen Sie Ihre Callback-Funktionen:
   - [`setRequestorComplete()`](#$setRequestorComplete)

     Ausgelöst von `setRequestor()`, gibt Erfolg oder Fehler zurück.\
     &quot;Erfolg&quot;bedeutet, dass Sie mit Berechtigungsaufrufen fortfahren können.

   - [displayProviderDialog(mvpds)](#$displayProviderDialog)

     Ausgelöst von `getAuthentication()` nur dann, wenn der Benutzer keinen Anbieter (MVPD) ausgewählt hat und noch nicht authentifiziert ist.\
     Die `mvpds` -Parameter ist ein Array von Anbietern, die dem Benutzer zur Verfügung stehen.

   - [`setAuthenticationStatus(status, errorcode)`](#$setAuthNStatus)

     Ausgelöst von `checkAuthentication()` jedes Mal.\
     Ausgelöst von `getAuthentication()` nur dann, wenn der Benutzer bereits authentifiziert ist und einen Provider ausgewählt hat.

     Status zurückgegeben ist erfolgreich oder fehlgeschlagen, der Fehlertyp wird im Fehlercode beschrieben.

   - [navigateToUrl(url)](#$navigateToUrl)

     Ausgelöst von `getAuthentication()` nachdem der Benutzer einen MVPD ausgewählt hat. Die `url` liefert den Speicherort der Anmeldeseite des MVPD.

   - [`sendTrackingData(event, data)`](#$sendTrackingData)

     Ausgelöst von `checkAuthentication(), getAuthentication(), checkAuthorization(), getAuthorization(), setSelectedProvider()`.\
     Die `event` -Parameter gibt an, welches Berechtigungsereignis aufgetreten ist; der `data` -Parameter ist eine Liste von Werten, die sich auf das Ereignis beziehen.

   - [`setToken(token, resource)`](#$setToken)

     Ausgelöst von `checkAuthorization()` und `getAuthorization()` nach erfolgreicher Autorisierung zum Anzeigen einer Ressource.\
     Die `token` -Parameter ist das kurzlebige Medien-Token; die `resource` -Parameter ist der Inhalt, den der Benutzer anzeigen darf.

   - [`tokenRequestFailed(resource, code, description)`](#$tokenRequestFailed)

     Ausgelöst von `checkAuthorization()` und `getAuthorization()` nach einer nicht erfolgreichen Autorisierung.\
     Die `resource` -Parameter ist der Inhalt, den der Benutzer anzuzeigen versucht hat; die `code` -Parameter ist der Fehlercode, der angibt, welcher Fehlertyp aufgetreten ist; der `description` -Parameter beschreibt den Fehler, der dem Fehlercode zugeordnet ist.

   - [`selectedProvider(mvpd)`](#$selectedProvider)

     Ausgelöst von `getSelectedProvider()`.\
     Die `mvpd` liefert Informationen zum vom Benutzer ausgewählten Provider.

   - [`setMetadataStatus(metadata, key, arguments)`](#$setMetadataStatus)

     Ausgelöst von `getMetadata().`\
     Die `metadata` liefert die spezifischen Daten, die Sie angefordert haben; die `key` -Parameter ist der Schlüssel, der in der Variablen `getMetadata()` und die `arguments` ist dasselbe Wörterbuch, das an `getMetadata()`.

   - [`preauthorizedResources(resources)`](#$preauthResources)

     Ausgelöst von `checkPreauthorizedResources()`.\
     Die `authorizedResources` -Parameter zeigt die Ressourcen an, die der Benutzer anzeigen darf.


![](assets/android-entitlement-flows.png)


### B. Startup Flow {#startup_flow}

1. Starten Sie die Anwendung der obersten Ebene.
1. Adobe Primetime-Authentifizierung initiieren

   a. Aufruf [`getInstance`](#$getInstance) , um eine Instanz der Adobe Primetime-Authentifizierung AccessEnabler zu erstellen.

   - **Abhängigkeit:** Adobe Primetime-Authentifizierung Native Android-Bibliothek (AccessEnabler)

   b. Aufruf` setRequestor()` Festlegung der Identität des Programmierers; Weiterleitung der Programmierung `requestorID` und (optional) ein Array von Adobe Primetime-Authentifizierungsendpunkten.

   - **Abhängigkeit:** Gültige Adobe Primetime-Authentifizierungsanfrage-ID\
     (Wenden Sie sich an Ihren Kundenbetreuer für die Adobe Primetime-Authentifizierung, um dies zu arrangieren.)

   - **Trigger:** setRequestorComplete()-Rückruf

   | NOTE |     |
   | --- | --- |  
   | ![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/icons/1313859077_lightbulb.png) | Berechtigungsanfragen können erst abgeschlossen werden, wenn die Identität des Anfragenden vollständig ermittelt wurde. Dies bedeutet effektiv, dass setRequestor() zwar noch ausgeführt wird, jedoch alle nachfolgenden Berechtigungsanfragen (z. B. `checkAuthentication()`) blockiert werden.<br><br>Sie haben zwei Implementierungsoptionen: Sobald die Identifizierungsinformationen des Anfragenden an den Backend-Server gesendet wurden, kann die UI-Anwendungsschicht einen der beiden folgenden Ansätze wählen:<br><br>1.  Warten Sie auf die Auslösung der `setRequestorComplete()` callback (Teil des AccessEnabler -Delegates).  Diese Option bietet die größte Sicherheit, dass `setRequestor()` abgeschlossen ist, daher wird dies für die meisten Implementierungen empfohlen.<br>2.  Fahren Sie fort, ohne auf die Aktivierung der `setRequestorComplete()` zurücksetzen und mit der Ausgabe von Berechtigungsanfragen beginnen. Diese Aufrufe (checkAuthentication, checkAuthorization, getAuthentication, getAuthorization, checkPreauthorizedResource, getMetadata, logout) werden von der AccessEnabler-Bibliothek in die Warteschlange gestellt, die die tatsächlichen Netzwerkaufrufe nach der `setRequestor(). `Diese Option kann gelegentlich unterbrochen werden, wenn beispielsweise die Netzwerkverbindung instabil ist. |

1. Aufruf [checkAuthentication()](#$checkAuthN) um nach einer vorhandenen Authentifizierung zu suchen, ohne den vollständigen Authentifizierungsfluss zu starten.   Wenn dieser Aufruf erfolgreich ist, können Sie direkt zum Autorisierungsfluss übergehen.  Ist dies nicht der Fall, fahren Sie mit dem Authentifizierungsfluss fort.

   - **Abhängigkeit:** Ein erfolgreicher Aufruf an `setRequestor()` (Diese Abhängigkeit gilt auch für alle nachfolgenden Aufrufe).

   - **Trigger:** setAuthenticationStatus()-Rückruf



### C. Authentifizierungsfluss {#authn_flow}

1. Aufruf [`getAuthentication()`](#$getAuthN) , um den Authentifizierungsfluss zu initiieren oder um zu bestätigen, dass der Benutzer bereits authentifiziert ist.\
   **Trigger:**
   - Der Rückruf setAuthenticationStatus() , wenn der Benutzer bereits authentifiziert ist.  Gehen Sie in diesem Fall direkt zum [Autorisierungsfluss](#authz_flow).
   - Der Rückruf displayProviderDialog() , wenn der Benutzer noch nicht authentifiziert ist.

1. Präsentieren Sie den Benutzer mit der Liste der Anbieter, die an gesendet werden `displayProviderDialog()`.

1. Nachdem der Benutzer einen Anbieter ausgewählt hat, rufen Sie die URL des MVPD des Benutzers aus der `navigateToUrl()` Callback.  Öffnen Sie eine WebView und leiten Sie dieses WebView-Steuerelement an die URL weiter.

1. Über die im vorherigen Schritt instanziierte WebView gelangt der Benutzer auf die Anmeldeseite des MVPD und gibt Anmeldedaten ein. In WebView finden verschiedene Umleitungsvorgänge statt.


   **Hinweis:** An dieser Stelle hat der Benutzer die Möglichkeit, den Authentifizierungsfluss abzubrechen. In diesem Fall ist Ihre UI-Schicht dafür verantwortlich, den AccessEnabler über dieses Ereignis zu informieren, indem sie `setSelectedProvider()` mit `null` als Parameter. Dadurch kann AccessEnabler den internen Status bereinigen und den Authentifizierungsfluss zurücksetzen.

1. Nach erfolgreicher Anmeldung durch den Benutzer erkennt Ihre Anwendungsebene das Laden einer &quot;benutzerdefinierten Umleitungs-URL&quot;(d. h.: `http://adobepass.android.app`). Diese benutzerdefinierte URL ist tatsächlich eine ungültige URL, die nicht von WebView geladen werden soll. Es ist ein Signal, dass der Authentifizierungsfluss abgeschlossen ist und die WebView geschlossen werden muss.

1. WebView-Steuerelement schließen und aufrufen `getAuthenticationToken()`, der AccessEnabler anweist, das Authentifizierungstoken vom Backend-Server abzurufen.

1. [Optional] Aufruf [`checkPreauthorizedResources(resources)`](#$checkPreauth) , um zu überprüfen, welche Ressourcen der Benutzer anzeigen darf. Die `resources` parameter ist ein Array geschützter Ressourcen, die mit dem Authentifizierungstoken des Benutzers verknüpft sind.\
   **Trigger:** `preAuthorizedResources()` callback\
   **Ausführungspunkt:** Nach Abschluss des Authentifizierungsablaufs

1. Wenn die Authentifizierung erfolgreich war, fahren Sie mit dem Autorisierungsfluss fort.



### D. Genehmigungsprozess {#authz_flow}

1. Aufruf [getAuthorization()](#$getAuthZ) , um den Genehmigungsprozess einzuleiten.

   Abhängigkeit: Gültige ResourceID(s), die mit den MVPD(s) vereinbart wurde.

   **Hinweis:** ResourceIDs sollten mit denen auf anderen Geräten oder Plattformen übereinstimmen und sind über MVPDs hinweg identisch.

1. Validieren Sie Authentifizierung und Autorisierung.

   - Wenn die Variable `getAuthorization()` Aufruf erfolgreich: Der Benutzer verfügt über gültige AuthN- und AuthZ-Token (der Benutzer ist authentifiziert und berechtigt, die angeforderten Medien zu sehen).
   - Wenn `getAuthorization()` schlägt fehl: Untersuchen Sie die ausgelöste Ausnahme, um ihren Typ zu bestimmen (AuthN, AuthZ oder etwas Anderes):
      - Wenn es sich um einen Authentifizierungsfehler (AuthN) handelte, starten Sie den Authentifizierungsfluss neu.
      - Wenn es sich um einen Autorisierungsfehler (AuthZ) handelt, ist der Benutzer nicht berechtigt, das angeforderte Medium zu sehen und dem Benutzer sollte eine Fehlermeldung angezeigt werden.
      - Wenn ein anderer Fehlertyp aufgetreten ist (Verbindungsfehler, Netzwerkfehler usw.) zeigen Sie dem Benutzer eine entsprechende Fehlermeldung an.

1. Validieren Sie das Token für kurze Medien.\
   Verwenden Sie die Adobe Primetime Authentication Media Token Verifier-Bibliothek, um das von der `getAuthorization()` Aufruf oben:

   - Wenn die Validierung erfolgreich ist: Wiedergabe des angeforderten Mediums für den Benutzer.
   - Wenn die Validierung fehlschlägt: Das AuthZ-Token war ungültig, die Medienanforderung sollte abgelehnt werden und dem Benutzer sollte eine Fehlermeldung angezeigt werden.

1. Kehren Sie zu Ihrem normalen Anwendungsfluss zurück.

### E. Medienfluss anzeigen {#media_flow}

1. Der Benutzer wählt das Medium aus, das angezeigt werden soll.
2. Sind die Medien geschützt?  Ihre Anwendung prüft, ob die ausgewählten Medien geschützt sind:
- Wenn das ausgewählte Medium geschützt ist, startet Ihre Anwendung die [Autorisierungsfluss](#authz_flow) höher.
- Wenn das ausgewählte Medium nicht geschützt ist, geben Sie das Medium für den Benutzer wieder.



### F. Abmeldefluss {#logout_flow}

1. Aufruf [`logout()`](#$logout) , um den Benutzer abzumelden.\
   AccessEnabler löscht alle zwischengespeicherten Werte und Token für das aktuelle MVPD für den aktuellen Anfragenden und auch für Anfragende mit Single Sign On. Nachdem der Cache gelöscht wurde, führt der AccessEnabler einen Server-Aufruf durch, um die Server-seitigen Sitzungen zu bereinigen.  Da der Server-Aufruf zu einer SAML-Umleitung zum IdP führen kann (dies ermöglicht die Sitzungsbereinigung auf der IdP-Seite), muss dieser Aufruf allen Umleitungen folgen. Aus diesem Grund muss dieser Aufruf innerhalb eines WebView-Steuerelements verarbeitet werden.

   a. Entsprechend dem gleichen Muster wie der Authentifizierungs-Workflow sendet die AccessEnabler-Domäne eine Anfrage an die UI-Anwendungsebene (über die`navigateToUrl()` callback) , um ein WebView-Steuerelement zu erstellen und dieses Steuerelement anzuweisen, die URL des Abmelde-Endpunkts auf den Backend-Server zu laden.

   b. Auch hier muss die Benutzeroberfläche die Aktivität des WebView-Steuerelements überwachen und den Zeitpunkt erkennen, zu dem das Steuerelement während mehrerer Umleitungen die benutzerdefinierte URL der Anwendung lädt (d. h.: `http://adobepass.android.app/`). Sobald dieses Ereignis stattfindet, schließt die UI-Anwendungsebene die WebView und der Abmeldevorgang ist abgeschlossen.

   **Hinweis:** Der Abmeldefluss unterscheidet sich vom Authentifizierungsfluss insofern, als der Benutzer in keiner Weise mit der WebView interagieren muss. Die UI-Anwendungsebene verwendet eine WebView, um sicherzustellen, dass alle Umleitungen befolgt werden. Daher ist es möglich (und empfohlen), das WebView-Steuerelement während des Abmeldevorgangs unsichtbar (d. h. ausgeblendet) zu machen.



### Benutzerfluss für die Anmeldung mit mehreren MVPDs und Abmeldung {#user_flows}

[Hier](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/files/AndroidSSOUserFlows.pdf) Sie haben ein Dokument, das das Verhalten bei der Verwendung mehrerer MVPDs beschreibt und was passiert, wenn sich der Benutzer von einer Anwendung abmeldet.

Das beschriebene Verhalten ist bei Verwendung von Android SDK-Version >= 2.0.0 verfügbar.
