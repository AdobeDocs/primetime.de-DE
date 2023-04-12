---
title: Grundlegendes zu Benutzer-IDs
description: Grundlegendes zu Benutzer-IDs
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# Grundlegendes zu Benutzer-IDs {#understanding-user-ids}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

Grundsätzlich ist jeder Benutzer, der einen Berechtigungsfluss initiiert, einer einzelnen eindeutigen Benutzer-ID zugeordnet. Im Zuge eines Berechtigungsablaufs kann jedoch eine Benutzer-ID auf unterschiedliche Weise angezeigt werden, je nachdem, von welcher API Sie die ID erhalten.

Die `sessionGUID` im Token für kurze Medien ist die sichere Form der Benutzer-ID, die über die `sendTrackingData()` aufrufen. In allen aktuellen Integrationen ist dies eine beständige GUID für den Benutzer über Zeit und Geräte hinweg. Die Quelle der GUID beginnt mit der Benutzer-ID aus der Authentifizierungsantwort, die vom MVPD stammt. Einige MVPDs könnten sich jedoch in Zukunft anders entscheiden und eine vorübergehende GUID senden. Wenn ein Programmierer sicherstellen möchte, dass die MVPD-Quell-Benutzer-ID in der AuthN-Antwort persistent ist, sollte er dies in seinen Vereinbarungen mit MVPDs anordnen.

Im Folgenden finden Sie die verschiedenen Möglichkeiten, wie die Benutzer-ID in den Adobe Primetime-Authentifizierungs-APIs dargestellt wird:

| Eigenschaft | Zweck | Hash | Digital signiert | Beschreibung |
| --- | --- | --- | --- | --- |
| sendTrackingData() GUID-Eigenschaft | Tracking/Analytics | Ja | Nein | - Die MVPD-Benutzer-ID, gehasht nach Adobe. Die Benutzer-ID kann nicht zur Quelle zum MVPD zurückverfolgt werden. </br> </br> - Diese Form der Kennung ist nicht digital signiert, daher ist sie für die Betrugsbekämpfung nicht sicher. Es ist jedoch ausreichend für Analysen.  </br> </br> - Dieses Formular der Benutzer-ID wird clientseitig für alle Ereignisse bereitgestellt, die die Adobe Primetime-Authentifizierung im AuthN/AuthZ-Fluss generiert. |
| sessionGUID-Eigenschaft des Short Media Token | Betrugsverfolgung der gleichzeitigen Nutzung | Ja | Ja | - Dies entspricht der Benutzer-ID über sendTrackingData(). Diese ist jedoch digital signiert, um ihre Integrität zu schützen, und eignet sich gut genug für die Verfolgung von Betrug. </br> </br> - Sie soll nach Verwendung unserer Validator-Bibliothek serverseitig verarbeitet und auf Betrugsmuster analysiert werden, bevor der Video-Stream an den Client freigegeben wird.  Die Durchführung dieser Aufgaben obliegt dem Programmierer. |
| getMetadata() userID-Eigenschaft | Kontoverknüpfung, Betrugsuntersuchung mit MVPD | Nein | Nein | - Diese Eigenschaft ermöglicht es Adobe, die eigentliche MVPD-Benutzer-ID für den Programmierer verfügbar zu machen. </br> </br> - In der Konfiguration der Adobe kann sie als verschlüsselt oder nicht festgelegt werden (je nach MVPD-Voreinstellung). Wenn sie verschlüsselt ist, wird sie mit dem öffentlichen Schlüssel aus dem der Adobe bereitgestellten Programmerzertifikat verschlüsselt, sodass sie dem Client nicht eindeutig angezeigt wird. </br> </br> - Dadurch erhält der Programmierer die tatsächliche Benutzer-ID aus dem MVPD, also kann sie direkt mit dem MVPD für die Kontoverknüpfung oder Betrugsuntersuchung verwendet werden. |


**In der Schlussfolgerung**

* Im Allgemeinen stellt der MVPD eine beständige eindeutige ID bereit <u>und übergibt sie an Adobe bei erfolgreicher Authentifizierung</u>. Sie ist im Allgemeinen in allen Netzwerken konsistent. Die Ausnahme ist Comcast MVPD, das für jeden Kanal eine andere Benutzer-ID bereitstellt.

* Die MVPD-Benutzer-ID enthält keine personenbezogenen Daten und ist KEINE Kontonummer. Es muss nicht in verschlüsselter Form offen gelegt werden, da wir mit allen MVPDs überprüft haben, dass keine PII gesendet werden.

Wie Sie die Benutzer-ID verwenden, hängt vom Anwendungsfall ab:

* Wenn Sie es für Tracking/Analysen benötigen, ist es am praktischsten, es von `sendTrackingData()`.
* Wenn Sie es Server-seitig für Stream-Veröffentlichung, Betrug oder operative Daten benötigen, können Sie es vom Media Token-Validator abrufen.
* Wenn Sie es für Kontoverknüpfung und tieferen Betrug benötigen, wenden Sie sich an Ihren Ansprechpartner bei der Adobe.

