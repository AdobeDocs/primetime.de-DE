---
description: Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.
seo-description: Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.
seo-title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
uuid: 0d0ddfea-6f32-467d-91bc-f18ceadcd842
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
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

