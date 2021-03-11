---
description: Mit dem Benachrichtigungsabschnitt der Browser TVSDK-Bibliothek können Sie ein Protokollierungs- und Debugging-System erstellen, das für Diagnose- und Validierungszwecke nützlich sein kann.
title: Benachrichtigungssystem
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Benachrichtigungssystem {#notification-system}

Mit dem Benachrichtigungsabschnitt der Browser TVSDK-Bibliothek können Sie ein Protokollierungs- und Debugging-System erstellen, das für Diagnose- und Validierungszwecke nützlich sein kann.

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

Browser TVSDK hat eine *no throw*-Richtlinie für die API. Die meisten Methoden geben einen `PSDKErrorCode`-Wert zurück, der angibt, ob die Methode erfolgreich ausgeführt wurde. Eine vollständige Liste aller möglichen `PSDKErrorCode`-Werte finden Sie unter Browser TVSDK API-Referenzen.

Asynchrone Fehler werden über die spezifischen Ereignis gemeldet.

Browser TVSDK sendet `MediaPlayer`-Ereignis, um Informationen zur Player-Aktivität bereitzustellen. Sie müssen Ereignis-Listener implementieren, um diese Ereignis zu erfassen und darauf zu reagieren.

>[!TIP]
>
>Wichtige Ereignis und Informationen werden in der Webbrowser-Konsole protokolliert.

## Benachrichtigungen {#section_06B96633433D497E842FB7ADD5F2C7DA}

Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen. Der Kern des Browser TVSDK-Benachrichtigungssystems ist die `Notification`-Klasse, die eine eigenständige Benachrichtigung darstellt.

So richten Sie Ihre Anwendung zum Warten auf Benachrichtigungen ein:

1. Suchen Sie mithilfe der MediaPlayer-Instanz nach Änderungen des MediaPlayer-Status.

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Implementieren Sie den Rückruf.

   Der Rückruf empfängt eine Instanz von `AdobePSDK.MediaPlayerStatusChangeEvent` und Browser TVSDK übergibt dieses Ereignis-Objekt an den Rückruf, der den neuen Player-Status enthält.
1. Ihre Anwendung kann andere Ereignis abhören, die von Browser TVSDK mit der `MediaPlayer`-Instanz gesendet werden.

