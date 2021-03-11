---
description: TVSDK unterstützt die Anzeige von linearen Video Player-Ad Interface Definition (VPAID)-Anzeigen in einer Werbeunterbrechung. VPAID Version 1.0 erfordert Flash, während Version 2.0 auch mit Browser TVSDK und JavaScript funktioniert.
title: Lineare VPAID-Anzeigen in einer Werbeunterbrechung anzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Lineare VPAID-Anzeigen in einer Werbeunterbrechung anzeigen{#display-linear-vpaid-ads-in-an-ad-break}

TVSDK unterstützt die Anzeige von linearen Video Player-Ad Interface Definition (VPAID)-Anzeigen in einer Werbeunterbrechung. VPAID Version 1.0 erfordert Flash, während Version 2.0 auch mit Browser TVSDK und JavaScript funktioniert.

Um VPAID-Anzeigen korrekt anzuzeigen, müssen Sie einen Anzeigen-Container ( `AdContainerView`) innerhalb der `MediaPlayerContext`-Instanz angeben.

Einschränkungen für VPAID-Anzeigen:

* VPAID-Anzeigen haben nicht unbedingt eine vordefinierte Dauer, da die Anzeige interaktiv sein kann. Daher entspricht die Anzeigendauer (durch die Anzeigenserverantwort definiert) möglicherweise nicht immer genau der tatsächlichen Dauer der Anzeige.
* Für VPAID 1.0-Anzeigen erfordert TVSDK die Installation des Flash-Players 14.0.0.160 oder höher auf dem Gerät. Bei älteren Versionen des Flash-Players ist diese Funktion deaktiviert und VPAID 1.0-Anzeigen werden übersprungen.

So richten Sie einen Container für die Anzeige von VPAID-Anzeigen (Version 1.0 oder 2.0) innerhalb einer Werbeunterbrechung ein:

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

1. Wenn die Größe der Ansicht geändert wird, setzen Sie die Größe des Containers der Anzeige zurück.

   ```
   adContainer.setSize(stage.stageWidth, stage.stageHeight);
   ```

   >[!NOTE]
   >
   >Wenn Sie ein Ereignis zum Ändern des Vollbildmodus erhalten und die neue Größe auf dem Container der Anzeige festlegen, übergeben Sie den Anzeigestatus der Bühne wie folgt, um sicherzustellen, dass die Größe des  korrekt angepasst wird:
   >
   >
   ```
   >private function onFullScreenChange(event:FullScreenEvent):void { 
   >if (_adContainer) 
   >{ _adContainer.setSize(stage.stageWidth, stage.stageHeight, stage.displayState); } 
   >}
   >```

