---
description: Das PTMediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein PTMediaPlayerItem stellt Audio oder Video auf Ihrem Player dar.
title: Arbeiten mit MediaPlayer-Objekten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Arbeiten mit MediaPlayer-Objekten {#work-with-mediaplayer-objects}

Das PTMediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein PTMediaPlayerItem stellt Audio oder Video auf Ihrem Player dar.

## Über die MediaPlayerItem-Klasse {#section_B6F36C0462644F5C932C8AA2F6827071}

Nachdem eine Medienressource erfolgreich geladen wurde, erstellt TVSDK eine Instanz der `PTMediaPlayerItem` -Klasse, um Zugriff auf diese Ressource zu gewähren.

Die `PTMediaPlayer` löst die Medienressource auf, lädt die zugehörige Manifestdatei und analysiert das Manifest. Dies ist der asynchrone Teil des Ressourcenladevorgangs. Die `PTMediaPlayerItem` -Instanz wird erzeugt, nachdem die Ressource aufgelöst wurde. Diese Instanz ist eine aufgelöste Version einer Medienressource. TVSDK bietet Zugriff auf die neu erstellten `PTMediaPlayerItem` Instanz über `PTMediaPlayer.currentItem`.

>[!TIP]
>
>Sie müssen warten, bis die Ressource erfolgreich geladen wurde, bevor Sie auf das Medienplayer-Element zugreifen.

## MediaPlayer-Objektlebenszyklus {#section_D87EF7FBC7B442BDBE825156DC2C1CCF}

Ab dem Zeitpunkt der Erstellung des `PTMediaPlayer` -Instanz zu dem Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), führt diese Instanz eine Reihe von Transitionen von einem Status zum anderen durch.

Einige Vorgänge sind nur zulässig, wenn sich der Player in einem bestimmten Status befindet. Beispielsweise wird `play` in `PTMediaPlayerStatusCreated` ist nicht zulässig. Sie können diesen Status erst aufrufen, wenn der Player die `PTMediaPlayerStatusReady` -Status.

So arbeiten Sie mit Status:

* Sie können den aktuellen Status des MediaPlayer-Objekts abrufen mit `PTMediaPlayer.status`.
* Die Liste der Status wird im Abschnitt `PTMediaPlayerStatus`.

Zustandsübergangsdiagramm für den Lebenszyklus einer MediaPlayer-Instanz:
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-ios2_web.png)

Die folgende Tabelle enthält weitere Details:

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>PTMediaPlayerStatus</b></th> 
   <th colname="col2" class="entry"><b>Tritt auf, wenn</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCreated</span> </p> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat einen neuen Medienplayer angefordert, indem Sie <span class="codeph"> playerWithMediaPlayerItem</span>. Der neu erstellte Player wartet darauf, dass Sie ein Medienplayer-Element angeben. Dies ist der Anfangsstatus des Medienplayers. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing</span> </p> </td> 
   <td colname="col2"> <p>Ihre App-Aufrufe <span class="codeph"> PTMediaPlayer.replaceCurrentItemWithPlayerItem</span>und der Medienplayer geladen wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusInitialized</span> </p> </td> 
   <td colname="col2"> <p>TVSDK hat das Medienplayer-Element erfolgreich festgelegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusReady</span> </p> </td> 
   <td colname="col2"> <p>Der Inhalt wird vorbereitet und Anzeigen wurden in die Timeline eingefügt, oder die Anzeigenverarbeitung ist fehlgeschlagen. Die Pufferung oder Wiedergabe kann beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPlaying</span> </p> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat <span class="codeph"> play</span>, sodass TVSDK versucht, das Video wiederzugeben. Es kann zu Pufferung kommen, bevor das Video tatsächlich wiedergegeben wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPaused</span> </p> </td> 
   <td colname="col2"> <p>Wenn Ihre Anwendung die Medien wiedergibt und anhält, wechselt der Medienplayer zwischen diesem Status und <span class="codeph"> PTMediaPlayerStatusPlaying</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCompleted</span> </p> </td> 
   <td colname="col2"> <p>Der Player hat das Ende des Streams erreicht und die Wiedergabe angehalten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusStopped</span> </p> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat den Medienplayer veröffentlicht, der auch alle zugehörigen Ressourcen freigibt. Sie können diese Instanz nicht mehr verwenden </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusError</span> </p> </td> 
   <td colname="col2"> <p>Während des Prozesses ist ein Fehler aufgetreten. Ein Fehler kann sich auch darauf auswirken, was Ihre Anwendung als Nächstes tun kann. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Sie können den Status verwenden, um Feedback zum Prozess zu geben (z. B. ein Spinner beim Warten auf die nächste Statusänderung) oder den nächsten Schritt beim Abspielen der Medien zu unternehmen, z. B. auf den entsprechenden Status zu warten, bevor Sie die nächste Methode aufrufen.
