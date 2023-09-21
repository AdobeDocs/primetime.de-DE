---
description: TVSDK unterstützt die Anzeige von linearen VPAID-Anzeigen (Video Player-Ad Interface Definition) in einer Werbeunterbrechung. VPAID Version 1.0 erfordert Flash, während Version 2.0 auch mit Browser TVSDK und JavaScript funktioniert.
title: Lineare VPAID-Anzeigen in einer Werbeunterbrechung anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Lineare VPAID-Anzeigen in einer Werbeunterbrechung anzeigen{#display-linear-vpaid-ads-in-an-ad-break}

TVSDK unterstützt die Anzeige von linearen VPAID-Anzeigen (Video Player-Ad Interface Definition) in einer Werbeunterbrechung. VPAID Version 1.0 erfordert Flash, während Version 2.0 auch mit Browser TVSDK und JavaScript funktioniert.

Um VPAID-Anzeigen korrekt anzuzeigen, müssen Sie einen Anzeigen-Container ( `AdContainerView`) innerhalb der `MediaPlayerContext` -Instanz.

Einschränkungen für VPAID-Anzeigen:

* VPAID-Anzeigen haben nicht unbedingt eine vordefinierte Dauer, da die Anzeige interaktiv sein kann. Daher entspricht die Anzeigendauer (definiert durch die Anzeigenserver-Antwort) möglicherweise nicht immer genau der tatsächlichen Dauer der Anzeige.
* Für VPAID 1.0-Anzeigen erfordert TVSDK die Installation des Flash-Players 14.0.0.160 oder höher auf dem Gerät. Bei früheren Versionen des Flash-Players ist diese Funktion deaktiviert und VPAID 1.0-Anzeigen werden übersprungen.

So richten Sie einen Anzeigen-Container für die Anzeige von VPAID-Anzeigen (Version 1.0 oder 2.0) innerhalb einer Werbeunterbrechung ein:

1. Verwenden Sie den folgenden Beispielcode, um einen Anzeigen-Container einzurichten, der VPAID-Anzeigen anzeigen kann.

   ```
   var context:MediaPlayerContext =  
     new MediaPlayerContext(_authorizedFeatureHelper.authorizedFeatures); 
   
   adContainer = new AdContainerView(); 
   adContainer.x = adContainer.y = 0; 
   adContainer.setSize(videoContainer.width, videoContainer.height); 
   addChild(adContainer); 
   
   context.adContainer = adContainer; 
   _player = new DefaultMediaPlayer(context);
   ```

1. Wenn die Größe der Ansicht geändert wird, setzen Sie die Größe des Anzeigen-Containers zurück.

   ```
   adContainer.setSize(stage.stageWidth, stage.stageHeight);
   ```

   >[!NOTE]
   >
   >Wenn Sie ein Vollbildänderungsereignis erhalten und die neue Größe im Anzeigenbehälter festlegen, übergeben Sie den Anzeigestatus der Bühne wie folgt, um sicherzustellen, dass die Größe des Players korrekt geändert wird:
   >
   >```
   >private function onFullScreenChange(event:FullScreenEvent):void { 
   >if (_adContainer) 
   >{ _adContainer.setSize(stage.stageWidth, stage.stageHeight, stage.displayState); } 
   >}
   >```
   >
