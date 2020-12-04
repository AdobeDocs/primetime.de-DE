---
description: TVSDK löst Ereignisse zur Wiedergabe aus, wenn Vorgänge zur Medienwiedergabe ausgeführt werden, z. B. wenn die Videowiedergabe beginnt.
seo-description: TVSDK löst Ereignisse zur Wiedergabe aus, wenn Vorgänge zur Medienwiedergabe ausgeführt werden, z. B. wenn die Videowiedergabe beginnt.
seo-title: Wiedergabe-Ereignisse
title: Wiedergabe-Ereignisse
uuid: 809a8e0e-f4d8-4013-b04a-49fb93d7ca8a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Wiedergabe-Ereignis{#playback-events}

TVSDK löst Ereignisse zur Wiedergabe aus, wenn Vorgänge zur Medienwiedergabe ausgeführt werden, z. B. wenn die Videowiedergabe beginnt.

Um über alle abspielrelevanten Ereignis benachrichtigt zu werden, registrieren Sie eine Implementierung von `MediaPlayer.PlaybackEventListener`, einschließlich der folgenden Ereignis-Rückrufe.

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
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRateSelected%28float%29" format="html" scope="external"> onRateSelected</a> (float rate) </td> 
   <td colname="2"> Der Benutzer oder TVSDK hat eine neue Wiedergabegeschwindigkeit gewählt, z. B. "Schnell vorwärts", "Zurückspulen"oder "Wiederaufnehmen mit normaler Geschwindigkeit". </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRatePlaying%28float%29" format="html" scope="external"> onRatePlaying</a> (float rate) </td> 
   <td colname="2"> Eine neue Wiedergabegeschwindigkeit ist auf dem Bildschirm sichtbar. </td> 
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
   <td colname="col1"><b>Media Player</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onStateChanged%28com.adobe.mediacore.MediaPlayer.PlayerState,com.adobe.mediacore.MediaPlayerNotification%29" format="html" scope="external"> onStateChanged</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlayerState.html" format="html" scope="external"> MediaPlayer.</a> PlayerStatproperty,  <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html" format="html" scope="external"> </a> MediaPlayerNotificationNotification) </td> 
   <td colname="2"> Der Status des Medienplayers hat sich geändert. Ihre Anwendung sollte Fehler in diesem Rückruf verarbeiten. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onProfileChanged%28long,%20long%29" format="html" scope="external"> onProfileChanged</a> (langes Profil, lange Zeit) </td> 
   <td colname="2"> Das aktuelle Profil des Medienplayers hat sich geändert. Verwenden Sie die Eigenschaft <span class="codeph"> Profil</span>, um das neue Profil abzurufen, das abgespielt wird. Verwenden Sie die Eigenschaft <span class="codeph"> time</span>, um den Zeitpunkt abzurufen, zu dem dieses Ereignis aufgetreten ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>MediaPlayerItem</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onUpdated%28%29" format="html" scope="external"> onUpdated</a> </td> 
   <td colname="2">Der Medienplayer hat die Medien in einem der folgenden Fälle erfolgreich aktualisiert: 
    <ul> 
     <li>Wenn ein Manifest für ein Live-Asset aktualisiert wird.</li> 
     <li>Wenn ein VOD- oder Live-Asset Untertitel und Aktivität zum ersten Mal für eine Untertitel-Spur entdeckt wird. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Manifest und Zeitschiene</b></td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimedMetadata%28com.adobe.mediacore.metadata.TimedMetadata%29" format="html" scope="external"> onTimedMetadata</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html" format="html" scope="external"> </a> TimedMetadatimedMetadata) </td> 
   <td colname="2"> Im Manifest werden neue zeitgesteuerte Metadaten gefunden. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated%28%29" format="html" scope="external"> onTimelineUpdated</a> </td> 
   <td colname="2">Der Medienplayer hat Anzeigen hinzugefügt oder entfernt, sodass er über eine aktualisierte Zeitschiene verfügt. <p>Das für ein Live-Asset aktualisierte Manifest und alte Werbeunterbrechungen wurden aus der Zeitleiste entfernt oder neue Werbemöglichkeiten (Cue-Points) wurden entdeckt. Der Medienplayer versucht, alle neuen Anzeigen aufzulösen und auf der Zeitleiste zu platzieren. </p><p> Verwenden Sie dieses Ereignis, um zu überprüfen, ob die Zeitleiste Updates enthält (VOD ändert sich während der Wiedergabe nicht). Sie können die Zeitschiene dann mit <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html#getTimeline%28%29" format="html" scope="external"> MediaPlayer.getTimeline</a> abrufen. </p> </td> 
  </tr> 
 </tbody> 
</table>
