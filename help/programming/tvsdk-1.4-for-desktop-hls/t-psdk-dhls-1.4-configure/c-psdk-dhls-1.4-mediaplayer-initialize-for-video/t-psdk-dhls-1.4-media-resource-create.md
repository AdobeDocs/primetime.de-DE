---
description: Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
title: Erstellen einer Medienressource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Erstellen einer Medienressource {#create-a-media-resource}

Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource.

Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.

1. Erstellen Sie eine `MediaResource` durch Übergabe von Informationen über die Medien an die `MediaResource` -Konstruktor.

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> Konstruktionsparameter </th> 
      <th colname="col2" class="entry"> Beschreibung </th> 
      </tr>
    </thead>
    =<tbody> 
      <tr> 
      <td colname="col1"><span class="codeph"> url</span> </td> 
      <td colname="col2"> <p>Eine Zeichenfolge, die die URL des Manifests/der Wiedergabeliste des Mediums darstellt. </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> type</span> </td> 
      <td colname="col2"> <p>Einer der folgenden string -Werte, der dem angegebenen Dateityp entspricht: 
        <ul id="ul_7512E90B7B294EF9BFBA2D68DE678CBB"> 
        <li id="li_AA84434E84184A3D909552794B425ABD"><span class="codeph"> MP4</span> - ISO-Basisformat für Mediendateien (MP4) </li> 
        <li id="li_8A2F3752569344B59EE30303A8393488"><span class="codeph"> HLS</span> - M3U8 </li> 
        </ul> </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> Metadaten</span> </td> 
      <td colname="col2"> <p>Eine Instanz der <span class="codeph"> Metadaten</span> -Klasse, die möglicherweise benutzerdefinierte Informationen über den zu ladenden Inhalt enthält. </p> <p>Beispiele für Inhalte sind alternative Inhalte oder Anzeigeninhalte, die innerhalb des Hauptinhalts platziert werden. Richten Sie bei Verwendung von Werbung <span class="codeph"> AuditudeSettings</span> bevor Sie diesen Konstruktor verwenden. Weitere Informationen finden Sie unter <a href="../../../tvsdk-1.4-for-desktop-hls/ad-insertion/ad-insertion-metadata/c-psdk-dhls-1.4-ad-insertion-metadata.md" format="dita" scope="local"> Ad Insertion-Metadaten</a>. </p> </td> 
      </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK unterstützt die Wiedergabe nur für bestimmte Inhaltstypen. Wenn Sie versuchen, einen anderen Inhaltstyp zu laden, sendet TVSDK ein Fehlerereignis.
   >
   >Bei MP4-Video-On-Demand (VOD)-Inhalten unterstützt TVSDK keine Trickwiedergabe, adaptive Bitrate (ABR)-Streaming, Anzeigeneinfügung, geschlossene Untertitel oder DRM.

   Der folgende Code erstellt eine `MediaResource` instance:

   ```
   // To do: Create metadata here
   MyResource = new MediaResource(
            "https://www.example.com/video/some-video.m3u8", 
            "HLS",
            MyMetadata)
   ```

   >[!TIP]
   >
   >An dieser Stelle können Sie `MediaResource` -Accessoires (Getter) zur Untersuchung des Typs, der URL und der Metadaten der Ressource.

1. Laden Sie die Medienressource mit einer der folgenden Methoden:

   * Ihre MediaPlayer-Instanz.

     Weitere Informationen finden Sie unter [Laden einer Medienressource in MediaPlayer](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md).
   * A `MediaPlayerItemLoader` Weitere Informationen finden Sie unter [Laden einer Medienressource in MediaPlayer](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md).
