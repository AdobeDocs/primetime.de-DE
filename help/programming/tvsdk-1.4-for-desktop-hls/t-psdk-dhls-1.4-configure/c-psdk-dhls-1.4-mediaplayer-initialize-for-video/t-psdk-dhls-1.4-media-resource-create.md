---
description: Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
seo-description: Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
seo-title: Medienressource erstellen
title: Medienressource erstellen
uuid: 3d03d92f-69b3-4da8-9b16-25a264115ae5
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Medienressource {#create-a-media-resource} erstellen

Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource.

Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.

1. Erstellen Sie ein `MediaResource`, indem Sie Informationen über das Medium an den `MediaResource`-Konstruktor übergeben.

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> Konstruktor-Parameter </th> 
      <th colname="col2" class="entry"> Beschreibung </th> 
      </tr>
    </thead>
    =<tbody> 
      <tr> 
      <td colname="col1"><span class="codeph"> url</span> </td> 
      <td colname="col2"> <p>Eine Zeichenfolge, die die URL der Manifest-/Wiedergabeliste des Mediums darstellt. </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> type</span> </td> 
      <td colname="col2"> <p>Einer der folgenden Zeichenfolgenwerte, der dem angegebenen Dateityp entspricht: 
        <ul id="ul_7512E90B7B294EF9BFBA2D68DE678CBB"> 
        <li id="li_AA84434E84184A3D909552794B425ABD"><span class="codeph"> MP4</span> - ISO-Basismedienformat (MP4) </li> 
        <li id="li_8A2F3752569344B59EE30303A8393488"><span class="codeph"> HLS</span> - M3U8 </li> 
        </ul> </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> metadata</span> </td> 
      <td colname="col2"> <p>Eine Instanz der Klasse <span class="codeph"> Metadata</span>, die benutzerdefinierte Informationen über den zu ladenden Inhalt enthalten kann. </p> <p>Beispiele für Inhalte sind alternative Inhalte oder Anzeigeninhalte, die in den Hauptinhalt platziert werden sollen. Richten Sie bei Verwendung von Werbung <span class="codeph"> AuditudeSettings</span> ein, bevor Sie diesen Konstruktor verwenden. Weitere Informationen finden Sie unter <a href="../../../tvsdk-1.4-for-desktop-hls/ad-insertion/ad-insertion-metadata/c-psdk-dhls-1.4-ad-insertion-metadata.md" format="dita" scope="local"> Ad Insertion Metadata</a>. </p> </td> 
      </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK unterstützt die Wiedergabe nur für bestimmte Inhaltstypen. Wenn Sie versuchen, einen anderen Inhaltstyp zu laden, löst TVSDK ein Ereignis mit Fehler aus.
   >
   >Bei MP4-Video-on-Demand-Inhalten (VOD) unterstützt TVSDK keine Trick-Wiedergabe, adaptive Bitrate (ABR)-Streaming, Anzeigeneinfügung, Untertitel oder DRM.

   Der folgende Code erstellt eine `MediaResource`-Instanz:

   ```
   // To do: Create metadata here
   MyResource = new MediaResource(
            "https://www.example.com/video/some-video.m3u8", 
            "HLS",
            MyMetadata)
   ```

   >[!TIP]
   >
   >An dieser Stelle können Sie `MediaResource`-Accessoren (Getter) verwenden, um den Typ, die URL und die Metadaten der Ressource zu untersuchen.

1. Laden Sie die Medienressource mit einer der folgenden Methoden:

   * Ihre MediaPlayer-Instanz.

      Weitere Informationen finden Sie unter [Eine Medienressource in MediaPlayer](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md) laden.
   * A `MediaPlayerItemLoader` Weitere Informationen finden Sie unter [Medienressource in MediaPlayer](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md) laden.

