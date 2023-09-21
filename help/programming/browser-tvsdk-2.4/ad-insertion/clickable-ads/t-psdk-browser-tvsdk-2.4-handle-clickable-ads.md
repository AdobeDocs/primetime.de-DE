---
description: Der MediaPlayer stellt eine notifyClick()-Funktion bereit, die anzeigenbezogene Ereignisse auslöst, wenn eine anklickbare Anzeige wiedergegeben wird. Diese Ereignisse stellen Anzeigen- und Werbeunterbrechungsinformationen bereit, mit denen Ihre App Clickthrough-Funktionen bereitstellen kann.
title: Umgang mit anklickbaren Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Umgang mit anklickbaren Anzeigen {#handle-clickable-ads}

Der MediaPlayer stellt eine notifyClick()-Funktion bereit, die anzeigenbezogene Ereignisse auslöst, wenn eine anklickbare Anzeige wiedergegeben wird. Diese Ereignisse stellen Anzeigen- und Werbeunterbrechungsinformationen bereit, mit denen Ihre App Clickthrough-Funktionen bereitstellen kann.

Der MediaPlayer löst die folgenden Ereignisse aus, wenn eine anklickbare Anzeige wiedergegeben wird:

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

Die `AdClickedEvent` enthält die Informationen, die zur Verarbeitung der Clickthrough-Funktion erforderlich sind.

1. Geben Sie in Ihrem Player ein Steuerelement an, über das Benutzer auf anklickbare Anzeigen klicken können.

   Dies kann eine Schaltfläche oder ein anderes Element sein, um den Klick des Benutzers zu erfassen.
1. Fügen Sie einen Ereignis-Listener für das Anzeigen-Klick-Ereignis des Benutzers hinzu.

   Beispiel:

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. Fügen Sie einen Handler für das Klickereignis des Benutzers hinzu.

   Dieser Handler muss den MediaPlayer auffordern, den `AdClicked` -Ereignis.

   ```
   onAdClick = function (event) { 
       // Get a reference to your player 
       var player = getPlayer(); 
       if (player) { 
           // Call the MediaPlayer's notifyClick function 
           // which gets MediaPlayer to fire AdClicked 
           player.notifyClick(); 
       } 
   } 
   ```

1. Fügen Sie Ereignis-Listener für den MediaPlayer-Anzeigenstart, -Klick und -abgeschlossene Benachrichtigungen hinzu.

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. Fügen Sie Ereignishandler hinzu.
a. Verarbeiten Sie das Anzeigenstartereignis.
Dies kann alles bewirken, z. B. das Einrichten der Benutzeroberfläche für den Benutzer.

   ```
   onAdStarted = function (event) { 
       if (clickAddButton && event && event.ad) { 
           var adClick = event.ad.primaryAsset && event.ad.primaryAsset.adClick; 
           if (adClick && adClick.isValid) { 
               // Do some initial processing  
               // when the ad starts, prior 
               // to the user's click. 
           } 
       } 
   }
   ```

   b. Behandeln Sie das angeklickte Anzeigen-Ereignis.
In diesem Beispiel erhalten wir Anzeigeninformationen aus dem Ereignis und öffnen ein neues Browser-Fenster mit diesen Informationen:

   ```
   onAdClickedEvent = function (event) { 
       if (event && event.ad) { 
           var adClick = event.adClick; 
           if (!(adClick && adClick.isValid)) { 
               adClick = event.ad.primaryAsset && event.ad.primaryAsset.adClick; 
           } 
           if (adClick && adClick.isValid) 
           { 
               // Do something with the currently playing ad 
               window.open(adClick.url); 
           } 
       } 
   }
   ```

   c. Behandeln Sie das Ereignis &quot;ad completed&quot;.

   ```
   onAdCompleted = function (event) { 
       if (clickAddButton) { 
           clickAddButton.setAttribute('hidden', 'true'); 
       } 
   }
   ```
