---
description: TVSDK hat spezifische Anforderungen an Medieninhalte, Manifestinhalte, DRM und Softwareversionen.
title: Voraussetzungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Voraussetzungen {#requirements}

TVSDK erfordert spezifische Eigenschaften für Medieninhalte, Manifestinhalte, DRM und Softwareversionen.

## System and software requirements {#section_96E5B079900246E78682AE44D3F23068}

Um TVSDK zu verwenden, stellen Sie sicher, dass Ihre Hardware, Ihr Betriebssystem und Ihre Anwendungsversionen alle die unten aufgeführten Mindestanforderungen erfüllen.

| Betriebssystem | iOS 7.0 oder höher |
|---|---|
| Xcode | Xcode 10 für iOS 12 und Xcode 9 für iOS 11 |

## Anforderungen an Inhalt und Manifest {#section_72DD0E4DA9774DCCADB42887497F1386}

Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Wiedergabelisten (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.

| Schlüsselbilder des Inhaltssegments | Jedes Inhaltssegment muss mit einem Schlüsselrahmen beginnen. |
|---|---|
| Sequenznummern im Live-/Linearvideo | Must match between all bit-rate renditions for the main content at any given time. |

## EXT-X-VERSIONSANFORDERUNGEN {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

Die Version von `#EXT-X-VERSION` in der Manifestdatei [!DNL .m3u8] wirkt sich darauf aus, welche Funktionen für Ihre Anwendung verfügbar sind und welche `EXT` -Tags gültig sind.

Im Folgenden finden Sie einige Informationen zum Tag `#EXT-X-VERSION` , das die HLS-Protokollversion angibt:

* Die Version muss mit den Funktionen und Attributen in der HLS-Wiedergabeliste übereinstimmen. Andernfalls kann es zu Wiedergabefehlern kommen. Weitere Informationen finden Sie unter [HTTP Live Streaming-Spezifikation](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Adobe empfiehlt die Verwendung von mindestens Version 2 von HLS für die Wiedergabe in TVSDK-basierten Clients.

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2 </span> </td> 
   <td colname="2"> Das Attribut IV des Tags <span class="codeph"> EXT-X-KEY </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Gleitkommawerte <span class="codeph"> EXTINF </span> Dauer <p>Die Dauer-Tags ( <span class="codeph"> #EXTINF: </span>&lt;Dauer&gt;,&lt;Titel&gt;) in Version 2 wurden auf Ganzzahlwerte gerundet. Für Version 3 und höher müssen die Zeiträume genau angegeben werden, und zwar im Gleitpunkt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">Das Tag <span class="codeph"> EXT-X-BYTERANGE </span> </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">Das Tag <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">Die <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> Tag </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">Die <span class="codeph"> EXT-X-MEDIA </span> Tag </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">Die <span class="codeph"> AUDIO </span> und <span class="codeph"> VIDEO </span> -Attribute der <span class="codeph"> EXT-X-STREAM-INF </span> Tag </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">TVSDK - alternative Audio </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
