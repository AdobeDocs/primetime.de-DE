---
title: Hintergrundaudio aktivieren
description: Hintergrundaudio aktivieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# Hintergrundaudio aktivieren {#enable-background-audio}

Um die Audiowiedergabe zu aktivieren, wenn die App im Hintergrund ausgeführt wird, sollte das Programm `enableAudioPlaybackInBackground` API von MediaPlayer mit &quot;true&quot;als Argument, wenn der Player im Status &quot;PREPARED&quot;ist.

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

Das Programm sollte die Wiedergabe anhalten, wenn es bei Ereignissen wie der Reaktion auf das Telefon den Fokus auf das Audio verliert. Das folgende Codefragment zeigt die Implementierung der `OnAudioFocusChangeListener`:

```
/** 
 * Register the AudioFocus Change listener to track Audio focus from device. 
 */ 
 AudioManager.OnAudioFocusChangeListener onAudioFocusChangeListener = new AudioManager.OnAudioFocusChangeListener(){ 
     @Override 
     public void onAudioFocusChange(int focusChange){ 
          switch(focusChange){ 
               case AudioManager.AUDIOFOCUS_GAIN: 
                    break; 
               case AudioManager.AUDIOFOCUS_LOSS_TRANSIENT_CAN_DUCK: 
                    /* lower output volume*/ 
                    break; 
               case AudioManager.AUDIOFOCUS_LOSS: 
               case AudioManager.AUDIOFOCUS_LOSS_TRANSIENT: 
                    if(_lastKnownStatus ==MediaPlayerStatus.PLAYING) 
                         _mediaPlayer.pause(); 
                    break; 
          } 
     } 
}; 
 
AudioManager audioManager = (AudioManager) getActivity().getApplicationContext().getSystemService(Context.AUDIO_SERVICE); 
audioManager.requestAudioFocus(onAudioFocusChangeListener, AudioManager.STREAM_MUSIC, AudioManager.AUDIOFOCUS_GAIN);
```
