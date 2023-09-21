---
description: Ihre Anwendung kann die Aktivität in Ihrem Player und den sich ändernden Status des Players überwachen, indem sie auf Ereignisse wartet, die von TVSDK gesendet werden.
title: Wiedergabeereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# Wiedergabeereignisse {#playback-events}

Ihre Anwendung kann die Aktivität in Ihrem Player und den sich ändernden Status des Players überwachen, indem sie auf Ereignisse wartet, die von TVSDK gesendet werden.

TVSDK sendet Wiedergabeereignisse, wenn Vorgänge der Medienwiedergabe stattfinden, z. B. Videostarts. Um über alle wiedergabebezogenen Ereignisse benachrichtigt zu werden, registrieren Sie Listener bei der `MediaPlayer` -Objekt für die folgenden Ereignisse.

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
   <td colname="2"> Der Benutzer oder TVSDK hat eine neue Wiedergaberate ausgewählt, z. B. "Schnell vorwärts", "Zurückspulen"oder "Fortsetzen"mit einer normalen Geschwindigkeit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_PLAYING" format="html" scope="external"> RATE_PLAYING</a> </td> 
   <td colname="2"> Auf dem Bildschirm wird eine neue Wiedergaberate angezeigt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> TimeChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html#TIME_CHANGED" format="html" scope="external"> TIME_CHANGED</a> </td> 
   <td colname="2"> Die aktuelle Abspielposition des Mediums wurde geändert. Wird regelmäßig nach Änderung der aktuellen Zeit alle 250 ms oder mehr gesendet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Medienplayer</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerStatus ChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html#STATUS_CHANGED" format="html" scope="external"> STATUS_CHANGED</a> </td> 
   <td colname="2"> Der Status des Medienplayers hat sich geändert. Ihre Anwendung sollte Fehler im Callback dieses Ereignisses verarbeiten. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">ProfilEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html#PROFILE_CHANGED" format="html" scope="external"> PROFILE_CHANGED</a> </td> 
   <td colname="2">Das aktuelle Profil des Medienplayers wurde geändert. Verwenden Sie die <span class="codeph"> ProfileEvent.profile</span> -Eigenschaft, um das neue Profil zu erhalten, das abgespielt wird. Verwenden Sie die <span class="codeph"> time</span> -Eigenschaft, um die Zeit abzurufen, zu der dieses Ereignis aufgetreten ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>MediaPlayerItem</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerItem-Ereignis.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_CREATED" format="html" scope="external"> ITEM_CREATED</a> </td> 
   <td colname="2">A <span class="codeph"> MediaPlayerItem</span> wurde erstellt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerItem-Ereignis.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_UPDATED" format="html" scope="external"> ITEM_UPDATED</a> </td> 
   <td colname="2">Der Medienplayer hat das Medium in einem der folgenden Fälle erfolgreich aktualisiert: 
    <ul id="ul_E4D1A1D468544C3B9F8046E9B68A956D"> 
     <li id="li_35A2A417BF924E039D9CB36CFBCDFEB6">Wenn eine Manifestaktualisierung für ein Live-Asset erfolgt. </li> 
     <li id="li_E7AB380C212B4011B07C3B313282681C">Wenn ein VOD- oder Live-Asset eine verdeckte Untertitelung aufweist und die Aktivität zuerst für einen verdeckten Untertitelpfad erkannt wird. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Untertitel und Audio</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> MediaPlayerItem-Ereignis.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#CAPTION_UPDATED" format="html" scope="external"> CAPTION_UPDATED</a> </td> 
   <td colname="2">Im Medien-Stream wurde ein neuer Untertitelpfad erkannt und die <span class="codeph"> closedCaptionsTracks</span> Sammlung wurde aktualisiert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Manifest und Timeline</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="0"> 
   <td colname="1">TimelineEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED" format="html" scope="external"> TIMELINE_UPDATED</a> </td> 
   <td colname="2">Der Medienplayer hat Anzeigen hinzugefügt oder entfernt, sodass er über eine aktualisierte Timeline verfügt. <p>Das für ein Live-Asset aktualisierte Manifest und alte Werbeunterbrechungen wurden aus der Timeline entfernt oder neue Anzeigenchancen (Cue-Point) wurden entdeckt. Der Medienplayer versucht, alle neuen Anzeigen aufzulösen und auf der Timeline zu platzieren. </p> <p> Verwenden Sie dieses Ereignis, um zu überprüfen, ob die Timeline aktualisiert wurde (VOD ändert sich während der Wiedergabe nicht). Sie können dann die Timeline mit <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayer.html#timeline" format="html" scope="external"> MediaPlayer.timeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>
