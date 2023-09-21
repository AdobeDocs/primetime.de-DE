---
description: Im Browser TVSDK können Sie nach einer bestimmten Position (Uhrzeit) in einem Stream suchen. Ein Stream kann eine gleitende Fensterwiedergabeliste oder ein VOD-Inhalt (Video-on-Demand) sein.
title: Suchen bei Verwendung der Suchleiste bearbeiten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Suchen bei Verwendung der Suchleiste bearbeiten{#handle-seek-when-using-the-seek-bar}

Im Browser TVSDK können Sie nach einer bestimmten Position (Uhrzeit) in einem Stream suchen. Ein Stream kann eine gleitende Fensterwiedergabeliste oder ein VOD-Inhalt (Video-on-Demand) sein.

>[!IMPORTANT]
>
>Die Suche in einem Live-Stream ist nur für DVR erlaubt.

1. Warten Sie, bis das Browser TVSDK für die Suche einen gültigen Status aufweist.

   Gültige Status sind PREPARED, COMPLETE, PAUSED und PLAYING. Ein gültiger Status stellt sicher, dass die Medienressource erfolgreich geladen wurde. Wenn der Player keinen gültigen suchbaren Status aufweist, wird beim Versuch, die folgenden Methoden aufzurufen, ein `IllegalStateException`.

   Sie können beispielsweise auf den Trigger Browser TVSDK warten  `AdobePSDK.MediaPlayerStatusChangeEvent`  mit einer `event.status` von `AdobePSDK.MediaPlayerStatus.PREPARED`.

1. Übergeben Sie die angeforderte Suchposition an die `MediaPlayer.seek` -Methode als Parameter in Millisekunden.

   Dadurch wird der Abspielkopf an eine andere Position im Stream verschoben.

   >[!TIP]
   >
   >Die angeforderte Suchposition entspricht möglicherweise nicht der tatsächlichen berechneten Position.

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. Warten Sie, bis das Browser TVSDK den Trigger  `AdobePSDK.PSDKEventType.SEEK_END`  -Ereignis, das die angepasste Position im Ereignis `actualPosition` Attribut:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete); 
   onSeekComplete = function (event) {
       // event.actualPosition
   }
   ```

   Dies ist wichtig, da sich die tatsächliche Startposition nach der Suche von der angeforderten Position unterscheiden kann. Es können einige der folgenden Regeln angewendet werden:

   * Das Wiedergabe-Verhalten ist betroffen, wenn eine Suche oder eine andere Neupositionierung mitten in einer Werbeunterbrechung endet oder Werbeunterbrechungen überspringt.
   * Sie können nur in der suchbaren Dauer des Assets suchen. Bei VOD ist dies von 0 bis zur Dauer des Assets.

1. Suchen Sie für die im obigen Beispiel erstellte Suchleiste nach `setPositionChangeListener()` , um zu sehen, wann der Benutzer scrubbt:

   ```js
   seekBar.setPositionChangeListener(function (pos) { 
                   var range = player.seekableRange; 
                   if (range) { 
                       var duration = range.duration; 
                       var time = duration * pos; // seek bar range is [0,1] 
                       player.seek(time); 
   
                       console.log("seek to " + time + " / " + duration); 
                   } 
   
               }); 
   ```

1. Richten Sie Ereignis-Listener-Rückrufe für Änderungen in der Suchaktivität des Benutzers ein.

       Der Suchvorgang ist asynchron, sodass Browser TVSDK diese Ereignisse im Zusammenhang mit der Suche sendet:
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` , um anzugeben, dass die Suche beginnt.
   * `AdobePSDK.PSDKEventType.SEEK_END` , um anzugeben, dass die Suche erfolgreich war.
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` , um anzugeben, dass der Medienplayer die vom Benutzer angegebene Suchposition angepasst hat.
