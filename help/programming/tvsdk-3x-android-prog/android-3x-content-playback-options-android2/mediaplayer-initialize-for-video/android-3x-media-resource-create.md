---
description: Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
title: Erstellen einer Medienressource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Erstellen einer Medienressource {#create-a-media-resource}

Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource.

Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.

1. Erstellen Sie eine `MediaResource` durch Übergabe von Informationen über die Medien an die `MediaResource` -Konstruktor.

   Die `MediaResource` -Konstruktor erfordert die folgenden Parameter:

   <table id="table_22886D6770FB45E99D35D0B90E6CC302"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> Konstruktionsparameter </th> 
      <th colname="col2" class="entry"> Beschreibung </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> <span class="codeph"> url </span> </td> 
      <td colname="col2"> Eine Zeichenfolge, die die URL des Manifests/der Wiedergabeliste des Mediums darstellt. </td> 
   </tr> 
   <tr> 
      <td colname="col1"> <span class="codeph"> type </span> </td> 
      <td colname="col2"> Eines der folgenden Mitglieder der <span class="codeph"> MediaResource.Type </span> enum, entsprechend dem angegebenen Dateityp: 
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282"> 
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li> 
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - ISO-Basisformat für Mediendateien (MP4) </li> 
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - Beschreibung der MPEG-DASH-Medienpräsentation (MPD) </li> 
      </ul> </td> 
   </tr> 
   <tr> 
      <td colname="col1"> <span class="codeph"> Metadaten </span> </td> 
      <td colname="col2"> Eine Instanz der <span class="codeph"> Metadaten </span> -Klasse (eine wörterbuchähnliche Struktur), die zusätzliche Informationen über den Inhalt enthalten kann, der geladen werden soll, z. B. alternative Inhalte oder Anzeigeninhalte, die innerhalb des Hauptinhalts platziert werden sollen. Richten Sie bei Verwendung von Werbung <span class="codeph"> AuditudeSettings </span> bevor Sie diesen Konstruktor verwenden <a href="/help/programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-insertion-metadata/android-3x-ad-insertion-metadata.md"> Anzeigeneinfüge-Metadaten </a>. </td> 
   </tr> 
   </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK unterstützt die Wiedergabe nur für bestimmte Inhaltstypen. Wenn Sie versuchen, einen anderen Inhaltstyp zu laden, sendet TVSDK ein Fehlerereignis.
   >
   >Bei MP4-Video-On-Demand (VOD)-Inhalten unterstützt TVSDK keine Trickwiedergabe, adaptive Bitrate (ABR)-Streaming, Anzeigeneinfügung, geschlossene Untertitel oder DRM.

   Der folgende Code erstellt eine `MediaResource` instance: >

   ```java
   // To do: Create metadata here 
   MediaResource res = new MediaResource( 
     "https://www.example.com/video/some-video.m3u8",  
   MediaResource.Type.HLS, 
     metadata); 
   ```

   Sie können nach diesem Schritt jederzeit Folgendes verwenden: `MediaResource` -Accessoires (Getter) zur Untersuchung des Typs, der URL und der Metadaten der Ressource.

1. Laden Sie die Medienressource mit einer der folgenden Optionen:

   * Die MediaPlayer-Instanz.
   * `MediaPlayerItemLoader` Weitere Informationen finden Sie unter [Laden einer Medienressource mit MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

   >[!IMPORTANT]
   >
   >Laden Sie die Medienressource nicht in einen Hintergrund-Thread. Die meisten TVSDK-Vorgänge müssen im Haupt-Thread ausgeführt werden, und die Ausführung in einem Hintergrund-Thread kann dazu führen, dass der Vorgang einen Fehler auslöst und beendet.
