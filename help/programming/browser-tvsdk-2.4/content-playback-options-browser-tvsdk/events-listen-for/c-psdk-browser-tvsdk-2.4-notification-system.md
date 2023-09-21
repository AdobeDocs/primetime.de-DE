---
description: Im Benachrichtigungsabschnitt der Browser TVSDK-Bibliothek können Sie ein Protokollierungs- und Debugging-System erstellen, das für Diagnose- und Validierungszwecke nützlich sein kann.
title: Benachrichtigungssystem
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Benachrichtigungssystem {#notification-system}

Im Benachrichtigungsabschnitt der Browser TVSDK-Bibliothek können Sie ein Protokollierungs- und Debugging-System erstellen, das für Diagnose- und Validierungszwecke nützlich sein kann.

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

Browser TVSDK verfügt über eine *no throw* -Richtlinie für die zugehörige API. Die meisten Methoden geben eine `PSDKErrorCode` -Wert, um anzugeben, ob die Methode erfolgreich ausgeführt wurde. Für eine vollständige Liste aller möglichen `PSDKErrorCode` -Werte, siehe Browser TVSDK-API-Referenzen.

Asynchrone Fehler werden über die spezifischen Ereignisse benachrichtigt.

Browser TVSDK-Dispatches `MediaPlayer` -Ereignisse, um Informationen zur Player-Aktivität bereitzustellen. Sie müssen Ereignis-Listener implementieren, um diese Ereignisse zu erfassen und darauf zu reagieren.

>[!TIP]
>
>Wichtige Ereignisse und Informationen werden in der Webbrowser-Konsole protokolliert.

## Benachrichtigungen abrufen {#section_06B96633433D497E842FB7ADD5F2C7DA}

Sie können Benachrichtigungen überwachen und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen. Der Kern des Browser TVSDK-Benachrichtigungssystems ist der `Notification` -Klasse, die eine eigenständige Benachrichtigung darstellt.

So richten Sie Ihre Anwendung so ein, dass auf Benachrichtigungen überwacht wird:

1. Suchen Sie mithilfe der MediaPlayer-Instanz nach Änderungen des MediaPlayer-Status.

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Implementieren Sie den Rückruf.

   Der Rückruf empfängt eine Instanz der `AdobePSDK.MediaPlayerStatusChangeEvent`und Browser TVSDK übergibt dieses Ereignisobjekt an den Callback, der den neuen Player-Status enthält.
1. Ihre Anwendung kann andere Ereignisse überwachen, die vom Browser TVSDK mithilfe der `MediaPlayer` -Instanz.
