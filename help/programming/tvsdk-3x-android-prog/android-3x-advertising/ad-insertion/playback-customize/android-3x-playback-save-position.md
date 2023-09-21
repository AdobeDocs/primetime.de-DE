---
description: Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.
title: Speichern Sie die Videoposition und nehmen Sie die Fortsetzung später vor
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Speichern Sie die Videoposition und nehmen Sie die Fortsetzung später vor {#save-the-video-position-and-resume-later}

Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.

Dynamisch eingefügte Anzeigen unterscheiden sich zwischen Benutzersitzungen, sodass die Position gespeichert wird **mit** Geteilte Anzeigen beziehen sich auf eine andere Position in einer zukünftigen Sitzung. TVSDK bietet Methoden zum Abrufen der Wiedergabeposition bei gleichzeitigem Ignorieren von geteilten Anzeigen.

1. Wenn der Benutzer ein Video beendet, ruft die Anwendung die Position im Video ab und speichert sie.

   >[!TIP]
   >
   >Anzeigendauern sind nicht enthalten.

   Werbeunterbrechungen können in jeder Sitzung aufgrund von Anzeigenmustern, Frequenzlimitierung usw. variieren. Die aktuelle Zeit des Videos in einer Sitzung kann in einer zukünftigen Sitzung anders sein. Beim Speichern einer Position im Video ruft die Anwendung die lokale Zeit ab, die Sie auf dem Gerät oder in einer Datenbank auf dem Server speichern können.

   Wenn sich der Benutzer beispielsweise in der 20. Minute des Videos befindet und diese Position fünf Minuten Anzeigen enthält, `getCurrentTime` gibt 1200 Sekunden zurück, während `getLocalTime` an dieser Position wird 900 Sekunden zurückgegeben.

   >[!IMPORTANT]
   >
   >Die lokale Zeit und die aktuelle Zeit sind für Live-/lineare Streams identisch. In diesem Fall `convertToLocalTime` hat keine Auswirkung. Für VOD bleibt die Ortszeit unverändert, während Anzeigen abgespielt werden.

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

1. Stellen Sie die Benutzersitzung wieder her, wenn die Player-Aktivität wieder aufgenommen wird.

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

   * Um die Wiedergabe des Videos von der Position aus fortzusetzen, die in einer vorherigen Sitzung gespeichert wurde, verwenden Sie `seekToLocalTime`.

     >[!TIP]
     >
     >Diese Methode wird nur mit lokalen Zeitwerten aufgerufen. Wenn die Methode mit aktuellen Zeitergebnissen aufgerufen wird, tritt ein falsches Verhalten auf.

   * Um zur aktuellen Zeit zu gelangen, verwenden Sie `seek`.

1. Wenn Ihre Anwendung die `onStatusChanged` Statusänderungsereignis, suchen Sie nach der gespeicherten lokalen Zeit.

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

1. Stellen Sie die Werbeunterbrechungen bereit, wie in der Benutzeroberfläche der Anzeigenrichtlinie angegeben.
1. Implementieren Sie eine benutzerdefinierte Anzeigenrichtlinienauswahl, indem Sie die standardmäßige Anzeigenrichtlinienauswahl erweitern.
1. Stellen Sie die Werbeunterbrechungen bereit, die dem Benutzer durch Implementierung von `selectAdBreaksToPlay`.

   Diese Methode umfasst eine Pre-Roll-Werbeunterbrechung und die Mid-Roll-Werbeunterbrechungen vor der lokalen Zeitposition. Ihre Anwendung kann entscheiden, eine Pre-Roll-Werbeunterbrechung wiederzugeben und zur festgelegten lokalen Zeit fortzufahren, eine Mid-Roll-Werbeunterbrechung abzuspielen und zur festgelegten lokalen Zeit fortzufahren oder keine Werbeunterbrechungen wiederzugeben.
