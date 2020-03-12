---
description: Sie können beliebige Streams aus einer TVSDK-basierten Sender-App abspielen lassen und den Stream mit Browser TVSDK auf Chromecast wiedergeben.
seo-description: Sie können beliebige Streams aus einer TVSDK-basierten Sender-App abspielen lassen und den Stream mit Browser TVSDK auf Chromecast wiedergeben.
seo-title: Google Cast app for Browser TVSDK
title: Google Cast app for Browser TVSDK
uuid: 018143e2-143a-4f88-97c6-4b10a2083f9e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Google Cast app for Browser TVSDK{#google-cast-app-for-browser-tvsdk}

Sie können beliebige Streams aus einer TVSDK-basierten Sender-App abspielen lassen und den Stream mit Browser TVSDK auf Chromecast wiedergeben.

<!--<a id="section_87CE5D6D46F0439EB6E63A742D6DD9C8"></a>-->

Es gibt zwei Komponenten einer App, die Cast-fähig ist:

* Die Sender-App, die als Remote-Steuerung fungiert.

   Absender-Apps umfassen Smartphones, PCs usw. Die App kann mit nativen SDKs für iOS, Android und Chrome entwickelt werden.
* Die Receiver-App, die auf Chromecast ausgeführt wird und den Inhalt abspielt.

   >[!IMPORTANT]
   >
   >Diese App kann nur eine HTML5-App sein.

Absender und Empfänger kommunizieren mit den Cast SDKs, um Nachrichten zu übermitteln.

## Grundlegender Workflow {#section_FAF680FF29DA4D24A50AC0A2B6402B58}

Im Folgenden finden Sie eine Übersicht zum Prozess:

1. Die Sender-App stellt eine Verbindung mit der Empfänger-App her.
1. Die Sender-App sendet eine Nachricht, um das Medium in die Empfänger-App zu laden.
1. Die Receiver-App beginnt mit der Wiedergabe.
1. Die Sender-App sendet Steuerungsmeldungen zur Wiedergabe, z. B. &quot;Abspielen&quot;, &quot;Anhalten&quot;, &quot;Suchen&quot;, &quot;Schnelles Vorspulen&quot;, &quot;Schnelles Zurückspulen&quot;, &quot;Zurückspulen&quot;, &quot;Lautstärkeänderung&quot;usw. an die Empfänger-App.
1. Die Empfänger-App reagiert auf diese Meldungen.

## Nachrichtenformat {#section_1624159DD51D4C87B3E5803DEEBCB6B7}

Sie müssen die Nachrichten definieren, damit Absender und Empfänger sie verstehen können. Hier ein Beispiel für eine Suchmeldung:

```js
{ 
"type": "seek", 
"seekTo": 10000 
} 
```

Beim Senden benutzerdefinierter Nachrichten wie der Suchmeldung über die Cast-SDKs ist ein benutzerdefinierter Namensraum erforderlich. Beispiel in JavaScript:

```js
Custom Message Namespace 
var MSG_NAMESPACE = "urn:x-cast:com.adobe.primetime"; 
```

## Herstellen einer Verbindung {#section_B4D40CABDD3E46FDBE7B5651DFF91653}

>[!IMPORTANT]
>
>Browser TVSDK-APIs werden beim Herstellen der Verbindung nicht einbezogen.

Um eine Verbindung herzustellen, müssen Sender und Empfänger die folgenden Aufgaben ausführen:

* Der Absender muss die Dokumentation für die Plattform unter [Sender App Development](https://developers.google.com/cast/docs/sender_apps)lesen.
* Der Empfänger verwendet die Cast-Empfänger-APIs, um eine Verbindung zur Sender-App herzustellen. Beispiel:

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

Informationen zum Senden von Nachrichten an den Empfänger finden Sie in der Dokumentation zur Plattform des Absenders.

>[!IMPORTANT]
>
>Sie müssen den Namensraum für die benutzerdefinierte Nachricht `MSG_NAMESPACE` in alle Nachrichten einschließen.

Für die Receiver-App befolgen Sie die Dokumentation für die APIs für die Empfänger-Empfänger.

**Beispiel einer Chrome-basierten Sender-Nachricht**

```js
window.session.sendMessage(MSG_NAMESPACE, message, successCallback, errorCallback); //https://developers.google.com/cast/docs/reference/chrome/chrome.cast.Session#sendMessage
```

**Chrome-basiertes Ereignis-Handling**

Binden Sie Ereignis-Handler an Ihre Benutzeroberflächenelemente, die Meldungen senden, wenn die entsprechenden Ereignis ausgelöst werden. Bei einer Chrome-basierten Absender-App kann das Ereignis &quot;Suchen&quot;beispielsweise wie folgt gesendet werden:

```js
document.getElementById("#seekBar").addEventListener("click", seekEventHandler); 
   
function seekEventHandler(event) { 
    seekMessage = { type: "seek", seekTo: player.currentTime }; //player is an instance of AdobePSDK.MediaPlayer 
    window.session.sendMessage(MSG_NAMESPACE, seekMessage, successCallback, errorCallback); 
} 
```

**Umgang mit Empfängermeldungen**

In der Empfänger-App ist hier ein Beispiel für die Handhabung der Suchmeldung aufgeführt:

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

