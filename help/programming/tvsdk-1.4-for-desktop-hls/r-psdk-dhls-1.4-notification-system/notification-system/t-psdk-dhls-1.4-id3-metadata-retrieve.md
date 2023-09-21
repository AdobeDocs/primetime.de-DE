---
description: ID3-Tags bieten Informationen zu einer Audio- oder Videodatei, wie den Titel der Datei oder den Namen des Künstlers. erkennt ID3-Tags auf der Transport Stream-(TS-)Segmentebene in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem -Tag extrahieren.
title: ID3-Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# ID3-Tags{#id-tags}

ID3-Tags bieten Informationen zu einer Audio- oder Videodatei, wie den Titel der Datei oder den Namen des Künstlers. erkennt ID3-Tags auf der Transport Stream-(TS-)Segmentebene in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem -Tag extrahieren.

>[!IMPORTANT]
>
>TVSDK erkennt ID3-Metadaten (Version 2.3.0 oder 2.4.0) in Audio- (AAC) und Video-Streams (H.264) in jeder der möglichen Kodierungen (ASCII, UTF8, UTF16-BE oder UTF16-LE). Dabei werden ID3-Tags ignoriert, die sich nicht in einer der erkannten Versionen oder Formate befinden. Nicht angegebene Kodierung wird als UTF8 behandelt.

Wenn TVSDK ID3-Metadaten erkennt, wird eine Benachrichtigung mit den folgenden Daten ausgegeben:

* InfoCode = 303007
* TYPE = ID3
* NAME = nicht vorhanden
* ID = 0

1. Implementieren eines Ereignis-Listeners für `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED` und registrieren Sie sie bei der `MediaPlayer` -Objekt.

   TVSDK ruft diesen Listener auf, wenn ID3-Metadaten erkannt werden.

   >[!NOTE]
   >
   >Benutzerdefinierte Anzeigencodes verwenden dieselbe `onTimedMetadata` -Ereignis, um die Erkennung eines neuen Tags anzuzeigen. Dies sollte keine Verwirrung verursachen, da benutzerdefinierte Anzeigencodes auf Manifestebene erkannt und ID3-Tags in den Stream eingebettet werden. Weitere Informationen finden Sie unter custom-tags-configure .

1. Rufen Sie die Metadaten ab.

   ```
   private function onID3Metadata(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       var metadata:Metadata = timedMetadata.metadata; 
       var keys:Vector.<String> = metadata.keySet(); 
       for (var i:int = keys.length - 1; i >= 0; --i) { 
           var value:ByteArray = metadata.getByteArray(keys[i]); 
           _logger.info("#onTimedMetadata Detected dictionary data key: [{0}],  
                        value: [{1}] of length {2} bytes at time [{3}].",  
                        keys[i],  
                        value.toString(),  
                        value.length,  
                        event.timedMetadata.time); 
       } 
   } 
   ```
