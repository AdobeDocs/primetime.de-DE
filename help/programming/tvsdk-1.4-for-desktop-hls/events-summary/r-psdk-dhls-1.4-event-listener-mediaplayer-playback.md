---
description: Ihre Anwendung kann die Aktivität im Player und den sich ändernden Status des Players überwachen, indem sie auf von TVSDK ausgelöste Ereignis überwacht.
title: Wiedergabe-Ereignisse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# Wiedergabe-Ereignis {#playback-events}

Ihre Anwendung kann die Aktivität im Player und den sich ändernden Status des Players überwachen, indem sie auf von TVSDK ausgelöste Ereignis überwacht.

TVSDK löst Ereignisse zur Wiedergabe aus, wenn Vorgänge zur Medienwiedergabe ausgeführt werden, z. B. wenn die Videowiedergabe beginnt. Um über alle abspielrelevanten Ereignis benachrichtigt zu werden, registrieren Sie Listener für die folgenden Ereignis beim `MediaPlayer`-Objekt.

<table frame="all" colsep="1" rowsep="1" id="table_922EEA3DE0BD47BA982E11F890CA0A6B"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Ereignis </th> 
   <th colname="2" class="entry"> Bedeutung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Wiedergabe</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_SELECTED" format="html" scope="external"> RATE_SELECTED</a> </td> 
   <td colname="2"> Der Benutzer oder TVSDK hat eine neue Wiedergabegeschwindigkeit gewählt, z. B. "Schnell vorwärts", "Zurückspulen"oder "Wiederaufnehmen mit normaler Geschwindigkeit". </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_PLAYING" format="html" scope="external"> RATE_PLAYING</a> </td> 
   <td colname="2"> Eine neue Wiedergabegeschwindigkeit ist auf dem Bildschirm sichtbar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> TimeChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html#TIME_CHANGED" format="html" scope="external"> TIME_CHANGED</a> </td> 
   <td colname="2"> Die aktuelle Abspielposition des Mediums wurde geändert. Wird regelmäßig nach einer Änderung der aktuellen Zeit alle 250 ms oder mehr ausgelöst. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Media Player</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerStatus ChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html#STATUS_CHANGED" format="html" scope="external"> STATUS_CHANGED</a> </td> 
   <td colname="2"> Der Status des Medienplayers hat sich geändert. Ihre Anwendung sollte Fehler im Rückruf dieses Ereignisses behandeln. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">ProfileEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html#PROFILE_CHANGED" format="html" scope="external"> Profil_CHANGED</a> </td> 
   <td colname="2">Das aktuelle Profil des Medienplayers hat sich geändert. Verwenden Sie die Eigenschaft <span class="codeph"> ProfileEvent.Profil</span>, um das neue Profil abzurufen, das abgespielt wird. Verwenden Sie die Eigenschaft <span class="codeph"> time</span>, um den Zeitpunkt abzurufen, zu dem dieses Ereignis aufgetreten ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>MediaPlayerItem</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerItem-Ereignis.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_CREATED" format="html" scope="external"> ITEM_CREATED</a> </td> 
   <td colname="2">Ein <span class="codeph"> MediaPlayerItem</span> wurde erstellt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerItem-Ereignis.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_UPDATED" format="html" scope="external"> ITEM_UPDATED</a> </td> 
   <td colname="2">Der Medienplayer hat die Medien in einem der folgenden Fälle erfolgreich aktualisiert: 
    <ul id="ul_E4D1A1D468544C3B9F8046E9B68A956D"> 
     <li id="li_35A2A417BF924E039D9CB36CFBCDFEB6">Wenn ein Manifest für ein Live-Asset aktualisiert wird. </li> 
     <li id="li_E7AB380C212B4011B07C3B313282681C">Wenn ein VOD- oder Live-Asset Untertitel und Aktivität zum ersten Mal für eine Untertitel-Spur entdeckt wird. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Beschriftungen und Audio</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> MediaPlayerItem-Ereignis.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#CAPTION_UPDATED" format="html" scope="external"> CAPTION_UPDATED</a> </td> 
   <td colname="2">Im Medienstream wurde eine neue Untertitelspur erkannt und die Sammlung <span class="codeph"> closeCaptionsTracks</span> wurde aktualisiert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Manifest und Zeitschiene</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="0"> 
   <td colname="1">TimelineEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED" format="html" scope="external"> TIMELINE_UPDATED</a> </td> 
   <td colname="2">Der Medienplayer hat Anzeigen hinzugefügt oder entfernt, sodass er über eine aktualisierte Zeitschiene verfügt. <p>Das für ein Live-Asset aktualisierte Manifest und alte Werbeunterbrechungen wurden aus der Zeitleiste entfernt oder neue Werbemöglichkeiten (Cue-Points) wurden entdeckt. Der Medienplayer versucht, alle neuen Anzeigen aufzulösen und auf der Zeitleiste zu platzieren. </p> <p> Verwenden Sie dieses Ereignis, um zu überprüfen, ob die Zeitleiste Updates enthält (VOD ändert sich während der Wiedergabe nicht). Anschließend können Sie die Zeitleiste mit <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayer.html#timeline" format="html" scope="external"> MediaPlayer.timeline</a> abrufen. </p> </td> 
  </tr> 
 </tbody> 
</table>

