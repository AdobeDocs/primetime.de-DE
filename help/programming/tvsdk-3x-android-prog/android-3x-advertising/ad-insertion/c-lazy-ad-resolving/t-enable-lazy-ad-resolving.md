---
description: Sie können die Funktion "Lazy Ad Resolving"mithilfe des vorhandenen Lazy Ad Loading-Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig deaktiviert).
keywords: Lazy;Ad Resolving;Ad Loading;delayLoading
title: Verzögertes Auflösen von Anzeigen aktivieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Verzögertes Auflösen von Anzeigen aktivieren {#enable-lazy-ad-resolving}

Sie können die Funktion &quot;Lazy Ad Resolving&quot;mithilfe des vorhandenen Lazy Ad Loading-Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig deaktiviert).

Sie können die verzögerte Anzeigenauflösung aktivieren oder deaktivieren, indem Sie [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) mit &quot;true&quot;oder &quot;false&quot;.

* Verwenden des Booleschen *hasDelayAdLoading* und *setDelayAdLoading* -Methoden in AdvertisingMetadata, um den Zeitpunkt der Anzeigenauflösung und die Platzierung von Anzeigen in der Timeline zu steuern:

   * Wenn *hasDelayAdLoading* gibt &quot;false&quot;zurück, wartet TVSDK, bis alle Anzeigen aufgelöst und platziert wurden, bevor zum Status VORBEREITET übergegangen wird.
   * Wenn *hasDelayAdLoading* gibt &quot;true&quot;zurück, löst TVSDK nur die ersten Anzeigen und Übergänge in den Status VORBEREITT auf.

      * Die verbleibenden Anzeigen werden während der Wiedergabe aufgelöst und platziert.

   * Wenn *hasPreroll *oder *hasLivePreroll* return false, TVSDK geht davon aus, dass es keine Pre-oll-Anzeige gibt, und startet sofort die Wiedergabe des Inhalts. Diese sind standardmäßig auf &quot;true&quot;gesetzt.

**Für verzögerte Anzeigenauflösung relevante APIs:**

```
Class:    com.adobe.mediacore.metadata.AdvertisingMetadata 
Methods: 
    public final boolean hasDelayAdLoading() // Check if Lazy Ad Resolving enabled 
    public final void setDelayAdLoading() // Enable or disable Lazy Ad Resolving 
    public final void setDelayAdLoadingTolerance() // Sets the Lazy Ad Resolving Tolerance level.  This value is added to the BufferControlParameters::playBufferTime and the content's EXT-X-TARGETDURATION to determine when ad breaks should resolve 
    public final double getDelayAdLoadingTolerance() // Gets the Lazy Ad Resolving Tolerance level 
    public final boolean hasPreroll() // Check for existence of pre-roll ads 
    public final void setPreroll() // Set pre-roll true or false 
    public final boolean hasLivePreroll() // Check for live pre-roll ads 
    public final void setLivePreroll() // Set live pre-roll true or false

Class:     com.adobe.mediacore.timeline.TimelineMarker 
Methods: 
    public double getDuration() // Returns the current duration of the TimelineMarker.  This will be zero if the ad break has not yet resolved. 
    public Placement.Type getPlacementType() // Returns whether
```

Um Anzeigen als Hinweise auf einer Scrubbing-Leiste genau wiederzugeben, sollten Sie auf die `TimelineEvent`-Ereignis und zeichnen Sie die Scrub-Leiste jedes Mal neu, wenn Sie dieses Ereignis erhalten.

Wenn die verzögerte Anzeigenauflösung für VOD-Streams aktiviert ist, werden alle Werbeunterbrechungen auf der Timeline platziert. Viele Werbeunterbrechungen werden jedoch noch nicht behoben. Die Anwendung kann bestimmen, ob diese Markierungen gezeichnet werden sollen, indem sie die `TimelineMarker::getDuration()`. Wenn der Wert größer als null ist, wurden die Anzeigen innerhalb der Werbeunterbrechung aufgelöst.

TVSDK löst dieses Ereignis aus, wenn eine Werbeunterbrechung aufgelöst wurde und der Player in den Status VORBEREITT wechselt.

```
mediaPlayer.addEventListener(MediaPlayerEvent.TIMELINE_UPDATED, timelineUpdatedEventListener); 
/** 
* ... 
*/ 
public void onTimelineUpdated(TimelineEvent event) { 
for (PlaybackManagerEventListener listener : eventListeners) { 
  listener.onUpdate(getLocalSeekRange(), event.getTimeline()); 
}
```
