---
description: Ihre Anwendung muss die entsprechenden PTTimedMetadata-Objekte zu den richtigen Zeiten verwenden.
seo-description: Ihre Anwendung muss die entsprechenden PTTimedMetadata-Objekte zu den richtigen Zeiten verwenden.
seo-title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
uuid: 38e72a9b-571a-48da-9c17-80be453e6a98
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden. {#store-timed-metadata-objects-as-they-are-dispatched}

Ihre Anwendung muss die entsprechenden PTTimedMetadata-Objekte zu den richtigen Zeiten verwenden.

Beim Analysieren von Inhalten, das vor der Wiedergabe erfolgt, identifiziert TVSDK abonnierte Tags und benachrichtigt Ihre Anwendung über diese Tags. Die mit jedem `PTTimedMetadata` verbundene Zeit ist die absolute Zeit auf der Wiedergabeschlüssel.

Ihr Antrag muss die folgenden Aufgaben abschließen:

1. Behalten Sie die aktuelle Wiedergabezeit im Auge.
1. Ordnen Sie die aktuelle Wiedergabezeit den ausgelösten Objekten `PTTimedMetadata` zu.

1. Verwenden Sie das `PTTimedMetadata`, wobei die Beginn-Zeit der aktuellen Wiedergabezeit entspricht.

   >[!NOTE]
   >
   >Der unten stehende Code setzt voraus, dass immer nur eine `PTTimedMetadata`-Instanz vorhanden ist. Wenn mehrere Instanzen vorhanden sind, muss die Anwendung sie entsprechend in einem Wörterbuch speichern. Eine Methode besteht darin, ein Array zu einem bestimmten Zeitpunkt zu erstellen und alle Instanzen in diesem Array zu speichern.

   Im folgenden Beispiel wird gezeigt, wie `PTTimedMetadata`-Objekte in einem `NSMutableDictionary (timedMetadataCollection)`-Schlüsselwort gespeichert werden, das nach der Beginn jedes `timedMetadata`-Parameters geordnet ist.

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

## Parsen von Nielsen-ID3-Tags {#example_3B51E9D4AF2449FAA8E804206F873ECF}

Um das ID3-Tag für die Analyse zu extrahieren, verwenden Sie Folgendes für die `onMediaPlayerSubscribedTagIdentified`-Methode:

```
(void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
{ 
NSDictionary *userInfo = [notification userInfo]; 
PTTimedMetadata *timedMetadata = (PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey]; 
if (timedMetadata.type == PTTimedMetadataTypeID3) 
Unknown macro: { PTMetadata *metadata = (PTMetadata *)timedMetadata; NSString * nstr = [[NSString alloc] initWithFormat} 
 
}
```

Extrahieren Sie nach der Analyse des ID3-Tags die Nielsen-spezifischen Metadaten wie folgt:

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
