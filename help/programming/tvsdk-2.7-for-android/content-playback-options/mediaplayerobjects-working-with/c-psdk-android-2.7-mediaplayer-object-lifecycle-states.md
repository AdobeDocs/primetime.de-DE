---
description: Der Status des Medienplayers bestimmt, welche Aktionen zulässig sind.
title: Lebenszyklus und Status des MediaPlayer-Objekts
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---


# Lebenszyklus und Status des MediaPlayer-Objekts {#lifecycle-and-statuses-of-the-mediaplayer-object}

Der Status des Medienplayers bestimmt, welche Aktionen zulässig sind.

Zum Arbeiten mit Medienplayer-Status:

* Sie können den aktuellen Status des `MediaPlayer`-Objekts mit `MediaPlayer.getStatus()` abrufen.

* Die Liste der Status wird in der Enum [MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/com/adobe/mediacore/MediaPlayerStatus.html) definiert.

Status-Transition-Diagramm für den Lebenszyklus einer `MediaPlayer` Instanz:
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
   <td colname="col2"> <p>Ihre Anwendung ruft <span class="codeph"> MediaPlayer.replaceCurrentItem() </span> auf. </p> <p>Das Medienplayer-Element wird geladen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISIERT </td> 
   <td colname="col2"> <p>TVSDK hat das Medienplayer-Element erfolgreich eingestellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VORBEREITUNG </td> 
   <td colname="col2"> <p>Ihre Anwendung ruft <span class="codeph"> MediaPlayer.prepareToPlay() </span> auf. Der Medienplayer lädt das Medienplayer-Element und alle zugehörigen Ressourcen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VORBEREITT </td> 
   <td colname="col2"> <p>TVSDK hat den Medienstream vorbereitet und versucht, die Auflösung von Anzeigen und das Einfügen von Anzeigen (sofern aktiviert) durchzuführen. Der Inhalt wird vorbereitet und Anzeigen wurden in die Zeitleiste eingefügt, oder der Anzeigenvorgang ist fehlgeschlagen. </p> <p>Die Pufferung oder Wiedergabe kann beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PLAYING/PAUSED </td> 
   <td colname="col2"> <p>Während die Anwendung das Medium abspielt und anhält, wechselt der Medienplayer zwischen diesen Status. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AUSGESETZT </td> 
   <td colname="col2"> <p>Wenn die Anwendung weg von der Wiedergabe navigiert, das Gerät herunterfährt oder Anwendungen wechselt, während der Player abgespielt oder angehalten wird, wird der Medienplayer ausgesetzt und Ressourcen werden freigegeben. </p> <p>Durch Aufruf von <span class="codeph"> MediaPlayer.restore() </span> wird der Player auf den Status zurückgesetzt, in dem sich der Player vor dem AUSSETZEN befand. Die Ausnahme ist, wenn der Spieler SUCHT, wenn suspendiert aufgerufen wird, der Spieler PAUSED und dann AUSGESETZT wird. </p> <p>Wichtig:  <p>Beachten Sie die folgenden Informationen: 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C">Der <span class="codeph"> MediaPlayer </span> ruft <span class="codeph"> die Aussetzung </span> nur dann automatisch auf, wenn das Oberflächenobjekt, das von <span class="codeph"> MediaPlayerView </span> verwendet wird, zerstört wird. </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1">Der <span class="codeph"> MediaPlayer </span> ruft <span class="codeph"> restore() </span> nur dann automatisch auf, wenn ein neues Oberflächenobjekt erstellt wird, das von <span class="codeph"> MediaPlayerView </span> verwendet wird. </li> 
      </ul> </p> </p> <p>Wenn die Wiedergabe bei der Wiederherstellung des MediaPlayer immer angehalten werden soll, verwenden Sie den Anwendungsaufruf <span class="codeph"> MediaPlayer.pause() </span> in der Methode <span class="codeph"> der Android-Aktivität </span>. onPause() . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VOLLSTÄNDIG </td> 
   <td colname="col2"> <p>Der Player hat das Ende des Streams erreicht und die Wiedergabe wurde gestoppt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VERÖFFENTLICHT </td> 
   <td colname="col2"> <p>Ihre Anwendung hat den Medienplayer veröffentlicht, der auch alle zugehörigen Ressourcen freigibt. Sie können diese Instanz nicht mehr verwenden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> FEHLER </td> 
   <td colname="col2"> <p>Während des Prozesses ist ein Fehler aufgetreten. Ein Fehler kann sich auch darauf auswirken, was die Anwendung als Nächstes tun kann. Weitere Informationen finden Sie unter <a href="../../../tvsdk-2.7-for-android/content-playback-options/t-psdk-android-2.7-error-handling-set-up.md#set-up-error-handling" format="dita" scope="local"> Einrichten der Fehlerbearbeitung </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Sie können den Status verwenden, um Feedback zum Prozess bereitzustellen, z. B. einen Spinner, während Sie auf die nächste Statusänderung warten, oder die nächsten Schritte beim Abspielen der Medien ausführen, z. B. auf den entsprechenden Status warten, bevor Sie die nächste Methode aufrufen.

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

