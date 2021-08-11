---
description: Die Version von `#`EXT-X-VERSION in der .m3u8-Datei wirkt sich darauf aus, welche Funktionen für Ihre Anwendung verfügbar sind und welche EXT-Tags in Ihrer Wiedergabeliste/Ihrem Manifest gültig sind.
title: EXT-X-VERSIONSANFORDERUNGEN
exl-id: ee778fe1-d050-4c90-af8d-6600fff72e52
source-git-commit: 8610792a7410dab59d42ab7771b534c2c1670ad2
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# `#`EXT-X-VERSIONSANFORDERUNGEN{#ext-x-version-requirements}

Die Version von #EXT-X-VERSION in der .m3u8-Datei wirkt sich darauf aus, welche Funktionen für Ihre Anwendung verfügbar sind und welche EXT-Tags in Ihrer Wiedergabeliste/Ihrem Manifest gültig sind.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Im Folgenden finden Sie einige Informationen zum Tag `#EXT-X-VERSION` , das die HLS-Protokollversion angibt:

* Die Version muss mit den Funktionen und Attributen in der HLS-Wiedergabeliste übereinstimmen. Andernfalls können Wiedergabefehler auftreten.

   Weitere Informationen finden Sie unter [HTTP Live Streaming-Spezifikation](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Die Version muss mit den Funktionen und Attributen in der HLS-Wiedergabeliste übereinstimmen. Andernfalls können Wiedergabefehler auftreten.

   Weitere Informationen finden Sie unter [HTTP Live Streaming-Spezifikation](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Adobe empfiehlt die Verwendung von mindestens Version 2 für die Wiedergabe in -basierten Clients.

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2  </span> </td> 
   <td colname="2"> Das Attribut IV des Tags <span class="codeph"> EXT-X-KEY </span> . </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3  </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Gleitkommawerte <span class="codeph"> EXTINF </span> Dauerwerte <p>Die Dauer-Tags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in Version 2 wurden auf ganzzahlige Werte gerundet. Für Version 3 und höher ist eine exakte Gleitkommazahl erforderlich. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4  </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_83D61E909D0C413FBDAB7A4A0BE1F03C"> 
      <li id="li_5071F2BE2DB74BBFB1F23B3B30C5CFD6">Das Tag <span class="codeph"> EXT-X-BYTERANGE </span> </li> 
      <li id="li_A093F448567D475AB44656D4600BCBD6">Das Tag <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> </li> 
      <li id="li_1084AE3B10FD4EB387D25EEDDFBBC8CD">Das Tag <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> </li> 
      <li id="li_4FEFA36E300C403DBB77BB4DA46DB4EB">Das Tag <span class="codeph"> EXT-X-MEDIA </span> </li> 
      <li id="li_E53D81AED45C47AEA346FA3A1B191E5C">Die Attribute <span class="codeph"> AUDIO </span> und <span class="codeph"> VIDEO </span> des Tags <span class="codeph"> EXT-X-STREAM-INF </span> </li> 
      <li id="li_2E99A4971B8046F3845CF3D4D363CCCF">TVSDK - alternative Audio </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
