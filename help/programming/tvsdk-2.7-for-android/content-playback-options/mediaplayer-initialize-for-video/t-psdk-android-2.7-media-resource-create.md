---
description: Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
title: Medienressource erstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# Medienressource {#create-a-media-resource} erstellen

Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource.

Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.

1. Erstellen Sie ein `MediaResource`, indem Sie Informationen über das Medium an den `MediaResource`-Konstruktor übergeben.

   Der Konstruktor `MediaResource` erfordert die folgenden Parameter:

   <table id="table_22886D6770FB45E99D35D0B90E6CC302">
      <thead>
      <tr>
      <th colname="col1" class="entry"> Konstruktor-Parameter </th>
      <th colname="col2" class="entry"> Beschreibung </th>
      </tr>
      </thead>
      <tbody>
      <tr>
      <td colname="col1"> <span class="codeph"> url  </span> </td>
      <td colname="col2"> Eine Zeichenfolge, die die URL der Manifest-/Wiedergabeliste des Mediums darstellt. </td>
      </tr>
      <tr>
      <td colname="col1"> <span class="codeph"> type  </span> </td>
      <td colname="col2"> Eines der folgenden Mitglieder des Enums <span class="codeph"> MediaResource.Type </span>, entsprechend dem angegebenen Dateityp:
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282">
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS  </span> - M3U8 </li>
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF  </span> - ISO-Basismedienformat (MP4) </li>
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH  </span> - Beschreibung der MPEG-DASH-Medienpräsentation (MPD) </li>
      </ul> </td>
      </tr>
      <tr>
      <td colname="col1"> <span class="codeph"> metadata  </span> </td>
      <td colname="col2"> Eine Instanz der Klasse <span class="codeph"> Metadata </span> (eine wörterbuchähnliche Struktur), die zusätzliche Informationen über den Inhalt enthält, der geladen werden soll, z. B. alternative Inhalte oder Anzeigeninhalte, die innerhalb des Hauptinhalts platziert werden sollen. Richten Sie bei Verwendung von Werbung <span class="codeph"> AuditudeSettings </span> ein, bevor Sie diesen Konstruktor verwenden. </td>
      </tr>
      </tbody>
   </table>

   >[!IMPORTANT]
   >
   >TVSDK unterstützt die Wiedergabe nur für bestimmte Inhaltstypen. Wenn Sie versuchen, einen anderen Inhaltstyp zu laden, löst TVSDK ein Ereignis mit Fehler aus.
   >
   >Bei MP4-Video-on-Demand-Inhalten (VOD) unterstützt TVSDK keine Trick-Wiedergabe, adaptive Bitrate (ABR)-Streaming, Anzeigeneinfügung, Untertitel oder DRM.

   Der folgende Code erstellt eine `MediaResource`-Instanz:

   ```java
   // To do: Create metadata here
   MediaResource res = new MediaResource(
     "https://www.example.com/video/some-video.m3u8",
     MediaResource.Type.HLS,
     metadata);
   ```

   Nach diesem Schritt können Sie jederzeit `MediaResource`-Accessoren (Getter) verwenden, um den Typ, die URL und die Metadaten der Ressource zu untersuchen.

1. Laden Sie die Medienressource mit einer der folgenden Optionen:

   * Die MediaPlayer-Instanz.
   * `MediaPlayerItemLoader` Weitere Informationen finden Sie unter  [Laden einer Medienressource mit MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).

   >[!IMPORTANT]
   >
   >Laden Sie die Medienressource nicht in einen Hintergrund-Thread. Die meisten TVSDK-Vorgänge müssen auf dem Haupt-Thread ausgeführt werden, und die Ausführung auf einem Hintergrund-Thread kann dazu führen, dass der Vorgang einen Fehler auslöst und beendet.
