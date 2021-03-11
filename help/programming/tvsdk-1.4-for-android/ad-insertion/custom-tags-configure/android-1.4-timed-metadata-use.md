---
description: Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabedauer mit der Beginn-Zeit übereinstimmt.
title: Verwenden von Zeitmetadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 1%

---


# Verwenden Sie zeitgesteuerte Metadaten {#use-timed-metadata}

Sie können TimedMetadata verwenden, wenn die aktuelle Wiedergabedauer mit der Beginn-Zeit übereinstimmt.

Um diese gespeicherten `TimedMetadata`-Objekte während der Wiedergabe zu verwenden, verwenden Sie die gespeicherten `ArrayList` von [Zeitmetadatenobjekte speichern, während sie gesendet werden.](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md)

1. Führen Sie einen Timer aus und führen Sie wiederholt eine Abfrage der aktuellen Wiedergabedauer durch.
1. Suchen Sie alle `TimedMetadata`-Objekte mit Beginn, die der aktuellen Wiedergabedauer entsprechen.

   Mit diesen Objekten können Sie verschiedene Aktionen ausführen.

   >[!IMPORTANT]
   >
   >Bei der Prüfung, ob die aktuelle Wiedergabezeit mit einem `TimedMetadata`-Objekt übereinstimmt, müssen Sie `shouldTriggerSubscribedTagEvent` als Bedingung einschließen.

   Die Zeitschiene kann sich aufgrund verschiedener Anzeigenverhaltensweisen ändern. So können z. B. ein oder mehrere Werbeunterbrechungen von ihrer ursprünglichen Position in der Zeitleiste verschoben werden, aber `shouldTriggerSubscribedTagEvent` stellt sicher, dass die Beginn-Zeit des Objekts mit der aktuellen Wiedergabedauer übereinstimmt.`TimeMetadata`

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

1. Regelmäßig die statische `TimedMetadata`-Instanzen aus der Liste entfernen, um zu verhindern, dass der Speicher ständig wächst.