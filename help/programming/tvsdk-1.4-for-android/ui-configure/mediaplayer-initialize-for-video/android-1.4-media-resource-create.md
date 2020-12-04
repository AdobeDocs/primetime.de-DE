---
description: Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource. Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
seo-description: Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource. Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
seo-title: Medienressource erstellen
title: Medienressource erstellen
uuid: d9fe982a-bedf-445c-b5be-f7918693782a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Medienressource {#create-a-media-resource} erstellen

Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource. Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.

1. Erstellen Sie ein `MediaResource`, indem Sie Informationen über das Medium an den `MediaResource`-Konstruktor übergeben.

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
    <tr> 
    <th colname="col1" class="entry"> Konstruktor-Parameter </th> 
    <th colname="col2" class="entry"> Beschreibung </th> 
    </tr> 
    </thead>
    <tbody> 
    <tr> 
    <td colname="col1"> <p>url </p> </td> 
    <td colname="col2"> <p>Eine Zeichenfolge, die die URL der Manifest-/Wiedergabeliste des Mediums darstellt. </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>type </p> </td> 
    <td colname="col2"> <p>Eines der folgenden Member der Auflistung <span class="codeph"> MediaResource.Type </span>, die dem angegebenen Dateityp entspricht: 
    <ul id="ul_72636C41CA7E4538A3BE11A79E0282FC"> 
    <li id="li_070960200DEB40E992C58FCB8909AEA3"> <span class="codeph"> HLS  </span> - M3U8 </li> 
    </ul> </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metadata </p> </td> 
    <td colname="col2"> <p>Eine Instanz der Klasse <span class="codeph"> Metadata </span>, die benutzerdefinierte Informationen über den zu ladenden Inhalt enthalten kann. </p> <p>Beispiele für Inhalte sind alternative Inhalte oder Anzeigeninhalte, die in den Hauptinhalt platziert werden sollen. Richten Sie bei Verwendung von Werbung <span class="codeph"> AuditudeSettings </span> ein. Weitere Informationen finden Sie unter <a href="../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-insertion-metadata-set-up.md" format="dita" scope="local"> Ad Insertion Metadaten </a>. </p> </td> 
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
   try { 
       // create a MediaResource instance pointing to some HLS content 
       Metadata metadata = //TODO: create metadata  
       MediaResource mediaResource = MediaResource.createFromUrl( 
         "https://www.example.com/video/some-video.m3u8",  
         MediaResource.Type.HLS,  
         metadata); 
   } catch(IllegalArgumentException ex) { 
       // this exception is thrown if the URL does not point  
       // to a valid url. 
   } 
   ```

   >[!TIP]
   >
   >An dieser Stelle können Sie `MediaResource`-Accessoren (Getter) verwenden, um den Typ, die URL und die Metadaten der Ressource zu untersuchen.

1. Laden Sie die Medienressource wie folgt:

   * Ihre MediaPlayer-Instanz.

      Weitere Informationen finden Sie unter [Eine Medienressource in MediaPlayer](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-resource-load.md) laden.
   * A `MediaPlayerItemLoader` Weitere Informationen finden Sie unter [Medienressource mit MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md) laden.
   >[!IMPORTANT]
   >
   >Laden Sie die Medienressource nicht in einen Hintergrund-Thread. Die meisten TVSDK-Vorgänge müssen auf dem Haupt-Thread ausgeführt werden, und die Ausführung auf einem Hintergrund-Thread kann dazu führen, dass der Vorgang einen Fehler auslöst und beendet.
