---
description: Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.
title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden. {#store-timed-metadata-objects-as-they-are-dispatched}

Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.

Beim Analysieren von Inhalten, das vor der Wiedergabe erfolgt, identifiziert TVSDK abonnierte Tags und benachrichtigt Ihre Anwendung über diese Tags. Die Zeit, die jedem `TimedMetadata` zugeordnet ist, ist die Ortszeit in der Wiedergabeschlüssel.

Ihr Antrag muss die folgenden Aufgaben abschließen:

1. Behalten Sie die aktuelle Wiedergabezeit im Auge.
1. Ordnen Sie die aktuelle Wiedergabezeit den ausgelösten Objekten `TimedMetadata` zu.

1. Verwenden Sie das `TimedMetadata`, wobei die Beginn-Zeit der aktuellen lokalen Wiedergabezeit entspricht.

   Das folgende Beispiel zeigt, wie `TimedMetadata`-Objekte in einem `ArrayList` gespeichert werden.

   ```java
   private List<TimedMetadata> _timedMetadataList = new ArrayList<TimedMetadata>(); 
   ... 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       ... 
       if (timedMetadata.getName().equalsIgnoreCase("#EXT-X-CUE"))  { 
           _timedMetadataList.add(timedMetadata); 
       } 
       ... 
   }
   ```

