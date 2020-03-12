---
description: Ab dem Zeitpunkt, zu dem Sie die MediaPlayer-Instanz erstellen, bis zu dem Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Transitionen zwischen den Status ab.
seo-description: Ab dem Zeitpunkt, zu dem Sie die MediaPlayer-Instanz erstellen, bis zu dem Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Transitionen zwischen den Status ab.
seo-title: MediaPlayer-Objektlebenszyklus
title: MediaPlayer-Objektlebenszyklus
uuid: 6670a30c-7053-4754-bc36-6bb8590c001d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayer-Objektlebenszyklus{#mediaplayer-object-lifecycle}

Ab dem Zeitpunkt, zu dem Sie die MediaPlayer-Instanz erstellen, bis zu dem Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Transitionen zwischen den Status ab.

Einige Vorgänge sind nur zulässig, wenn sich der Player in einem bestimmten Status befindet. Beispielsweise ist ein Aufruf `play` in `IDLE` diesem Fall nicht zulässig. Sie können diesen Status erst aufrufen, nachdem der Player den `PREPARED` Status erreicht hat.

So arbeiten Sie mit Staaten:

* Sie können den aktuellen Status des `MediaPlayer` Objekts abrufen mit `MediaPlayer.getStatus`.

   ```java
   PlayerState getStatus() throws IllegalStateException;
   ```

* Die Liste der Statusangaben wird in definiert `MediaPlayer.PlayerState`.

Statusdiagramm für die Transition des Lebenszyklus einer `MediaPlayer` Instanz:
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

Die folgende Tabelle enthält weitere Details:

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> MediaPlayer.PlayerState </th> 
   <th colname="col2" class="entry"> Tritt auf, wenn </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> IDLE </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat einen neuen Medienplayer angefordert, indem Sie <span class="codeph"> DefaultMediaPlayer.create aufrufen </span>. Der neu erstellte Player wartet darauf, dass Sie ein Medienplayer-Element angeben. Dies ist der Ausgangszustand des Medienplayers. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISIERUNG </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung mit dem Namen <span class="codeph"> MediaPlayer.replaceCurrentItem </span>, und der Medienplayer wird geladen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISIERT </span> </td> 
   <td colname="col2"> <p>TVSDK hat das Medienplayer-Element erfolgreich festgelegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> VORBEREITUNG </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung mit dem Namen <span class="codeph"> MediaPlayer.prepareToPlay </span>. Der Medienplayer lädt das Medienplayer-Element und die zugehörigen Ressourcen. </p> <p>Tipp:  Es kann vorkommen, dass die Hauptmedien gepuffert werden. </p> <p>TVSDK bereitet den Medienstream vor und versucht, die Anzeigenauflösung und das Einfügen von Anzeigen durchzuführen (sofern aktiviert). </p> <p>Tipp:  Um die Beginn-Zeit auf einen Nicht-Nullwert festzulegen, rufen Sie <span class="codeph"> prepareToPlay(startTime) </span> mit der Uhrzeit in Millisekunden auf. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> VORBEREITT </span> </td> 
   <td colname="col2"> <p>Der Inhalt wird vorbereitet und Anzeigen wurden in die Zeitleiste eingefügt, oder der Anzeigenvorgang ist fehlgeschlagen. Die Pufferung oder Wiedergabe kann beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> ABSPIELEN </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat play genannt <span class="codeph"> </span>, sodass TVSDK versucht, das Video abzuspielen. Es kann zu Pufferung kommen, bevor das Video tatsächlich wiedergegeben wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> ANGEHALTEN </span> </td> 
   <td colname="col2"> <p>Während Ihre Anwendung die Medien wiedergibt und anhält, wechselt der Medienplayer zwischen diesem Status und PLAYING. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AUSGESETZT </span> </td> 
   <td colname="col2"> <p>Die Anwendung navigierte weg von der Wiedergabe, schloss das Gerät ab oder schaltete Anwendungen ein, während der Player abgespielt oder angehalten wurde. Der Medienplayer wurde ausgesetzt und Ressourcen wurden freigegeben. Um fortzufahren, stellen Sie den Medienplayer wieder her. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> VOLLSTÄNDIG </span> </td> 
   <td colname="col2"> <p>Der Player erreichte das Ende des Streams und die Wiedergabe wurde gestoppt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> VERÖFFENTLICHT </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat den Medienplayer veröffentlicht, der auch alle zugehörigen Ressourcen freigibt. Sie können diese Instanz nicht mehr verwenden </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> FEHLER </span> </td> 
   <td colname="col2"> <p>Während des Prozesses ist ein Fehler aufgetreten. Ein Fehler kann sich auch darauf auswirken, was Ihre Anwendung als Nächstes tun kann. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Sie können den Status verwenden, um Feedback zum Prozess bereitzustellen (z. B. ein Kreisel, während auf die nächste Statusänderung gewartet wird) oder um den nächsten Schritt beim Abspielen der Medien zu tun, z. B. auf den entsprechenden Status zu warten, bevor die nächste Methode aufgerufen wird.

Beispiel:

```java
@Override 
public void onStateChanged(MediaPlayer.PlayerState state,  
                           MediaPlayerNotification notification) { 
   switch (state) { 
      // It is recommended that you call prepareToPlay() after receiving  
      // the INITIALIZED state. 
      case INITIALIZED: 
         _mediaPlayer.prepareToPlay(); 
         break; 
      case PREPARING: 
         showBufferingSpinner(); 
         break; 
      case PREPARED: 
         hideBufferingSpinner(); 
      ..... 
    } 
}
```

