---
description: Die Version von EXT-X-VERSION in der .m3u8-Datei beeinflusst, welche Funktionen für Ihre Anwendung verfügbar sind und welche EXT-Tags in Ihrer Wiedergabeliste/Ihrem Manifest gültig sind.
title: EXT-X-VERSIONSANFORDERUNGEN
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# EXT-X-VERSIONSANFORDERUNGEN{#ext-x-version-requirements}

Die Version von `#EXT-X-VERSION` in der .m3u8-Datei beeinflusst, welche Funktionen für Ihre Anwendung verfügbar sind und welche EXT-Tags in Ihrer Wiedergabeliste/Ihrem Manifest gültig sind.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Im Folgenden finden Sie einige Informationen zum Tag `#EXT-X-VERSION` , das die HLS-Protokollversion angibt:

* Die Version muss mit den Funktionen und Attributen in der HLS-Wiedergabeliste übereinstimmen. Andernfalls kann es zu Wiedergabefehlern kommen. Weitere Informationen finden Sie unter [HTTP Live Streaming-Spezifikation](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Adobe empfiehlt die Verwendung von mindestens Version 2 für die Wiedergabe in Browser TVSDK-basierten Clients.

  Clients und Server müssen die Versionen wie folgt implementieren:

<table frame="all" colsep="1" rowsep="1" id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Mindestens diese Version verwenden </th> 
   <th colname="2" class="entry"> So verwenden Sie diese Funktionen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Gleitkommawerte <span class="codeph"> EXTINF </span> Dauer <p>Die Dauer-Tags ( <span class="codeph"> #EXTINF: </span>&lt;Dauer&gt;,&lt;Titel&gt;) in Version 2 wurden auf Ganzzahlwerte gerundet. Für Version 3 und höher ist eine exakte Gleitkommazahl erforderlich. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">Das Tag <span class="codeph"> EXT-X-MEDIA </span> </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">Die Attribute <span class="codeph"> AUDIO </span> und <span class="codeph"> VIDEO </span> des Tags <span class="codeph"> EXT-X-STREAM-INF </span> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
