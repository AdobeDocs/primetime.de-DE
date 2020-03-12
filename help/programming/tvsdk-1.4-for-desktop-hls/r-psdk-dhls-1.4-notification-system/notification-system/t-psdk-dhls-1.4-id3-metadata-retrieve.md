---
description: ID3-Tags enthalten Informationen zu einer Audio- oder Videodatei, wie z. B. den Titel der Datei oder den Namen des Künstlers. erkennt ID3-Tags auf der Segmentebene Transport Stream (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem Tag extrahieren.
seo-description: ID3-Tags enthalten Informationen zu einer Audio- oder Videodatei, wie z. B. den Titel der Datei oder den Namen des Künstlers. erkennt ID3-Tags auf der Segmentebene Transport Stream (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem Tag extrahieren.
seo-title: ID3-Tags
title: ID3-Tags
uuid: 5c016260-5ced-480e-897a-11ffe7f34441
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ID3-Tags{#id-tags}

ID3-Tags enthalten Informationen zu einer Audio- oder Videodatei, wie z. B. den Titel der Datei oder den Namen des Künstlers. erkennt ID3-Tags auf der Segmentebene Transport Stream (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem Tag extrahieren.

>[!IMPORTANT]
>
>TVSDK erkennt ID3-Metadaten (Version 2.3.0 oder 2.4.0) in Audio- (AAC) und Video-Streams (H.264) in allen möglichen Kodierungen (ASCII, UTF8, UTF16-BE oder UTF16-LE). Dabei werden ID3-Tags ignoriert, die sich nicht in einer der erkannten Versionen oder Formate befinden. Nicht angegebene Kodierung wird als UTF8 behandelt.

Wenn TVSDK ID3-Metadaten erkennt, wird eine Benachrichtigung mit den folgenden Daten ausgegeben:

* InfoCode = 303007
* TYPE = ID3
* NAME = nicht vorhanden
* ID = 0

1. Implementieren Sie einen Ereignis-Listener für `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED` und registrieren Sie ihn beim `MediaPlayer` -Objekt.

   TVSDK ruft diesen Listener auf, wenn er ID3-Metadaten erkennt.

   >[!NOTE]
   >
   >Benutzerdefinierte Anzeigenbezeichnungen verwenden dasselbe `onTimedMetadata` Ereignis, um die Erkennung eines neuen Tags anzuzeigen. Dies sollte keine Verwirrung stiften, da auf Manifestebene benutzerdefinierte Anzeigenbezeichnungen erkannt werden und ID3-Tags im Stream eingebettet werden. Weitere Informationen finden Sie unter custom-tags-configure .

1. Abrufen der Metadaten.

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

