---
description: TVSDK erfordert spezifische Eigenschaften für Medieninhalte, Manifestinhalte und Softwareversionen.
seo-description: TVSDK erfordert spezifische Eigenschaften für Medieninhalte, Manifestinhalte und Softwareversionen.
seo-title: Anforderungen
title: Anforderungen
uuid: 7e5fb176-4c3f-4c12-9080-3afced28627b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Voraussetzungen {#requirements}

TVSDK erfordert spezifische Eigenschaften für Medieninhalte, Manifestinhalte und Softwareversionen.

## System- und Softwareanforderungen {#section_61C32A0209C44230B392B113B85643EE}

Um TVSDK zu verwenden, stellen Sie sicher, dass Ihre Hardware-, Betriebssystem- und Anwendungsversionen alle die unten aufgeführten Mindestanforderungen erfüllen.

Betriebssystem: iOS 6.0 oder höher

## Anforderungen an Inhalt und Manifest {#section_05FA02E2189742008DA09D87E66DCAB7}

Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Playlists (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.

| Schlüsselbilder des Inhaltssegments | Jedes Inhaltssegment muss mit einem Schlüsselrahmen beginnen. |
|---|---|
| Sequenznummern im Live-/Linearvideo | Muss zu jeder Zeit zwischen allen Bitratendarstellungen für den Hauptinhalt übereinstimmen. |

## #EXT-X-VERSION requirements {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

Die Version von `#EXT-X-VERSION` in der Datei [!DNL .m3u8] beeinflusst, welche Funktionen für Ihre Anwendung verfügbar sind und welche `EXT`-Tags in Ihrer Wiedergabeliste/Ihrem Manifest gültig sind.

Im Folgenden finden Sie einige Informationen zum `#EXT-X-VERSION`-Tag, das die HLS-Protokollversion angibt:

* Die Version muss mit den Funktionen und Attributen in der HLS-Playlist übereinstimmen. Andernfalls kann es zu Wiedergabefehlern kommen.

   Weitere Informationen finden Sie unter [HTTP Live Streaming-Spezifikation](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Wenn das Tag nicht in der Übergeordnet- oder Medienwiedergabeliste enthalten ist oder keine Version angegeben wurde, wird standardmäßig Version 1 verwendet. Inhalte, die nicht mit Version 1 übereinstimmen, werden nicht wiedergegeben.
* Adobe empfiehlt, mindestens Version 2 für die Wiedergabe in TVSDK-basierten Clients zu verwenden.

Clients und Server müssen die Versionen wie folgt implementieren:

<table id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr> 
   <th colname="1" class="entry"> Mindestens diese Version verwenden </th> 
   <th colname="2" class="entry"> So verwenden Sie diese Funktionen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2  </span> </td> 
   <td colname="2"> Das Attribut IV des Tags <span class="codeph"> EXT-X-KEY </span>. </td> 
  </tr> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3  </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Fließkommawerte <span class="codeph"> EXTINF </span> <p>Die Dauer-Tags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in Version 2 wurden auf ganzzahlige Werte gerundet. Für Version 3 und höher muss die Dauer exakt im Gleitkommawert sein. </p> </li> 
     <li id="li_8DF5E91F1D5D4E19894595E1FE0A5EDE"> TVSDK-Funktionen wie Anzeigeneinfügung und nahtlose ABR </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4  </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_99E24D013E3141308B5A57446A9B8033"> 
      <li id="li_F36E65ADD2CA451C82FF18DBD5667927">Das <span class="codeph"> EXT-X-BYTERANGE </span>-Tag </li> 
      <li id="li_8C653168A7B84D11AC233E7548A8D2EF">Das Tag <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> </li> 
      <li id="li_2922B34717CB4F6189068529CDBE6D10">Das <span class="codeph"> EXT-X-I-FRAMES-ONLY </span>-Tag </li> 
      <li id="li_D015D78E217641D7867EB509E9F9EEE2">Das <span class="codeph"> EXT-X-MEDIA </span>-Tag </li> 
      <li id="li_CA068EA381984F5497FE67617CA8BB34">Die Attribute <span class="codeph"> AUDIO </span> und <span class="codeph"> VIDEO </span> des <span class="codeph">-Tags EXT-X-STREAM-INF </span> </li> 
      <li id="li_EE78CC7D194A4EB2897F9AE8E4B081B8"> TVSDK Alternative Audio </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
