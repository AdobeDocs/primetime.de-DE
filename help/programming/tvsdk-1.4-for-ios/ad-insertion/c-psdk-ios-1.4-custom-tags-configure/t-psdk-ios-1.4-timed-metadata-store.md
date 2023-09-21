---
description: Ihre Anwendung muss die entsprechenden PTTimedMetadata-Objekte zu den entsprechenden Zeiten verwenden.
title: Speichern zeitgesteuerter Metadatenobjekte beim Versand
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Speichern zeitgesteuerter Metadatenobjekte beim Versand {#store-timed-metadata-objects-as-they-are-dispatched}

Ihre Anwendung muss die entsprechenden PTTimedMetadata-Objekte zu den entsprechenden Zeiten verwenden.

Beim Analysieren von Inhalten, das vor der Wiedergabe erfolgt, identifiziert TVSDK abonnierte Tags und benachrichtigt Ihre Anwendung über diese Tags. Die mit jedem `PTTimedMetadata` ist die absolute Zeit auf der Wiedergabe-Timeline.

Ihre Anwendung muss die folgenden Aufgaben ausführen:

1. Behalten Sie die aktuelle Wiedergabezeit im Auge.
1. Übereinstimmung der aktuellen Wiedergabezeit mit der gesendeten `PTTimedMetadata` Objekte.

1. Verwenden Sie die `PTTimedMetadata` wobei die Startzeit der aktuellen Wiedergabezeit entspricht.

   >[!NOTE]
   >
   >Im folgenden Code wird davon ausgegangen, dass es nur einen `PTTimedMetadata` -Instanz zu einer bestimmten Zeit. Wenn mehrere Instanzen vorhanden sind, muss die Anwendung sie ordnungsgemäß in einem Wörterbuch speichern. Eine Methode besteht darin, ein Array zu einem bestimmten Zeitpunkt zu erstellen und alle Instanzen in diesem Array zu speichern.

   Das folgende Beispiel zeigt, wie Sie speichern `PTTimedMetadata` Objekte in `NSMutableDictionary (timedMetadataCollection)` die durch die Startzeit jedes `timedMetadata`.

   ```
   NSMutableDictionary *timedMetadataCollection; 
   
   - (void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
   { 
       if (!timedMetadataCollection) 
       { 
           timedMetadataCollection = [[NSMutableDictionary alloc] init]; 
       } 
       NSDictionary *userInfo = [notification userInfo]; 
       PTTimedMetadata *timedMetadata = [(PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey] retain]; 
       if ([timedMetadata.name  isEqualToString: @"#EXT-OATCLS-SCTE35"]) 
       { 
            NSLog(@"Adding timedMetadata %@ to timedMetadataCollection with time                      
                    %f",timedMetadata.name,CMTimeGetSeconds(timedMetadata.time)); 
   
           NSNumber *timedMetadataStartTime = [NSNumber numberWithInt:(int)CMTimeGetSeconds(timedMetadata.time)]; 
           [timedMetadataCollection setObject:timedMetadata forKey:timedMetadataStartTime]; 
       } 
       [timedMetadata release]; 
   }
   ```

## Parsen von Nielsen ID3-Tags {#example_3B51E9D4AF2449FAA8E804206F873ECF}

Um das ID3-Tag für das Parsen zu extrahieren, verwenden Sie Folgendes für die `onMediaPlayerSubscribedTagIdentified` -Methode:

```
(void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
{ 
NSDictionary *userInfo = [notification userInfo]; 
PTTimedMetadata *timedMetadata = (PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey]; 
if (timedMetadata.type == PTTimedMetadataTypeID3) 
Unknown macro: { PTMetadata *metadata = (PTMetadata *)timedMetadata; NSString * nstr = [[NSString alloc] initWithFormat} 
 
}
```

Nachdem Sie das ID3-Tag analysiert haben, extrahieren Sie die Nielsen-spezifischen Metadaten wie folgt:

```
    (NSString *)parseNielsenUrlFromID3Tag:(NSString *)str 
    { 
    /* ID3 tag <AVMetadataItem: 0x15e58e60, identifier=id3/PRIV, keySpace=org.id3, key class = __NSCFString, key=PRIV, commonKey=(null), extendedLanguageTag=(null), dataType=(null), time= {110265598/4410000 = 25.004} 
 
    , duration= 
    {INVALID} 
 
    , startDate=(null), extras= 
    { info = "www.nielsen.com/X100zdCIGeIlgZnkYj6UvQ==/pI-X5FFk07770SXf2ZbI6g==/CE0C6​1TsDo0jIrNn9N2yTPe6nVG3dHZHfgS52fJeQjf9fJCga9tj4OW4NXPZ9fI1mx0gfYUPBXnjqolHemZPtn_FCoNg​8Dqw8-Auruf15fU04pJfXTTN0IgZ4iWBmeRiPpS9X100zdCIGeIlgZnkYj6UvVjmPIdY5jyRQTA=/00000/21778/00"; } 
 
    , value length=1> 
    */ 
 
NSString *nielsenStr = nil; 
for (NSString *keyValuePairString in [str componentsSeparatedByString:@", "]) 
{ 
if([keyValuePairString rangeOfString:@"nielsen.com"].location != NSNotFound) 
{ // Nielsen NSRange start = [keyValuePairString rangeOfString:@"\""]; NSRange end = [keyValuePairString rangeOfString:@"\";"]; nielsenStr = [keyValuePairString substringWithRange:NSMakeRange(start.location + 1, end.location-start.location)]; } 
 
} 
return nielsenStr; 
}
```
