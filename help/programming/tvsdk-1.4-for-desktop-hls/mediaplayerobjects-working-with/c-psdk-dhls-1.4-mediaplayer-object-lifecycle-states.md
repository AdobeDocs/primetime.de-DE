---
description: Ab dem Zeitpunkt, zu dem Sie die MediaPlayer-Instanz erstellen, bis zum Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Übergängen zwischen Status ab.
title: MediaPlayer-Objektlebenszyklus
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MediaPlayer-Objektlebenszyklus{#mediaplayer-object-lifecycle}

Ab dem Zeitpunkt, zu dem Sie die MediaPlayer-Instanz erstellen, bis zum Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Übergängen zwischen Status ab.

Einige Vorgänge sind nur zulässig, wenn sich der Player in einem bestimmten Status befindet. Beispielsweise wird `play` in IDLE ist nicht zulässig. Sie können diesen Status erst aufrufen, nachdem der Player den Status VORBEREITET erreicht hat.

So arbeiten Sie mit Status:

* Sie können den aktuellen Status des `MediaPlayer` -Objekt mithilfe der `MediaPlayer.status` -Eigenschaft.

  ```
  function get status():String;
  ```

* Die Liste der Status wird im Abschnitt `MediaPlayer.PlayerStatus`.

Zustandsübergangsdiagramm für den Lebenszyklus eines `MediaPlayer` instance:
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
   <td colname="col2"> <p> Ihre Anwendung forderte durch Instanziierung einen neuen Medienplayer an <span class="codeph"> MediaPlayer </span>. Der neu erstellte Player wartet darauf, dass Sie ein Medienplayer-Element angeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISIERUNG </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung <span class="codeph"> MediaPlayer.replaceCurrentResource </span>und der Medienplayer geladen wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISIERT </span> </td> 
   <td colname="col2"> <p>TVSDK hat das Medienplayer-Element erfolgreich festgelegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> VORBEREITUNG </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung <span class="codeph"> MediaPlayer.prepareToPlay </span>. Der Medienplayer lädt das Medienplayer-Element und die zugehörigen Ressourcen. </p> <p>Tipp: Es kann zu Pufferung der Hauptmedien kommen. </p> <p>TVSDK bereitet den Medien-Stream vor und versucht, die Anzeigenauflösung und das Einfügen von Anzeigen durchzuführen (sofern aktiviert). </p> <p>Tipp: Rufen Sie auf, um die Startzeit auf einen Wert ungleich null festzulegen. <span class="codeph"> prepareToPlay(startTime) </span> mit der Zeit in Millisekunden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> VORBEREITET </span> </td> 
   <td colname="col2"> <p>Der Inhalt wird vorbereitet und Anzeigen wurden in die Timeline eingefügt, oder die Anzeigenverarbeitung ist fehlgeschlagen. Die Pufferung oder Wiedergabe kann beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PLAYING </span> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat <span class="codeph"> play </span>, sodass TVSDK versucht, das Video wiederzugeben. Es kann zu Pufferung kommen, bevor das Video tatsächlich wiedergegeben wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PAUSED </span> </td> 
   <td colname="col2"> <p>Wenn Ihre Anwendung die Medien wiedergibt und anhält, wechselt der Medienplayer zwischen diesem Status und der WIEDERGABE. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> SUCHEN </span> </td> 
   <td colname="col2"> <p>Der Medienplayer sucht nach der richtigen Position, während er angehalten oder wiedergegeben wird. Um festzustellen, wann die Suche gestartet oder beendet wurde, suchen Sie nach dem <span class="codeph"> SeekEvent.SEEK_BEGIN </span> und <span class="codeph"> SeekEvent.SEEK_END </span> -Ereignisse. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> ABGESCHLOSSEN </span> </td> 
   <td colname="col2"> <p>Der Player hat das Ende des Streams erreicht und die Wiedergabe angehalten. </p> </td> 
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
>Sie können den Status verwenden, um Feedback zum Prozess zu geben (z. B. ein Spinner beim Warten auf die nächste Statusänderung) oder den nächsten Schritt beim Abspielen der Medien zu unternehmen, z. B. auf den entsprechenden Status zu warten, bevor Sie die nächste Methode aufrufen.
