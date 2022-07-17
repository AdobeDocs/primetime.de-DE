---
description: TVSDK hat spezifische Anforderungen an Medieninhalte, Manifestinhalte, DRM und Softwareversionen.
title: Voraussetzungen
exl-id: 85bf7b85-5f4b-4ed5-aa4f-765dabc5d4d8
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Voraussetzungen {#requirements}

TVSDK hat spezifische Anforderungen an Medieninhalte, Manifestinhalte, DRM und Softwareversionen.

## System- und Softwareanforderungen {#section_96E5B079900246E78682AE44D3F23068}

Um TVSDK zu verwenden, stellen Sie sicher, dass Ihre Hardware, Ihr Betriebssystem und Ihre Anwendungsversionen alle die unten aufgeführten Mindestanforderungen erfüllen.

| Betriebssystem | Android 4.0 oder höher (Minimum API Level 14) |
|---|---|
| CPU | 1 GHz Einzelkernwert oder gleichwertig |
| RAM | 256 MB |
| GPU | Hardware-GPU für die Wiedergabe erforderlich |
| Architektur | x86 über Houdini, ARM64, ARMv7 und ARMv8 |

## Anforderungen an Inhalt und Manifest {#section_72DD0E4DA9774DCCADB42887497F1386}

Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Wiedergabelisten (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.

| Adobe Access DRM | Wenn der DRM-geschützte Stream eine Mehrfach-Bitrate (MBR) aufweist, sollte der für den MBR verwendete DRM-Verschlüsselungsschlüssel mit dem Schlüssel übereinstimmen, der in allen Bitratenströmen verwendet wird. |
|---|---|
| Anzeigenvariantenmanifeste | Muss über dieselbe Bitrate wie die Ausgabeformate des Hauptinhalts verfügen. |

## #EXT-X-VERSIONSANFORDERUNGEN {#section_49A33664651A46EC9ED888BA9C1C3F6D}

Die Version von `#EXT-X-VERSION` im [!DNL .m3u8] Die Manifestdatei beeinflusst, welche Funktionen für Ihre Anwendung verfügbar sind und welche `EXT` -Tags sind gültig.

Im Folgenden finden Sie einige Informationen zum `#EXT-X-VERSION` -Tag, das die HLS-Protokollversion angibt:

* Die Version muss mit den Funktionen und Attributen in der HLS-Wiedergabeliste übereinstimmen. Andernfalls können Wiedergabefehler auftreten. Weitere Informationen finden Sie unter [HTTP-Live-Streaming-Spezifikation](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
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
   <td colname="2"> Das Attribut IV des <span class="codeph"> EXT-X-KEY </span> -Tag. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Gleitkomma <span class="codeph"> EXTINF </span> Dauerwerte <p>The duration tags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in version 2 were rounded to integer values. Für Version 3 und höher müssen die Zeiträume genau angegeben werden, und zwar im Gleitpunkt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">Die <span class="codeph"> EXT-X-BYTERANGE </span> Tag </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">Die <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> Tag </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">Die <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> Tag </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">Die <span class="codeph"> EXT-X-MEDIA </span> Tag </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">Die <span class="codeph"> AUDIO </span> und <span class="codeph"> VIDEO </span> -Attribute der <span class="codeph"> EXT-X-STREAM-INF </span> Tag </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">TVSDK - alternative Audio </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
