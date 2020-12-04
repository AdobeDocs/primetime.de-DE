---
description: Der MediaPlayer stellt eine notificationClick()-Funktion bereit, mit der bei der Wiedergabe einer klickbaren Anzeige anzeigenbezogene Ereignis ausgelöst werden. Diese Ereignis enthalten Anzeigen- und Werbeunterbrechungsinformationen, die Ihre App zur Bereitstellung von Clickthrough-Funktionen verwenden kann.
seo-description: Der MediaPlayer stellt eine notificationClick()-Funktion bereit, mit der bei der Wiedergabe einer klickbaren Anzeige anzeigenbezogene Ereignis ausgelöst werden. Diese Ereignis enthalten Anzeigen- und Werbeunterbrechungsinformationen, die Ihre App zur Bereitstellung von Clickthrough-Funktionen verwenden kann.
seo-title: Handhabung anklickbarer Anzeigen
title: Handhabung anklickbarer Anzeigen
uuid: 5d3c9d36-60d7-4272-a523-7d1fe0e1615f
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Umgang mit klickbaren Anzeigen {#handle-clickable-ads}

Der MediaPlayer stellt eine notificationClick()-Funktion bereit, mit der bei der Wiedergabe einer klickbaren Anzeige anzeigenbezogene Ereignis ausgelöst werden. Diese Ereignis enthalten Anzeigen- und Werbeunterbrechungsinformationen, die Ihre App zur Bereitstellung von Clickthrough-Funktionen verwenden kann.

Der MediaPlayer löst folgende Ereignis aus, wenn eine anklickbare Anzeige wiedergegeben wird:

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

Die `AdClickedEvent` enthält die Informationen, die zur Verarbeitung der Clickthrough-Funktion erforderlich sind.

1. Geben Sie in Ihrem Player ein Steuerelement an, damit Benutzer auf klickbare Anzeigen klicken können.

   Dies kann eine Schaltfläche oder ein anderes Element zur Erfassung des Klicks des Benutzers sein.
1. hinzufügen ein Ereignis-Listener für das Anzeigen-Klick-Ereignis des Benutzers.

   Beispiel:

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. hinzufügen einen Handler für das click-Ereignis des Benutzers.

   Dieser Handler muss den MediaPlayer auffordern, das `AdClicked`-Ereignis auszulösen.

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

1. hinzufügen Ereignis-Listener für den MediaPlayer-Anzeigenordner, Benachrichtigungen mit angeklickter und abgeschlossener Anzeige.

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. hinzufügen Ereignis-Handler.
a. Behandeln Sie das Ereignis des Beginns der Anzeige.
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

   b. Behandeln Sie das angeklickte Ereignis.
In diesem Beispiel erhalten wir Anzeigeninformationen aus dem Ereignis und öffnen ein neues Browserfenster mit den folgenden Informationen:

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

   c. Behandeln Sie das Ereignis mit abgeschlossener Anzeige.

   ```
   onAdCompleted = function (event) { 
       if (clickAddButton) { 
           clickAddButton.setAttribute('hidden', 'true'); 
       } 
   }
   ```
