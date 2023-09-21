---
description: Sie können beliebige Streams aus einer TVSDK-basierten Absender-App senden und den Stream mit Browser TVSDK auf Chromecast wiedergeben lassen.
title: Google Cast App für Browser TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Google Cast App für Browser TVSDK{#google-cast-app-for-browser-tvsdk}

Sie können beliebige Streams aus einer TVSDK-basierten Absender-App senden und den Stream mit Browser TVSDK auf Chromecast wiedergeben lassen.

<!--<a id="section_87CE5D6D46F0439EB6E63A742D6DD9C8"></a>-->

Es gibt zwei Komponenten einer Cast-fähigen App:

* Die Absender-App, die als Remote-Steuerung fungiert.

  Absender-Apps umfassen Smartphones, PCs usw. Die App kann mit nativen SDKs für iOS, Android und Chrome entwickelt werden.
* Die Receiver-App, die auf Chromecast ausgeführt wird und den Inhalt wiedergibt.

  >[!IMPORTANT]
  >
  >Diese App kann nur eine HTML5-App sein.

Absender und Empfänger kommunizieren mit den Cast SDKs, um Nachrichten zu übermitteln.

## Grundlegender Workflow {#section_FAF680FF29DA4D24A50AC0A2B6402B58}

Im Folgenden finden Sie eine Übersicht über den Prozess:

1. Die Absender-App stellt eine Verbindung mit der Empfänger-App her.
1. Die Absender-App sendet eine Nachricht, um die Medien in die Empfänger-App zu laden.
1. Die Receiver-App beginnt mit der Wiedergabe.
1. Die Absender-App sendet Kontrollnachrichten für die Wiedergabe, wie z. B. Wiedergabe, Pause, Suchen, Vorwärts, schnelle Zurückspulen, Zurückspulen, Volumenänderung usw. an die Empfänger-App.
1. Die Empfänger-App reagiert auf diese Nachrichten.

## Nachrichtenformat {#section_1624159DD51D4C87B3E5803DEEBCB6B7}

Sie müssen die Nachrichten definieren, damit der Absender und der Empfänger sie verstehen können. Im Folgenden finden Sie ein Beispiel für eine Suchmeldung:

```js
{ 
"type": "seek", 
"seekTo": 10000 
} 
```

Beim Senden benutzerdefinierter Nachrichten wie der Suchnachricht über die Cast-SDKs ist ein benutzerdefinierter Namespace für Nachrichten erforderlich. Hier ist ein Beispiel in JavaScript:

```js
Custom Message Namespace 
var MSG_NAMESPACE = "urn:x-cast:com.adobe.primetime"; 
```

## Herstellen einer Verbindung {#section_B4D40CABDD3E46FDBE7B5651DFF91653}

>[!IMPORTANT]
>
>Browser TVSDK-APIs sind bei der Herstellung der Verbindung nicht beteiligt.

Um eine Verbindung herzustellen, müssen Absender und Empfänger die folgenden Aufgaben ausführen:

* Der Absender muss die Plattformdokumentation unter [Entwicklung der Sender App](https://developers.google.com/cast/docs/sender_apps).
* Der Empfänger verwendet die Cast-Empfänger-APIs, um eine Verbindung mit der Absender-App herzustellen. Beispiel:

  ```js
  window.castReceiverManager = cast.receiver.CastReceiverManager.getInstance(); 
  
  window.castReceiverManager.onReady = function (event) { /*handle event*/ }; 
  window.castReceiverManager.onSenderConnected = function (event) { /*handle event*/ }; 
  window.castReceiverManager.onSenderDisconnected = function (event) { /*handle event*/ }; 
  
  var customMessageBus = window.castReceiverManager.getCastMessageBus(MSG_NAMESPACE); 
  customMessageBus.onMessage = function (event) { /*handle messages*/ }; 
  
  window.castReceiverManager.start(); 
  ```

## Nachrichtenverarbeitung {#section_3E4814546F5946C9B3E7A1AE384B4FF8}

Informationen zum Senden von Nachrichten an den Empfänger finden Sie in der Dokumentation zur Plattform Ihres Absenders.

>[!IMPORTANT]
>
>Sie müssen den benutzerdefinierten Nachrichten-Namespace einschließen, `MSG_NAMESPACE` in allen Nachrichten.

Befolgen Sie für die Receiver-App die Dokumentation für die APIs für den gecast-Empfänger.

**Beispiel einer Chrome-basierten Absendernachricht**

```js
window.session.sendMessage(MSG_NAMESPACE, message, successCallback, errorCallback); //https://developers.google.com/cast/docs/reference/chrome/chrome.cast.Session#sendMessage
```

**Ereignisbehandlung für Chrome-basierten Absender**

Binden Sie Ereignis-Handler an Ihre UI-Elemente, die Nachrichten senden, wenn die entsprechenden Ereignisse ausgelöst werden. Bei einer Chrome-basierten Absender-App kann das Suchereignis beispielsweise wie folgt gesendet werden:

```js
document.getElementById("#seekBar").addEventListener("click", seekEventHandler); 
   
function seekEventHandler(event) { 
    seekMessage = { type: "seek", seekTo: player.currentTime }; //player is an instance of AdobePSDK.MediaPlayer 
    window.session.sendMessage(MSG_NAMESPACE, seekMessage, successCallback, errorCallback); 
} 
```

**Umgang mit Empfängernachrichten**

Hier ist ein Beispiel für die Verarbeitung der Suchmeldung in der Empfänger-App:

```js
customMessageBus.onMessage = function (event) { 
    var message = JSON.parse(event.data); 
    switch (message.type) { 
        case "seek":  
            player.seek(parseInt(message.seekTo)); 
            break; 
        //code for handling other events 
        default:  
            break; 
    } 
}; 
```
