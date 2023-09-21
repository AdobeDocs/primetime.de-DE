---
description: TVSDK sendet Wiedergabeereignisse, wenn Vorgänge der Medienwiedergabe stattfinden, z. B. Videostarts.
title: Wiedergabeereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Wiedergabeereignisse{#playback-events}

TVSDK sendet Wiedergabeereignisse, wenn Vorgänge der Medienwiedergabe stattfinden, z. B. Videostarts.

Um über alle wiederkehrenden Ereignisse benachrichtigt zu werden, registrieren Sie eine Implementierung von `MediaPlayer.PlaybackEventListener`, einschließlich der folgenden Ereignisrückrufe.

<table frame="all" colsep="1" rowsep="1"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Ereignis </th> 
   <th colname="2" class="entry"> Bedeutung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Wiedergabe</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPlayComplete%28%29" format="html" scope="external"> onPlayComplete</a> </td> 
   <td colname="2"> Das Ende einer Medienquelle wurde erreicht. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPlayStart%28%29" format="html" scope="external"> onPlayStart</a> </td> 
   <td colname="2"> Die Wiedergabe einer Medienquelle wurde gestartet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRateSelected%28float%29" format="html" scope="external"> onRateSelected</a> (Fließgeschwindigkeit) </td> 
   <td colname="2"> Der Benutzer oder TVSDK hat eine neue Wiedergaberate ausgewählt, z. B. "Schnell vorwärts", "Zurückspulen"oder "Fortsetzen"mit einer normalen Geschwindigkeit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRatePlaying%28float%29" format="html" scope="external"> onRatePlaying</a> (Fließgeschwindigkeit) </td> 
   <td colname="2"> Auf dem Bildschirm wird eine neue Wiedergaberate angezeigt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Medien</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPrepared%28%29" format="html" scope="external"> onPrepared</a> </td> 
   <td colname="2"> Der Medienplayer hat die Medien erfolgreich vorbereitet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onSizeAvailable%28long,%20long%29" format="html" scope="external"> onSizeAvailable</a> (lange Höhe, lange Breite) </td> 
   <td colname="2"> Die Größe des Mediums ist verfügbar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Medienplayer</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onStateChanged%28com.adobe.mediacore.MediaPlayer.PlayerState,com.adobe.mediacore.MediaPlayerNotification%29" format="html" scope="external"> onStateChanged</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlayerState.html" format="html" scope="external"> MediaPlayer.PlayerState</a> state, <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html" format="html" scope="external"> MediaPlayerNotification</a> notification) </td> 
   <td colname="2"> Der Status des Medienplayers hat sich geändert. Ihre Anwendung sollte Fehler in diesem Rückruf verarbeiten. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onProfileChanged%28long,%20long%29" format="html" scope="external"> onProfileChanged</a> (langes Profil, lange Zeit) </td> 
   <td colname="2"> Das aktuelle Profil des Medienplayers wurde geändert. Verwenden Sie die <span class="codeph"> Profil</span> -Eigenschaft, um das neue Profil zu erhalten, das abgespielt wird. Verwenden Sie die <span class="codeph"> time</span> -Eigenschaft, um die Zeit abzurufen, zu der dieses Ereignis aufgetreten ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>MediaPlayerItem</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onUpdated%28%29" format="html" scope="external"> onUpdated</a> </td> 
   <td colname="2">Der Medienplayer hat das Medium in einem der folgenden Fälle erfolgreich aktualisiert: 
    <ul> 
     <li>Wenn eine Manifestaktualisierung für ein Live-Asset erfolgt.</li> 
     <li>Wenn ein VOD- oder Live-Asset eine verdeckte Untertitelung aufweist und die Aktivität zuerst für einen verdeckten Untertitelpfad erkannt wird. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Manifest und Timeline</b></td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimedMetadata%28com.adobe.mediacore.metadata.TimedMetadata%29" format="html" scope="external"> onTimedMetadata</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html" format="html" scope="external"> TimedMetadata</a> timedMetadata) </td> 
   <td colname="2"> Im Manifest werden neue zeitgesteuerte Metadaten gefunden. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated%28%29" format="html" scope="external"> onTimelineUpdated</a> </td> 
   <td colname="2">Der Medienplayer hat Anzeigen hinzugefügt oder entfernt, sodass er über eine aktualisierte Timeline verfügt. <p>Das für ein Live-Asset aktualisierte Manifest und alte Werbeunterbrechungen wurden aus der Timeline entfernt oder neue Anzeigenchancen (Cue-Point) wurden entdeckt. Der Medienplayer versucht, alle neuen Anzeigen aufzulösen und auf der Timeline zu platzieren. </p><p> Verwenden Sie dieses Ereignis, um zu überprüfen, ob die Timeline aktualisiert wurde (VOD ändert sich während der Wiedergabe nicht). Sie können dann die Timeline mit <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html#getTimeline%28%29" format="html" scope="external"> MediaPlayer.getTimeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>
