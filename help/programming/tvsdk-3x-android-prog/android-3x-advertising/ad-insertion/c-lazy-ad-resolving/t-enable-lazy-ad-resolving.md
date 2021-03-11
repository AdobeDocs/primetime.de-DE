---
description: Sie können die Funktion "Lazy Ad Resolving"über den vorhandenen Lazy Ad Loading Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig deaktiviert).
keywords: Verzögert;Anzeigen auflösen;Laden der Anzeige;VerzögerungLaden
title: Verzögerte Anzeigenauflösung aktivieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


# Verzögerte Anzeigenauflösung {#enable-lazy-ad-resolving} aktivieren

Sie können die Funktion &quot;Lazy Ad Resolving&quot;über den vorhandenen Lazy Ad Loading Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig deaktiviert).

Sie können die Lazy Ad Resolving aktivieren oder deaktivieren, indem Sie [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) mit true oder false aufrufen.

* Verwenden Sie die booleschen *hasDelayAdLoading*- und *setDelayAdLoading*-Methoden in AdvertisingMetadata, um die zeitliche Steuerung der Anzeigenauflösung und die Platzierung der Anzeigen auf der Zeitleiste zu steuern:

   * Wenn *hasDelayAdLoading* &quot;false&quot;zurückgibt, wartet TVSDK, bis alle Anzeigen aufgelöst und platziert wurden, bevor zum Status &quot;PREPARED&quot;gewechselt wird.
   * Wenn *hasDelayAdLoading* &quot;true&quot;zurückgibt, löst TVSDK nur die ersten Anzeigen und Transitionen in den Status &quot;VORBEREITET&quot;auf.

      * Die verbleibenden Anzeigen werden während der Wiedergabe aufgelöst und platziert.
   * Wenn *hasPreroll *oder *hasLivePreroll* false zurückgibt, geht TVSDK davon aus, dass es keine Preroll-Anzeige gibt und Beginn sofort die Wiedergabe des Inhalts durchführen. Diese sind standardmäßig auf true eingestellt.


**APIs für verzögerte Anzeigenauflösung:**

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

Um Anzeigen als Hinweise auf einer Scrubbing-Leiste genau wiederzugeben, sollten Sie auf das `TimelineEvent`Ereignis achten und die Scrubbing-Leiste jedes Mal neu zeichnen, wenn Sie dieses Ereignis erhalten.

Wenn &quot;Verzögerte Anzeigenauflösung&quot;für VOD-Streams aktiviert ist, werden alle Werbeunterbrechungen auf der Zeitleiste platziert. Viele Werbeunterbrechungen werden jedoch noch nicht behoben. Die Anwendung kann bestimmen, ob diese Marker gezeichnet werden sollen, indem Sie `TimelineMarker::getDuration()` aktivieren. Wenn der Wert größer als null ist, wurden die Anzeigen innerhalb der Werbeunterbrechung aufgelöst.

TVSDK löst dieses Ereignis aus, wenn eine Werbeunterbrechung aufgelöst wurde und der Player in den Status &quot;VORBEREITT&quot;Transition wird.

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
