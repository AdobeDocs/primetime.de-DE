---
description: Sie können die Funktion "Lazy Ad Resolving"über den vorhandenen Lazy Ad Loading Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig aktiviert).
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: Sie können die Funktion "Lazy Ad Resolving"über den vorhandenen Lazy Ad Loading Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig aktiviert).
seo-title: Verzögerte Anzeigenauflösung aktivieren
title: Verzögerte Anzeigenauflösung aktivieren
uuid: a084ee0b-53af-4600-91f6-d30ccc89699d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Verzögerte Anzeigenauflösung aktivieren {#enable-lazy-ad-resolving}

Sie können die Funktion &quot;Lazy Ad Resolving&quot;über den vorhandenen Lazy Ad Loading Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig aktiviert).

Sie können die Lazy Ad Resolving aktivieren oder deaktivieren, indem Sie [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) mit `true` oder `false`aufrufen.

1. Verwenden Sie die booleschen `hasDelayAdLoading` und `setDelayAdLoading` Methoden, `AdvertisingMetadata` um die zeitliche Steuerung der Anzeigenauflösung und die Platzierung der Anzeigen in der Zeitleiste zu steuern:

   * Wenn &quot;false&quot; `hasDelayAdLoading` zurückgegeben wird, wartet TVSDK, bis alle Anzeigen aufgelöst und platziert wurden, bevor zum Status &quot;PREPARED&quot;gewechselt wird.
   * Wenn &quot;true&quot; `hasDelayAdLoading` zurückgegeben wird, löst TVSDK nur die ersten Anzeigen und Transitionen in den Status &quot;VORBEREITT&quot;auf. Die verbleibenden Anzeigen werden während der Wiedergabe aufgelöst und platziert.
   * Wenn `hasPreroll` oder `hasLivePreroll` &quot;false&quot;zurückgegeben wird, geht TVSDK davon aus, dass es keine Preroll-Anzeige gibt und Beginn die Inhaltswiedergabe sofort durchführen. Die Standardeinstellung lautet true.

      APIs für verzögerte Anzeigenauflösung:

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

1. Um Anzeigen als Hinweise auf einer Scrubbing-Leiste genau wiederzugeben, sollten Sie auf das `TimelineEvent` Ereignis achten und die Scrubbing-Leiste jedes Mal neu zeichnen, wenn Sie dieses Ereignis erhalten.

   Wenn die Option &quot;Lazy Ad Resolving&quot;für VOD-Streams aktiviert ist, werden nicht alle Anzeigen auf der Zeitleiste platziert, wenn Ihr Player in den Status &quot;PREPARED&quot;wechselt. Daher muss Ihr Player die Scrubbing-Leiste explizit neu zeichnen.

   TVSDK optimiert den Versand dieses Ereignisses, um die Anzahl der Male zu minimieren, die Sie die Scrubbing-Leiste neu zeichnen müssen. Daher steht die Anzahl der Zeitschienen-Ereignis nicht in Zusammenhang mit der Anzahl der Werbeunterbrechungen, die auf der Zeitschiene platziert werden sollen. Wenn Sie beispielsweise fünf Werbeunterbrechungen haben, erhalten Sie möglicherweise nicht genau fünf Ereignis.

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

>Rufen Sie `AdvertisingMetadata.hasDelayAdLoading`an, um zu überprüfen, ob die Funktion zum Auflösen von Lazy-Anzeigen aktiviert oder deaktiviert ist. Ein Rückgabewert von `true` bedeutet, dass &quot;Lazy Ad Resolving&quot;aktiviert ist; `false` bedeutet, dass die Funktion deaktiviert ist.

