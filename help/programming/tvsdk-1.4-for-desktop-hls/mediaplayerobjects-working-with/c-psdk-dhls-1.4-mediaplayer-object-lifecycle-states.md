---
description: Ab dem Zeitpunkt, zu dem Sie die MediaPlayer-Instanz erstellen, bis zu dem Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Transitionen zwischen Status ab.
seo-description: Ab dem Zeitpunkt, zu dem Sie die MediaPlayer-Instanz erstellen, bis zu dem Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Transitionen zwischen Status ab.
seo-title: MediaPlayer-Objektlebenszyklus
title: MediaPlayer-Objektlebenszyklus
uuid: 1452ae3a-7ce9-439e-951c-9d3db63b1d20
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# MediaPlayer-Objektlebenszyklus{#mediaplayer-object-lifecycle}

Ab dem Zeitpunkt, zu dem Sie die MediaPlayer-Instanz erstellen, bis zu dem Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Transitionen zwischen Status ab.

Einige Vorgänge sind nur zulässig, wenn sich der Player in einem bestimmten Status befindet. Beispielsweise ist ein Aufruf `play` in IDLE nicht zulässig. Sie können diesen Status erst aufrufen, nachdem der Player den Status &quot;VORBEREITT&quot;erreicht hat.

So arbeiten Sie mit Status:

* Sie können den aktuellen Status des `MediaPlayer` Objekts mithilfe der `MediaPlayer.status` Eigenschaft abrufen.

   ```
   function get status():String;
   ```

* Die Liste der Status wird in `MediaPlayer.PlayerStatus`definiert.

Statusdiagramm für die Transition des Lebenszyklus einer `MediaPlayer` Instanz:
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-flash-1_2_web.png)

Die folgende Tabelle enthält weitere Details:

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <span class="codeph"> MediaPlayerStatus </span> </th> 
   <th colname="col2" class="entry"> Tritt auf, wenn </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> IDLE </span> </td> 
   <td colname="col2"> <p> Ihre Anwendung hat einen neuen Medienplayer durch Instanziierung von <span class="codeph"> MediaPlayer angefordert </span>. Der neu erstellte Player wartet darauf, dass Sie ein Medienplayer-Element angeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISIERUNG </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung mit dem Namen <span class="codeph"> MediaPlayer.replaceCurrentResource </span>, und der Medienplayer wird geladen. </p> </td> 
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
   <td colname="col1"> <span class="codeph"> SUCHEN </span> </td> 
   <td colname="col2"> <p>Der Medienplayer sucht bei der Pause oder beim Abspielen nach der richtigen Position. Um festzustellen, wann die Suche gestartet oder beendet wurde, suchen Sie nach den <span class="codeph"> Ereignissen SeekEvent.SEEK_BEGIN </span> und <span class="codeph"> SeekEvent.SEEK_END </span> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> ABGESCHLOSSEN </span> </td> 
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

