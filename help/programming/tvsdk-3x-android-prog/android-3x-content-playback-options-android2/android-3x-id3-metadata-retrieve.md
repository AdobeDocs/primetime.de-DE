---
description: ID3-Tags bieten Informationen zu einer Audio- oder Videodatei, wie den Titel der Datei oder den Namen des Künstlers. TVSDK erkennt ID3-Tags auf der Segmentebene des Transport-Streams (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem -Tag extrahieren.
title: ID3-Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# ID3-Tags {#id-tags}

ID3-Tags bieten Informationen zu einer Audio- oder Videodatei, wie den Titel der Datei oder den Namen des Künstlers. TVSDK erkennt ID3-Tags auf der Segmentebene des Transport-Streams (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem -Tag extrahieren.

>[!IMPORTANT]
>
>TVSDK erkennt ID3-Metadaten (Version 2.3.0 oder 2.4.0) in Audio- (AAC) und Video-Streams (H.264) in allen möglichen Kodierungen (ASCII, UTF8, UTF16-BE oder UTF16-LE). Dabei werden ID3-Tags ignoriert, die sich nicht in einer der erkannten Versionen oder Formate befinden. Nicht angegebene Kodierung wird als UTF8 behandelt.

Wenn TVSDK ID3-Metadaten erkennt, wird eine Benachrichtigung mit den folgenden Daten ausgegeben:

* TYPE = ID3
* NAME = ID3

1. Implementieren eines Ereignis-Listeners für `MediaPlayer.TimedMetadataEventListener#onTimedMetadata(TimeMetadata timeMetadata)` und registrieren Sie sie bei der `MediaPlayer` -Objekt.

   TVSDK ruft diesen Listener auf, wenn er erkennt `ID3` Metadaten.

   >[!TIP]
   >
   >Benutzerdefinierte Anzeigencodes verwenden dieselbe `onTimedMetadata` -Ereignis, um die Erkennung eines neuen Tags anzuzeigen. Dies sollte keine Verwirrung verursachen, da benutzerdefinierte Anzeigencodes auf Manifestebene erkannt und ID3-Tags in den Stream eingebettet werden. Weitere Informationen finden Sie unter [Benutzerdefinierte Tags](../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/custom-tags-configure/android-3x-custom-tags-configure.md).

1. Rufen Sie die Metadaten ab.

   ```java
   @Override 
    public void onTimedMetadata(TimedMetadata timedMetadata) { 
       TimedMetadata.Type type = timedMetadata.getType(); 
       if (type.equals(TimedMetadata.Type.ID3)){ 
           long time = timeMetadata.getTime(); 
           Metadata metadata = timedMetadata.getMetadata(); 
           Set<String> keys = metadata.keySet(); 
           for (String key : keys){ 
               byte[] value = metadata.getByteArray(key); 
           } 
       } 
   }
   ```
