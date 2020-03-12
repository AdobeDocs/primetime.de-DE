---
description: Der Begriff "Sofort-Ein"bezieht sich auf das Vorausladen eines oder mehrerer Kanal, sodass ein Benutzer, der einen Kanal auswählt oder Kanal wechselt, sofort die Inhaltswiedergabe sieht. Die Pufferung erfolgt bereits, wenn der Beginn sie ansieht.
seo-description: Der Begriff "Sofort-Ein"bezieht sich auf das Vorausladen eines oder mehrerer Kanal, sodass ein Benutzer, der einen Kanal auswählt oder Kanal wechselt, sofort die Inhaltswiedergabe sieht. Die Pufferung erfolgt bereits, wenn der Beginn sie ansieht.
seo-title: Sofort ein
title: Sofort ein
uuid: 4cb4d221-170f-46e8-af26-32f259377617
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Sofort ein {#instant-on}

Der Begriff &quot;Sofort-Ein&quot;bezieht sich auf das Vorausladen eines oder mehrerer Kanal, sodass ein Benutzer, der einen Kanal auswählt oder Kanal wechselt, sofort die Inhaltswiedergabe sieht. Die Pufferung erfolgt bereits, wenn der Beginn sie ansieht.

TVSDK initialisiert ohne sofortiges Einschalten die wiederzugebenden Medien, jedoch nicht die Pufferung des Streams, bis die Anwendung aufruft `play`. Dem Benutzer werden erst dann Inhalte angezeigt, wenn die Pufferung abgeschlossen ist. Mit dem sofortigen Start können Sie mehrere Instanzen des Medienplayers (oder des Medienplayer-Elementladers) starten, und TVSDK-Beginn können die Streams sofort zwischenspeichern.

Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird sofort die Wiedergabe des neuen Kanal-Beginns `play` aufgerufen.

Obwohl die Anzahl der `MediaPlayer` Instanzen, die TVSDK ausführen kann, nicht begrenzt ist, verbraucht das Ausführen von mehr Instanzen mehr Ressourcen. Die Anwendungsleistung kann durch die Anzahl der ausgeführten Instanzen beeinträchtigt werden. Weitere Informationen zu diesen Instanzen finden Sie unter Medienressource mit MediaPlayerItemLoader [laden](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

## Pufferung für sofortige Wiedergabe konfigurieren {#configure-buffering-for-instant-on-playback}

Bei sofortigem Einschalten können Benutzer die Kanal und die Wiedergabe-Beginn sofort ohne Wartezeit wechseln. Wenn Sie &quot;Sofort aktivieren&quot;aktivieren, puffert TVSDK einen oder mehrere Kanal, bevor die Wiedergabe beginnt.

1. Vergewissern Sie sich, dass die Ressource geladen wurde und wiedergegeben werden kann, indem Sie überprüfen, ob der Status VORBEREITET ist.
1. Rufen Sie vor dem Aufruf `play`die `prepareBuffer` einzelnen `MediaPlayer` Instanzen auf.

   Dies ermöglicht sofortiges Ein, was bedeutet, dass TVSDK-Beginn Pufferung ohne tatsächliche Wiedergabe der Medienressource durchführen. TVSDK sendet das `BUFFERING_COMPLETED` Ereignis, wenn der Puffer voll ist.

   >[!NOTE]
   >
   >Standardmäßig `prepareBuffer` und `prepareToPlay` richten Sie den Medienstream so ein, dass er von Anfang an als Beginn wiedergegeben wird. Übergeben Sie die Position (in Millisekunden) an eine andere Stelle, um einen Beginn zu `prepareToPlay`erzielen.

   ```java
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state,  
                              MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               // By default, prepareToPlay and prepareBuffer buffer and start playing 
               // from the beginning of the stream. To start at another position, 
               // pass it into prepareToPlay. This example starts 5 seconds into the stream. 
               _mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               _mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. Wenn Sie das `BUFFERING_COMPLETE` Ereignis erhalten, zeigen Sie mit dem Beginn, der das Element abspielt, visuelles Feedback an, um anzuzeigen, dass der Inhalt vollständig gepuffert ist.

   Bei einem Aufruf `play`sollte die Wiedergabe sofort beginnen.

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
