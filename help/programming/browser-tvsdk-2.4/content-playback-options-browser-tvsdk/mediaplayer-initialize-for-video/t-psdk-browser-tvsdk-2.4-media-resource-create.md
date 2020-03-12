---
description: Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
seo-description: Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.
seo-title: Medienressource erstellen
title: Medienressource erstellen
uuid: c25c037e-e9a0-430c-a150-b75a9ac051b1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Medienressource erstellen {#create-a-media-resource}

Die MediaResource-Klasse stellt den Inhalt dar, der von der MediaPlayer-Instanz geladen werden soll.

1. Erstellen Sie eine Datei, `MediaResource` indem Sie Informationen über das Medium an den `MediaResource` Konstruktor weiterleiten.

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
    <td colname="col2"> <p>Einer der folgenden Member der <span class="codeph"> MediaResource.Type- </span> Auflistung, die dem angegebenen Dateityp entspricht: </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4 </span> - ISO-Basismedienformat (MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metadata </p> </td> 
    <td colname="col2"> <p>Eine Instanz der <span class="codeph"> Metadata- </span> Klasse, die benutzerdefinierte Informationen über den zu ladenden Inhalt enthalten kann. Beispiele für Inhalte sind alternative Inhalte oder Anzeigeninhalte, die in den Hauptinhalt platziert werden sollen. Wenn Sie Werbung verwenden, richten Sie <span class="codeph"> AuditudeSettings ein, </span> bevor Sie diesen Konstruktor verwenden. Weitere Informationen finden Sie unter <a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Ad-Insertion-metadata</a>. </p> <p>Tipp:  Sie können bei Bedarf Flash-Ausweichmöglichkeiten erzwingen, indem Sie beim Erstellen einer Medienressource den <span class="codeph"> forceFlash- </span> Parameter verwenden. Dies kann nützlich sein, da derzeit nicht alle Funktionen (wie Live Ad Workflows) in Browser TVSDK unterstützt werden. Flash-Fallback wird verwendet, um Videoinhalte wiederzugeben. </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >Browser TVSDK unterstützt die Wiedergabe nur für bestimmte Inhaltstypen. Wenn Sie versuchen, einen anderen Inhaltstyp zu laden, löst Browser TVSDK ein Ereignis aus.

   Mit dem folgenden Code wird eine `MediaResource` Instanz erstellt:

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
   >Anschließend können Sie jederzeit mithilfe von `MediaResource` Accessoren (Gettern) den Typ, die URL und die Metadaten der Ressource überprüfen.

1. Laden Sie die MediaPlayer-Instanz. Weitere Informationen finden Sie unter [Medienressource im MediaPlayer](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md)laden.
