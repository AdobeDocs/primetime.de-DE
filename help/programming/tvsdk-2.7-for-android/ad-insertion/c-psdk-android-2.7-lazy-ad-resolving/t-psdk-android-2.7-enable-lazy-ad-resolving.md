---
description: Sie können die Funktion "Lazy Ad Resolving"mithilfe des vorhandenen Lazy Ad Loading-Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig aktiviert).
keywords: Lazy;Ad Resolving;Ad Loading;delayLoading
title: Verzögertes Auflösen von Anzeigen aktivieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Verzögertes Auflösen von Anzeigen aktivieren {#enable-lazy-ad-resolving}

Sie können die Funktion &quot;Lazy Ad Resolving&quot;mithilfe des vorhandenen Lazy Ad Loading-Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig aktiviert).

Sie können die verzögerte Anzeigenauflösung aktivieren oder deaktivieren, indem Sie [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) mit `true` oder `false`.

1. Verwenden des Booleschen `hasDelayAdLoading` und `setDelayAdLoading` Methoden in `AdvertisingMetadata` zur Steuerung des Timings der Anzeigenauflösung und der Platzierung von Anzeigen in der Timeline:

   * Wenn `hasDelayAdLoading` gibt &quot;false&quot;zurück, wartet TVSDK, bis alle Anzeigen aufgelöst und platziert wurden, bevor zum Status VORBEREITET übergegangen wird.
   * Wenn `hasDelayAdLoading` gibt &quot;true&quot;zurück, löst TVSDK nur die ersten Anzeigen und Übergänge in den Status VORBEREITT auf. Die verbleibenden Anzeigen werden während der Wiedergabe aufgelöst und platziert.
   * Wann `hasPreroll` oder `hasLivePreroll` return false, TVSDK geht davon aus, dass es keine Pre-oll-Anzeige gibt, und startet sofort die Wiedergabe des Inhalts. Die Standardeinstellung lautet &quot;true&quot;.

     Für verzögerte Anzeigenauflösung relevante APIs:

     ```
     Class: 
        com.adobe.mediacore.metadata.AdvertisingMetadata 
     
     Methods: 
     […] 
         public final boolean hasDelayAdLoading() // Check if Lazy Ad Resolving enabled 
         public final void setDelayAdLoading()    // Enable or disable Lazy Ad Resolving 
         public final boolean hasPreroll()        // Check for existence of pre-roll ads 
         public final void setPreroll()           // Set pre-roll true or false 
         public final boolean hasLivePreroll()    // Check for live pre-roll ads 
         public final void setLivePreroll()       // Set live pre-roll true or false 
     […]
     ```

1. Um Anzeigen als Hinweise auf einer Scrubbing-Leiste genau wiederzugeben, sollten Sie auf die `TimelineEvent` -Ereignis und zeichnen Sie die Scrub-Leiste jedes Mal neu, wenn Sie dieses Ereignis erhalten.

   Wenn die verzögerte Anzeigenauflösung für VOD-Streams aktiviert ist, werden nicht alle Anzeigen auf der Timeline platziert, wenn Ihr Player in den Status &quot;VORBEREITET&quot;wechselt. Daher muss Ihr Player die Scrubbing-Leiste explizit neu zeichnen.

   TVSDK optimiert den Versand dieses Ereignisses, um die Häufigkeit zu minimieren, mit der Sie die Scrubbing-Leiste neu zeichnen müssen. Daher hängt die Anzahl der Timeline-Ereignisse nicht mit der Anzahl der Werbeunterbrechungen zusammen, die auf der Timeline platziert werden sollen. Wenn Sie beispielsweise fünf Werbeunterbrechungen haben, erhalten Sie möglicherweise nicht genau fünf Ereignisse.

   ```java
   mediaPlayer.addEventListener 
       (MediaPlayerEvent.TIMELINE_UPDATED, timelineUpdatedEventListener); 
   /** 
    * ... 
    */ 
   public void onTimelineUpdated(TimelineEvent event) { 
   
       for (PlaybackManagerEventListener listener : eventListeners) { 
           listener.onUpdate(getLocalSeekRange(), event.getTimeline()); 
       } 
   } 
   ```

>Rufen Sie auf, um zu überprüfen, ob die Funktion zur verzögerten Anzeigenauflösung aktiviert oder deaktiviert ist. `AdvertisingMetadata.hasDelayAdLoading`. Ein Rückgabewert von `true` bedeutet, dass die verzögerte Anzeigenauflösung aktiviert ist; `false` bedeutet, dass die Funktion deaktiviert ist.
