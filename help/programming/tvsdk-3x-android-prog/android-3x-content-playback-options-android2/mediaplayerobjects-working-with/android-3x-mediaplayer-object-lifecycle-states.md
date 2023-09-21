---
description: Der Status des Medienplayers bestimmt, welche Aktionen zulässig sind.
title: Lebenszyklus und Status des MediaPlayer-Objekts
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Lebenszyklus und Status des MediaPlayer-Objekts{#lifecycle-and-statuses-of-the-mediaplayer-object}

Der Status des Medienplayers bestimmt, welche Aktionen zulässig sind.

Für die Arbeit mit Medienplayer-Status:

* Sie können den aktuellen Status der `MediaPlayer` Objekt mit `MediaPlayer.getStatus()`.

* Die Liste der Status wird im Abschnitt [MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/com/adobe/mediacore/MediaPlayerStatus.html) enum.

Status-Transition-Diagramm für den Lebenszyklus eines `MediaPlayer` instance:

<!--<a id="fig_A6425F24C7734DC681D992859D2A6743"></a>-->

![](assets/media_player_statuses.png)

Die folgende Tabelle enthält Details zum Lebenszyklus und den Status des Medienplayers:

<table id="table_82757A0043EB4AACA474E6B30326A6B7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status </th> 
   <th colname="col2" class="entry"> Tritt auf, wenn </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> IDLE </td> 
   <td colname="col2"> <p>Der Anfangsstatus des Medienplayers. Der Player wird erstellt und wartet darauf, dass Sie ein Medienplayer-Element angeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISIERUNG </td> 
   <td colname="col2"> <p>Ihre App-Aufrufe <span class="codeph"> MediaPlayer.replaceCurrentItem() </span>. </p> <p>Das Medienplayer-Element wird geladen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISIERT </td> 
   <td colname="col2"> <p>TVSDK hat das Medienplayer-Element erfolgreich festgelegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VORBEREITUNG </td> 
   <td colname="col2"> <p>Ihre App-Aufrufe <span class="codeph"> MediaPlayer.prepareToPlay() </span>. Der Medienplayer lädt das Medienplayer-Element und alle zugehörigen Ressourcen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VORBEREITET </td> 
   <td colname="col2"> <p>TVSDK hat den Medien-Stream vorbereitet und versucht, die Anzeigenauflösung und das Einfügen von Anzeigen durchzuführen (sofern aktiviert). Der Inhalt wird vorbereitet und Anzeigen wurden in die Timeline eingefügt, oder die Anzeigenverarbeitung ist fehlgeschlagen. </p> <p>Die Pufferung oder Wiedergabe kann beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> WIEDERGABE/ANGEHALTEN </td> 
   <td colname="col2"> <p>Während die Anwendung die Medien wiedergibt und aussetzt, wechselt der Medienplayer zwischen diesen Status. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AUSGESETZT </td> 
   <td colname="col2"> <p>Wenn die Anwendung von der Wiedergabe weg navigiert, das Gerät herunterfährt oder Anwendungen wechselt, während der Player wiedergegeben oder angehalten wird, wird der Medienplayer ausgesetzt und die Ressourcen werden freigegeben. </p> <p>Aufruf <span class="codeph"> MediaPlayer.restore() </span> gibt den Player in den Status zurück, in dem sich der Player befand, bevor er AUSGESETZT wurde. Die Ausnahme besteht darin, dass der Player beim Aufrufen der Unterbrechung SUCHT, der Player angehalten und anschließend AUSGESETZT wird. </p> <p>Wichtig:  <p>Beachten Sie die folgenden Informationen: 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C">Die <span class="codeph"> MediaPlayer </span> automatische Aufrufe <span class="codeph"> aussetzen </span> nur, wenn das von der <span class="codeph"> MediaPlayerView </span> zerstört wird. </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1">Die <span class="codeph"> MediaPlayer </span> automatische Aufrufe <span class="codeph"> restore() </span> nur bei einem neuen Oberflächenobjekt, das von der <span class="codeph"> MediaPlayerView </span> erstellt wird. </li> 
      </ul> </p> </p> <p>Wenn die Wiedergabe bei der Wiederherstellung des MediaPlayer immer angehalten werden soll, rufen Sie Ihre Anwendung auf <span class="codeph"> MediaPlayer.pause() </span> in der Android-Aktivität <span class="codeph"> onPause() </span> -Methode. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> COMPLETE </td> 
   <td colname="col2"> <p>Der Player hat das Ende des Streams erreicht und die Wiedergabe wurde angehalten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VERÖFFENTLICHT </td> 
   <td colname="col2"> <p>Ihre Anwendung hat den Medienplayer veröffentlicht, in dem auch alle zugehörigen Ressourcen veröffentlicht werden. Sie können diese Instanz nicht mehr verwenden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> FEHLER </td> 
   <td colname="col2"> <p>Während des Prozesses ist ein Fehler aufgetreten. Ein Fehler kann sich auch darauf auswirken, was die Anwendung als Nächstes tun kann. Weitere Informationen finden Sie unter <a href="../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-error-handling-set-up.md" format="dita" scope="local"> Einrichten der Fehlerbehandlung </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Sie können den Status verwenden, um Feedback zum Prozess bereitzustellen, z. B. ein Spinner beim Warten auf die nächste Statusänderung oder die nächsten Schritte beim Abspielen der Medien, z. B. warten auf den entsprechenden Status, bevor Sie die nächste Methode aufrufen.

Beispiel:

```java
mediaPlayer.addEventListener(MediaPlayerEvent STATUS_CHANGED, new StatusChangeEventListener() { 
    @Override  
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        switch(event.getStatus()) { 
            case INITIALIZED: 
                mediaPlayer.prepareToPlay(); 
                break; 
            case PREPARING: 
                showBufferingSpinner(); 
                break; 
            case PREPARED: 
                hideBufferingSpinner(); 
                mediaPlayer.play(); 
                break; 
            ...                
        } 
        ... 
    } 
}); 
```
