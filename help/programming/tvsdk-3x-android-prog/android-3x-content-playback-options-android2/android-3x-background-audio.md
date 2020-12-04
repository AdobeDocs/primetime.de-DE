---
seo-title: Hintergrundaudio aktivieren
title: Hintergrundaudio aktivieren
uuid: aa6dc934-e85c-4db1-901b-9777f47106e6
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# Hintergrundaudio {#enable-background-audio} aktivieren

Um die Audiowiedergabe zu aktivieren, wenn sich die App im Hintergrund befindet, sollte die App die API von MediaPlayer mit dem Argument &quot;true&quot;aufrufen, wenn sich der Player im VORBEREITTEN Status befindet.`enableAudioPlaybackInBackground`

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

Die App sollte die Wiedergabe anhalten, wenn sie den Fokus auf Audio während Ereignissen wie dem Anruf usw. verliert. Das folgende Codefragment zeigt, wie `OnAudioFocusChangeListener` implementiert wird:

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
