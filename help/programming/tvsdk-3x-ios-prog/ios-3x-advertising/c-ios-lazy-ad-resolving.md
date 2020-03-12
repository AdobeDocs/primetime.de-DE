---
description: Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktion "Auflösen von verzögerten Anzeigen"kann diese Startverzögerung verringern. Anzeigen können nun in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst werden. Dies wird durch den Einsatz eines dualen Player-Ansatzes erreicht.
seo-description: Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktion "Auflösen von verzögerten Anzeigen"kann diese Startverzögerung verringern. Anzeigen können nun in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst werden. Dies wird durch den Einsatz eines dualen Player-Ansatzes erreicht.
seo-title: Just-in-time-Anzeigenauflösung
title: Just-in-time-Anzeigenauflösung
uuid: f7b20439-3604-4d69-bdfe-2e0ad26f495b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Just-in-time-Anzeigenauflösung {#just-in-time-ad-resolving}

Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktion &quot;Auflösen von verzögerten Anzeigen&quot;kann diese Startverzögerung verringern. Anzeigen können nun in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst werden. Dies wird durch den Einsatz eines dualen Player-Ansatzes erreicht.

**Grundlegender Prozess zum Auflösen und Laden von Anzeigen:**

1. TVSDK lädt ein Manifest (Playlist) herunter und löst *alle Anzeigen* auf.
1. TVSDK *lädt* alle Anzeigen und fügt die Anzeigensegmente in die Manifeste ein.
1. TVSDK verschiebt den Player in den Status &quot;VORBEREITT&quot;, und die Wiedergabe des Inhalts beginnt.

Der Player verwendet die URLs im Manifest, um den Anzeigeninhalt (kreative Elemente) abzurufen, stellt sicher, dass der Anzeigeninhalt in einem Format vorliegt, das TVSDK wiedergeben kann, und TVSDK platziert die Anzeigen auf der Zeitleiste. Dieser grundlegende Prozess des Auflösens und Ladens von Anzeigen kann zu einer unannehmbar langen Verzögerung für Benutzer führen, die auf die Wiedergabe ihres Inhalts warten, insbesondere wenn das Manifest mehrere Anzeigen-URLs enthält.

**Lazy Ad Resolving:**

1. TVSDK lädt die Wiedergabeliste herunter.
1. TVSDK *löst alle Pre-Roll-Anzeigen auf und lädt* sie, verschiebt den Player in den Status &quot;VORBEREITT&quot;und beginnt mit der Inhaltswiedergabe.
1. TVSDK *löst* jede Werbeunterbrechung vor der Position auf Grundlage des in `PTAdMetadata::delayAdLoadingTolerance`definierten Werts auf.

Beispielsweise `delayAdLoadingTolerance` ist die Standardeinstellung auf 5 Sekunden eingestellt. Wenn AdBreak auf die Wiedergabe um 3:00 Uhr eingestellt ist, wird es um 2:55:00 Uhr aufgelöst. Sie können diesen Wert erhöhen, wenn Sie glauben, dass Ihre Anzeigenauflösung länger als 5 Sekunden dauern wird.

>[!IMPORTANT]
>
>**Faktoren, die bei der Auflösung von Lazy Ad zu berücksichtigen sind:**
>* Lazy Ad Resolving wird nur für VOD-Streams mit den Modi SERVER_MAP Anzeigensignalisierung unterstützt.
>* Die verzögerte Anzeigenauflösung ist nicht standardmäßig aktiviert. Sie müssen `PTAdMetadata::delayAdLoading` = YES einstellen, um es zu aktivieren.
>* Die verzögerte Anzeigenauflösung ist nicht mit der Funktion &quot;Sofortiges Anzeigen&quot;kompatibel. Weitere Informationen zu &quot;Sofort ein&quot;finden Sie unter &quot; [Sofort ein](../../tvsdk-3x-ios-prog/ios-3x-instant-on-ios.md)&quot;.
>* Der Bild-in-Bild-Modus wird bei der Auflösen von Lazy-Anzeigen nicht unterstützt. Bitte deaktivieren Sie alle Bild-in-Bild-Modi, wenn Sie Lazy Ad Resolving aktivieren.
>* Eine verzögerte Anzeigenauflösung wirkt sich nicht auf Pre-Roll-Anzeigen aus.
>


**Verzögerte Anzeigenauflösung aktivieren**

Sie können die Funktion &quot;Lazy Ad Resolving&quot;über den vorhandenen Lazy Ad Loading Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig deaktiviert).

Sie können die Option &quot;Lazy Ad Resolving&quot;aktivieren, indem Sie beim Einrichten Ihrer Anzeigenmetadaten `PTAdMetadata::delayAdLoading`= YES einstellen.

**APIs für verzögerte Anzeigenauflösung:**

```
Class:    PTAdMetadata 
Properties: 
  
/** 
 * Property to define whether ad break resolution must be delayed until after stream start or not. 
 * When this value is NO, ads are resolved before stream start and spliced into the content when possible allowing  
   for a seamless playback experience. 
 * When this value is YES, ads are displayed in a secondary video player instance and resolved lazily only when  
   needed. 
 * Default value is NO 
 */ 
@property (nonatomic, assign) BOOL delayAdLoading; 
  
/** 
 * Property to define the lookahead for ad break resolution.  Ad breaks will be resolved when they occur between  
   the playhead time and the specified tolerance. 
 * If set to zero, the ad will be resolved immediately before playing the ad.  This may cause a slight delay in the  
   playback of the ads. 
 * Default value is 5.0 or 5 seconds. 
 */ 
  
@property (nonatomic, assign) NSTimeInterval delayAdLoadingTolerance;
```
