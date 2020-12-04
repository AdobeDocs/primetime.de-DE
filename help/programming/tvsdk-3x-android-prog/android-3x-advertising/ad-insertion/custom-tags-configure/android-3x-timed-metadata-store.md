---
description: Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.
seo-description: Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.
seo-title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
uuid: 3d0ed022-829d-474e-83a9-152caeb5b317
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden. {#store-timed-metadata-objects-as-they-are-dispatched}

Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.

Beim Analysieren von Inhalten, das vor der Wiedergabe erfolgt, identifiziert TVSDK abonnierte Tags und benachrichtigt Ihre Anwendung über diese Tags.

>[!TIP]
>
>Die Zeit, die jedem `TimedMetadata` zugeordnet ist, ist die Ortszeit in der Wiedergabeschlüssel.

So speichern Sie zeitgesteuerte Metadatenobjekte beim Auslösen:

1. Behalten Sie die aktuelle Wiedergabezeit im Auge.
1. Ordnen Sie die aktuelle Wiedergabezeit den ausgelösten Objekten `TimedMetadata` zu.

1. Verwenden Sie das `TimedMetadata`, wobei die Beginn-Zeit der aktuellen lokalen Wiedergabezeit entspricht.

   Das folgende Beispiel zeigt, wie `TimedMetadata`-Objekte in einem `ArrayList` gespeichert werden.

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

