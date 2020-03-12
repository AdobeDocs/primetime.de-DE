---
seo-title: Hintergrundaudio aktivieren
title: Hintergrundaudio aktivieren
uuid: aa6dc934-e85c-4db1-901b-9777f47106e6
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Hintergrundaudio aktivieren {#enable-background-audio}

Um die Audiowiedergabe zu aktivieren, wenn sich die App im Hintergrund befindet, sollte die App die MediaPlayer- `enableAudioPlaybackInBackground` API mit true als Argument aufrufen, wenn sich der Player im VORBEREITTEN Status befindet.

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

Die App sollte die Wiedergabe anhalten, wenn sie den Fokus auf Audio während Ereignissen wie dem Anruf usw. verliert. Das folgende Codefragment zeigt, wie die `OnAudioFocusChangeListener`:

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
