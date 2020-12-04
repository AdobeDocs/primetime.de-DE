---
description: Das PTMediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein PTMediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.
seo-description: Das PTMediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein PTMediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.
seo-title: Arbeiten mit MediaPlayer-Objekten
title: Arbeiten mit MediaPlayer-Objekten
uuid: eba26ad7-8c9a-4703-af32-1dfb928f6b67
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---


# Arbeiten mit MediaPlayer-Objekten{#work-with-mediaplayer-objects}

Das PTMediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein PTMediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.

## Info zur MediaPlayerItem-Klasse {#section_B6F36C0462644F5C932C8AA2F6827071}

Nachdem eine Medienressource erfolgreich geladen wurde, erstellt TVSDK eine Instanz der Klasse `PTMediaPlayerItem`, um Zugriff auf diese Ressource zu gewähren.

Das `PTMediaPlayer` löst die Medienressource, lädt die zugehörige Manifestdatei und analysiert das Manifest. Dies ist der asynchrone Teil des Ressourcenladevorgangs. Die `PTMediaPlayerItem`-Instanz wird erzeugt, nachdem die Ressource aufgelöst wurde. Diese Instanz ist eine aufgelöste Version einer Medienressource. TVSDK bietet Zugriff auf die neu erstellte `PTMediaPlayerItem`-Instanz über `PTMediaPlayer.currentItem`.

>[!TIP]
>
>Sie müssen warten, bis die Ressource erfolgreich geladen wurde, bevor Sie auf das Medienplayer-Element zugreifen können.

## MediaPlayer-Objektlebenszyklus {#section_D87EF7FBC7B442BDBE825156DC2C1CCF}

Ab dem Zeitpunkt, zu dem Sie die `PTMediaPlayer`-Instanz erstellen, bis zu dem Zeitpunkt, zu dem Sie sie beenden (wiederverwenden oder entfernen), schließt diese Instanz eine Reihe von Transitionen von einem Status zum anderen ab.

Einige Vorgänge sind nur zulässig, wenn sich der Player in einem bestimmten Status befindet. Beispielsweise ist das Aufrufen von `play` in `PTMediaPlayerStatusCreated` nicht zulässig. Sie können diesen Status erst aufrufen, nachdem der Player den Status `PTMediaPlayerStatusReady` erreicht hat.

So arbeiten Sie mit Status:

* Sie können den aktuellen Status des MediaPlayer-Objekts mit `PTMediaPlayer.status` abrufen.
* Die Liste der Status ist in `PTMediaPlayerStatus` definiert.

Statusdiagramm für die Transition des Lebenszyklus einer MediaPlayer-Instanz:
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-ios2_web.png)

Die folgende Tabelle enthält weitere Details:

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> PTMediaPlayerStatus </th> 
   <th colname="col2" class="entry"> Tritt auf, wenn </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCreated</span> </p> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat einen neuen Medienplayer angefordert, indem Sie <span class="codeph"> playerWithMediaPlayerItem</span> aufrufen. Der neu erstellte Player wartet darauf, dass Sie ein Medienplayer-Element angeben. Dies ist der ursprüngliche Status des Medienplayers. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing</span> </p> </td> 
   <td colname="col2"> <p>Ihre Anwendung ruft <span class="codeph"> PTMediaPlayer.replaceCurrentItemWithPlayerItem</span> auf und der Medienplayer lädt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusInitialized</span> </p> </td> 
   <td colname="col2"> <p>TVSDK hat das Medienplayer-Element erfolgreich festgelegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusReady</span> </p> </td> 
   <td colname="col2"> <p>Der Inhalt wird vorbereitet und Anzeigen wurden in die Zeitleiste eingefügt, oder der Anzeigenvorgang ist fehlgeschlagen. Die Pufferung oder Wiedergabe kann beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPlaying</span> </p> </td> 
   <td colname="col2"> <p>Ihre Anwendung hat "<span class="codeph"> play</span>"genannt, sodass TVSDK versucht, das Video abzuspielen. Es kann zu Pufferung kommen, bevor das Video tatsächlich wiedergegeben wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPaused</span> </p> </td> 
   <td colname="col2"> <p>Während Ihre Anwendung das Medium wiedergibt und anhält, wechselt der Medienplayer zwischen diesem Status und <span class="codeph"> PTMediaPlayerStatusPlaying</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCompleted</span> </p> </td> 
   <td colname="col2"> <p>Der Player erreichte das Ende des Streams und die Wiedergabe wurde gestoppt. </p> </td> 
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
>Sie können den Status verwenden, um Feedback zum Prozess bereitzustellen (z. B. ein Kreisel, während auf die nächste Statusänderung gewartet wird) oder um den nächsten Schritt beim Abspielen der Medien zu tun, z. B. auf den entsprechenden Status zu warten, bevor die nächste Methode aufgerufen wird.

