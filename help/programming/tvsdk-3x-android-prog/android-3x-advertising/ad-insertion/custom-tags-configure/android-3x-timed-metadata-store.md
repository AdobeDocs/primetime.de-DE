---
description: Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den entsprechenden Zeiten verwenden.
title: Speichern zeitgesteuerter Metadatenobjekte beim Versand
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# Speichern zeitgesteuerter Metadatenobjekte beim Versand {#store-timed-metadata-objects-as-they-are-dispatched}

Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den entsprechenden Zeiten verwenden.

Beim Analysieren von Inhalten, das vor der Wiedergabe erfolgt, identifiziert TVSDK abonnierte Tags und benachrichtigt Ihre Anwendung über diese Tags.

>[!TIP]
>
>Die mit jedem `TimedMetadata` ist die lokale Zeit auf der Wiedergabescheitleiste.

So speichern Sie zeitgesteuerte Metadatenobjekte beim Versand:

1. Behalten Sie die aktuelle Wiedergabezeit im Auge.
1. Übereinstimmung der aktuellen Wiedergabezeit mit der gesendeten `TimedMetadata` Objekte.

1. Verwenden Sie die `TimedMetadata` wobei die Startzeit der aktuellen lokalen Wiedergabezeit entspricht.

   Das folgende Beispiel zeigt, wie Sie speichern `TimedMetadata` Objekte in `ArrayList`.

   ```java
   private List<TimedMetadata> _timedMetadataList =  
     new ArrayList<TimedMetadata>(); 
   ... 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       ... 
       if (timedMetadata.getName().equalsIgnoreCase("#EXT-X-CUE"))  { 
           _timedMetadataList.add(timedMetadata); 
       } 
       ... 
   }
   ```
