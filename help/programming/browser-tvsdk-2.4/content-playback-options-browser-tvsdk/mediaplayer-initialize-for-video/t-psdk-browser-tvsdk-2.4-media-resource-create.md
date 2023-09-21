---
description: Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
title: Erstellen einer Medienressource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Erstellen einer Medienressource {#create-a-media-resource}

Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.

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
    <td colname="col2"> <p>Eines der folgenden Mitglieder der <span class="codeph"> MediaResource.Type </span> Auflistung, die dem angegebenen Dateityp entspricht: </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4 </span> - ISO-Basisformat für Mediendateien (MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>Metadaten </p> </td> 
    <td colname="col2"> <p>Eine Instanz der <span class="codeph"> Metadaten </span> -Klasse, die möglicherweise benutzerdefinierte Informationen über den zu ladenden Inhalt enthält. Beispiele für Inhalte sind alternative Inhalte oder Anzeigeninhalte, die innerhalb des Hauptinhalts platziert werden. Richten Sie bei Verwendung von Werbung <span class="codeph"> AuditudeSettings </span> bevor Sie diesen Konstruktor verwenden. Weitere Informationen finden Sie unter <a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Ad-Insertion-metadata</a>. </p> <p>Tipp: Sie können bei Bedarf einen Flash-Fallback erzwingen, indem Sie die <span class="codeph"> forceFlash </span> Parameter beim Erstellen einer Medienressource. Dies kann nützlich sein, da derzeit nicht alle Funktionen (wie Live-Anzeigen-Workflows) in Browser TVSDK unterstützt werden. Flash Fallback wird verwendet, um Videoinhalte wiederzugeben. </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >Browser TVSDK unterstützt die Wiedergabe nur für bestimmte Inhaltstypen. Wenn Sie versuchen, einen anderen Inhaltstyp zu laden, sendet Browser TVSDK ein Fehlerereignis.

   Der folgende Code erstellt eine `MediaResource` instance:

   ```js
   //create a MediaResource instance pointing to some HLS content 
   Metadata metadata = //TODO: create metadata here 
   mediaResource = new AdobePSDK.MediaResource ( 
         "https://www.example.com/video/some-video.m3u8", 
         AdobePSDK.MediaResourceType.HLS,  
         metadata);
   ```

   >[!TIP]
   >
   >Danach können Sie jederzeit `MediaResource` -Accessoires (Getter) zur Untersuchung des Typs, der URL und der Metadaten der Ressource.

1. Laden Sie Ihre MediaPlayer-Instanz. Weitere Informationen finden Sie unter [Laden einer Medienressource im MediaPlayer](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md).
