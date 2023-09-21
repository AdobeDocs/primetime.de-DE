---
description: Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabezeit mit der Startzeit übereinstimmt.
title: Zeitgesteuerte Metadaten verwenden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Zeitgesteuerte Metadaten verwenden {#use-timed-metadata}

Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabezeit mit der Startzeit übereinstimmt.

So verwenden Sie diese gespeicherten `TimedMetadata` Objekte während der Wiedergabe verwenden Sie die gespeicherten `ArrayList` von [Speichern von zeitgesteuerten Metadatenobjekten beim Versand](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md).

1. Führen Sie einen Timer aus und fragen Sie wiederholt die aktuelle Wiedergabedauer ab.
1. Suchen Sie alle `TimedMetadata` -Objekte mit Startzeiten, die der aktuellen Wiedergabedauer entsprechen.

   Sie können diese Objekte verwenden, um verschiedene Aktionen durchzuführen.

   >[!IMPORTANT]
   >
   >Bei der Überprüfung, ob die aktuelle Wiedergabezeit mit einer `TimedMetadata` Objekte einschließen `shouldTriggerSubscribedTagEvent` als Bedingung.

   Die Timeline kann sich aufgrund verschiedener Anzeigenverhaltensweisen ändern. Beispielsweise können eine oder mehrere Werbeunterbrechungen von ihren ursprünglichen Positionen in der Timeline verschoben werden, aber `shouldTriggerSubscribedTagEvent` stellt sicher, dass `TimeMetadata` Die Startzeit des Objekts entspricht der aktuellen Wiedergabezeit.

   Beispiel:

   ```java
    _playbackClockEventListener = new Clock.ClockEventListener() {
       @Override
       public void onTick(String name) {
           getActivity().runOnUiThread(new Runnable() {
               @Override
               public void run() {
                   /* handle timedmetadata object list  */ 
                   if (_mediaPlayer != null && _timedMetadataList != null && _timedMetadataList.size() > 0) {
                       if (_lastKnownStatus == MediaPlayer.PlayerState.PLAYING) {
                           long localTime = _mediaPlayer.getLocalTime();
                           Iterator<TimedMetadata> iterator = _timedMetadataList.iterator(); 
                           while (iterator.hasNext()) {
                               TimedMetadata timedMetadata = iterator.next();
                               long diff = localTime - timedMetadata.getTime();
                               if (diff >= 0 &&
                                   diff <= PLAYBACK_CLOCK_INTERVAL &&
                                   _mediaPlayer.shouldTriggerSubscribedTagEvent()) {
                                   // use timed metadata object
                               }
                           }
                       }
                   }
               }
           });
       }
   };
   _playbackClock.addClockEventListener(_playbackClockEventListener);
   ```

1. Periodisches Leeren veraltet `TimedMetadata` -Instanzen aus der Liste, um zu verhindern, dass der Speicher ständig wächst.
