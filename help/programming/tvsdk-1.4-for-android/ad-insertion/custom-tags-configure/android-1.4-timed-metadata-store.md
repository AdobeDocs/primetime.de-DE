---
description: Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.
seo-description: Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.
seo-title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
title: Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden
uuid: 0e6d2a42-37a8-477e-b925-66bbc23445c1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Speichern Sie zeitgesteuerte Metadatenobjekte, während sie gesendet werden {#store-timed-metadata-objects-as-they-are-dispatched}

Ihre Anwendung muss die entsprechenden TimedMetadata-Objekte zu den richtigen Zeiten verwenden.

Beim Analysieren von Inhalten, das vor der Wiedergabe erfolgt, identifiziert TVSDK abonnierte Tags und benachrichtigt Ihre Anwendung über diese Tags. Die jeweils zugehörige Zeit `TimedMetadata` ist die Ortszeit auf der Wiedergabeschlüssel.

Ihr Antrag muss die folgenden Aufgaben abschließen:

1. Behalten Sie die aktuelle Wiedergabezeit im Auge.
1. Ordnen Sie die aktuelle Wiedergabezeit den ausgelösten `TimedMetadata` Objekten zu.

1. Verwenden Sie die `TimedMetadata` Zeitangabe des Beginns mit der aktuellen lokalen Wiedergabezeit.

   Das folgende Beispiel zeigt, wie `TimedMetadata` Objekte in einem gespeichert werden `ArrayList`.

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

