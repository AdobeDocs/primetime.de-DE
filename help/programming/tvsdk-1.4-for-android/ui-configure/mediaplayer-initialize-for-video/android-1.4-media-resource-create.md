---
description: Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource. Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
title: Erstellen einer Medienressource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Erstellen einer Medienressource {#create-a-media-resource}

Initialisieren Sie für jeden neuen Videoinhalt eine MediaResource-Instanz mit Informationen zum Videoinhalt und laden Sie die Medienressource. Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.

1. Erstellen Sie eine `MediaResource` durch Übergabe von Informationen über die Medien an die `MediaResource` -Konstruktor.

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
    <tr> 
    <th colname="col1" class="entry"> Konstruktionsparameter </th> 
    <th colname="col2" class="entry"> Beschreibung </th> 
    </tr> 
    </thead>
    <tbody> 
    <tr> 
    <td colname="col1"> <p>url </p> </td> 
    <td colname="col2"> <p>Eine Zeichenfolge, die die URL des Manifests/der Wiedergabeliste des Mediums darstellt. </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>type </p> </td> 
    <td colname="col2"> <p>Eines der folgenden Mitglieder der <span class="codeph"> MediaResource.Type </span> Auflistung, die dem angegebenen Dateityp entspricht: 
    <ul id="ul_72636C41CA7E4538A3BE11A79E0282FC"> 
    <li id="li_070960200DEB40E992C58FCB8909AEA3"> <span class="codeph"> HLS </span> - M3U8 </li> 
    </ul> </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>Metadaten </p> </td> 
    <td colname="col2"> <p>Eine Instanz der <span class="codeph"> Metadaten </span> -Klasse, die möglicherweise benutzerdefinierte Informationen über den zu ladenden Inhalt enthält. </p> <p>Beispiele für Inhalte sind alternative Inhalte oder Anzeigeninhalte, die innerhalb des Hauptinhalts platziert werden. Richten Sie bei Verwendung von Werbung <span class="codeph"> AuditudeSettings </span>. Weitere Informationen finden Sie unter <a href="../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-insertion-metadata-set-up.md" format="dita" scope="local"> Ad Insertion-Metadaten </a>. </p> </td> 
    </tr> 
    </tbody> 
    </table>

   >[!IMPORTANT]
   >
   >TVSDK unterstützt die Wiedergabe nur für bestimmte Inhaltstypen. Wenn Sie versuchen, einen anderen Inhaltstyp zu laden, sendet TVSDK ein Fehlerereignis.
   >
   >Bei MP4-Video-On-Demand (VOD)-Inhalten unterstützt TVSDK keine Trickwiedergabe, adaptive Bitrate (ABR)-Streaming, Anzeigeneinfügung, geschlossene Untertitel oder DRM.

   Der folgende Code erstellt eine `MediaResource` instance:

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
   >An dieser Stelle können Sie `MediaResource` -Accessoires (Getter) zur Untersuchung des Typs, der URL und der Metadaten der Ressource.

1. Laden Sie die Medienressource wie folgt:

   * Ihre MediaPlayer-Instanz.

     Weitere Informationen finden Sie unter [Laden einer Medienressource im MediaPlayer](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-resource-load.md).
   * A `MediaPlayerItemLoader` Weitere Informationen finden Sie unter [Laden einer Medienressource mit MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

   >[!IMPORTANT]
   >
   >Laden Sie die Medienressource nicht in einen Hintergrund-Thread. Die meisten TVSDK-Vorgänge müssen im Haupt-Thread ausgeführt werden, und die Ausführung in einem Hintergrund-Thread kann dazu führen, dass der Vorgang einen Fehler auslöst und beendet.
