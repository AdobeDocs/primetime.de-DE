---
description: In Browser TVSDK können Sie eine bestimmte Position (Zeit) in einem Stream suchen. Ein Stream kann ein Sliding-Window-Playlist oder Video-on-Demand (VOD)-Inhalt sein.
title: Verarbeiten der Suche bei Verwendung der Suchleiste
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# Verarbeiten Sie die Suche bei Verwendung der Suchleiste{#handle-seek-when-using-the-seek-bar}

In Browser TVSDK können Sie eine bestimmte Position (Zeit) in einem Stream suchen. Ein Stream kann ein Sliding-Window-Playlist oder Video-on-Demand (VOD)-Inhalt sein.

>[!IMPORTANT]
>
>Die Suche in einem Live-Stream ist nur für DVR zulässig.

1. Warten Sie, bis Browser TVSDK sich in einem gültigen Status für die Suche befindet.

   Gültige Status sind &quot;VORBEREITEN&quot;, &quot;ABGESCHLOSSEN&quot;, &quot;ANGEHALTEN&quot;und &quot;WIEDERGABE&quot;. Wenn Sie sich in einem gültigen Status befinden, wird sichergestellt, dass die Medienressource erfolgreich geladen wurde. Wenn sich der Player nicht in einem gültigen, suchbaren Zustand befindet, wird beim Versuch, die folgenden Methoden aufzurufen, ein `IllegalStateException` zurückgegeben.

   Sie können beispielsweise auf Browser TVSDK auf Trigger `AdobePSDK.MediaPlayerStatusChangeEvent` mit einem `event.status` von `AdobePSDK.MediaPlayerStatus.PREPARED` warten.

1. Übergeben Sie die angeforderte Suchposition als Parameter an die `MediaPlayer.seek`-Methode in Millisekunden.

   Dadurch wird der Abspielkopf an eine andere Position im Stream verschoben.

   >[!TIP]
   >
   >Die angeforderte Suchposition kann nicht mit der tatsächlichen berechneten Position übereinstimmen.

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. Warten Sie, bis Browser TVSDK das Ereignis `AdobePSDK.PSDKEventType.SEEK_END` Trigger, das die angepasste Position im Attribut `actualPosition` des Ereignisses zurückgibt:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete); 
   onSeekComplete = function (event) {
       // event.actualPosition
   }
   ```

   Dies ist wichtig, da sich die tatsächliche Position des Beginns nach der Suche von der angeforderten Position unterscheiden kann. Es gelten möglicherweise einige der folgenden Regeln:

   * Das Wiedergabeverhalten wird beeinträchtigt, wenn eine Suche oder eine andere Neupositionierung in der Mitte einer Werbeunterbrechung endet oder Werbeunterbrechungen übersprungen werden.
   * Sie können nur in der suchbaren Dauer des Assets suchen. Bei VOD ist dies von 0 bis zur Laufzeit des Assets.

1. Suchen Sie für die im obigen Beispiel erstellte Suchleiste nach `setPositionChangeListener()`, um zu sehen, wann der Benutzer scrubbt:

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

1. Richten Sie Ereignis-Listener-Rückrufe für Änderungen in der Suchfunktion des Benutzers ein.

       Der Suchvorgang ist asynchron, sodass Browser TVSDK die folgenden Ereignisse im Zusammenhang mit der Suche auslöst:
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` , um anzugeben, dass die Suche beginnt.
   * `AdobePSDK.PSDKEventType.SEEK_END` , um anzuzeigen, dass die Suche erfolgreich war.
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` , um anzugeben, dass der Medienplayer die vom Benutzer bereitgestellte Suchposition angepasst hat.

