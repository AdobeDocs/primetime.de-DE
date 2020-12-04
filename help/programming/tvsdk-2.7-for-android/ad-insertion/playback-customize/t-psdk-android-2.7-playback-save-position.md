---
description: Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.
seo-description: Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.
seo-title: Speichern Sie die Videoposition und nehmen Sie den Vorgang später wieder auf
title: Speichern Sie die Videoposition und nehmen Sie den Vorgang später wieder auf
uuid: 007c8e89-54f4-4dfd-81f8-b931e216e724
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---


# Speichern Sie die Videoposition und setzen Sie die Wiedergabe später fort.{#save-the-video-position-and-resume-later}

Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.

Dynamisch eingefügte Anzeigen unterscheiden sich von Benutzersitzung zu Benutzersitzung. Daher bezieht sich das Speichern der Position **mit** geteilten Anzeigen auf eine andere Position in einer zukünftigen Sitzung. TVSDK stellt Methoden zum Abrufen der Wiedergabeposition bereit, während geteilte Anzeigen ignoriert werden.

1. Wenn der Benutzer ein Video beendet, ruft Ihre Anwendung die Position im Video ab und speichert sie.

   >[!TIP]
   >
   >Die Anzeigendauer ist nicht inbegriffen.

   Werbeunterbrechungen können je nach Sitzung unterschiedlich ausfallen, da Anzeigenmuster, Frequenzbegrenzungen usw. gelten. Die aktuelle Zeit des Videos in einer Sitzung kann in einer zukünftigen Sitzung anders sein. Beim Speichern einer Position im Video ruft die Anwendung die lokale Zeit ab, die Sie auf dem Gerät oder in einer Datenbank auf dem Server speichern können.

   Wenn sich der Benutzer beispielsweise in der 20. Minute des Videos befindet und diese Position fünf Minuten der Anzeigen umfasst, gibt `getCurrentTime` 1200 Sekunden zurück, während `getLocalTime` an dieser Position 900 Sekunden zurückgibt.

   >[!IMPORTANT]
   >
   >Die lokale Zeit und die aktuelle Zeit sind für Live-/lineare Streams identisch. In diesem Fall hat `convertToLocalTime` keine Auswirkung. Bei VOD bleibt die Ortszeit unverändert, während Anzeigen abgespielt werden.

   ```java
   // Save the user session when player activity stops 
       @Override 
       public void onStop(){ 
           super.onStop(); 
           ... 
           prefs = PreferenceManager.getDefaultSharedPreferences( 
                                     getActivity().getApplicationContext()); 
           SharedPreferences.Editor editor = prefs.edit(); 
           // get the local time where stream stopped playing and  
           // save it in System preferences 
           editor.putLong(LAST_LOCAL_TIME, _mediaPlayer.getLocalTime());  
           editor.putString(LAST_MEDIA_RESOURCE, _contentInfo.toMediaResource().getUrl()); 
           editor.commit(); 
           ... 
       }
   ```

1. Stellen Sie die Benutzersitzung wieder her, wenn die Player-Aktivität fortgesetzt wird.

   ```java
   @Override 
   public void onResume() { 
       super.onResume(); 
       ... 
       prefs =  
         PreferenceManager.getDefaultSharedPreferences(getActivity().getApplicationContext()); 
       if (prefs.getString(LAST_MEDIA_RESOURCE, "nil"). 
         equals(_contentInfo.toMediaResource().getUrl())) { 
           _lastKnownLocalTime =  
             prefs.getLong(LAST_LOCAL_TIME, 0); // get the last local time  
                                                // saved in system preferences 
           if(_lastKnownLocalTime > 0) { 
               _shouldResumePlayback = true; 
           } 
       } 
       ... 
   } 
   ```

1. So setzen Sie das Video an derselben Position fort:

   * Um das Video von der Position wiederzugeben, die in einer vorherigen Sitzung gespeichert wurde, verwenden Sie `seekToLocalTime`.

      >[!TIP]
      >
      >Diese Methode wird nur mit lokalen Zeitwerten aufgerufen. Wenn die Methode mit den aktuellen Zeitergebnissen aufgerufen wird, tritt ein falsches Verhalten auf.

   * Um zur aktuellen Zeit zu suchen, verwenden Sie `seek`.

1. Wenn Ihre Anwendung das Ereignis `onStatusChanged` zur Statusänderung erhält, suchen Sie nach der gespeicherten Ortszeit.

   ```java
   private final MediaPlayer.PlaybackEventListener _playbackEventListener =  
     new MediaPlayer.PlaybackEventListener() { 
       @Override 
       public void onPrepared() { 
           ... 
           if(_shouldResumePlayback){ 
               if(_lastKnownLocalTime >= 0) { 
                    _mediaPlayer.seekToLocalTime(_lastKnownLocalTime); 
               } 
           } 
           ... 
       } 
       ... 
   }
   ```

1. Stellen Sie die Werbeunterbrechungen gemäß den Angaben in der Benutzeroberfläche der Anzeigenrichtlinie bereit.
1. Implementieren Sie eine benutzerdefinierte Anzeigenrichtlinienauswahl, indem Sie die standardmäßige Anzeigenrichtlinien-Auswahl erweitern.
1. Geben Sie die Werbeunterbrechungen an, die dem Benutzer durch Implementierung von `selectAdBreaksToPlay` angezeigt werden müssen.

   Diese Methode umfasst eine Pre-Roll-Werbeunterbrechung und die Mid-Roll-Werbeunterbrechungen vor der lokalen Zeitposition. Ihre Anwendung kann beschließen, eine Pre-Roll-Werbeunterbrechung auszuführen und zur angegebenen Ortszeit wiederaufzunehmen, eine Mid-Roll-Werbeunterbrechung abzuspielen und zur angegebenen Ortszeit fortzufahren oder keine Werbeunterbrechungen wiederzugeben.
