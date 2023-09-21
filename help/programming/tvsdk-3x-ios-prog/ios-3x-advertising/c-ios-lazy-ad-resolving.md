---
description: Das Auflösen von Anzeigen und Laden von Anzeigen kann zu einer inakzeptablen Verzögerung für einen Benutzer führen, der auf den Start der Wiedergabe wartet. Die Funktion "Lazy Ad Loading Resolving"kann diese Startverzögerung reduzieren. Anzeigen können jetzt in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst werden. Dies wird durch die Verwendung eines dualen Player-Ansatzes erreicht.
title: Just-in-Time-Anzeigenauflösung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Just-in-Time-Anzeigenauflösung {#just-in-time-ad-resolving}

Das Auflösen von Anzeigen und Laden von Anzeigen kann zu einer inakzeptablen Verzögerung für einen Benutzer führen, der auf den Start der Wiedergabe wartet. Die Funktion &quot;Lazy Ad Loading Resolving&quot;kann diese Startverzögerung reduzieren. Anzeigen können jetzt in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst werden. Dies wird durch die Verwendung eines dualen Player-Ansatzes erreicht.

**Grundlegender Prozess zur Anzeigenauflösung und zum Laden:**

1. TVSDK lädt ein Manifest (Wiedergabeliste) herunter und *auflöst* alle Anzeigen.
1. TVSDK *lädt* alle Anzeigen und fügt die Anzeigensegmente in die Manifeste ein.
1. TVSDK verschiebt den Player in den Status VORBEREITT , und die Wiedergabe des Inhalts beginnt.

Der Player verwendet die URLs im Manifest, um den Anzeigeninhalt (kreative Inhalte) zu erhalten, stellt sicher, dass der Anzeigeninhalt in einem Format vorliegt, das TVSDK wiedergeben kann, und TVSDK platziert die Anzeigen auf der Timeline. Dieser grundlegende Prozess der Auflösung und des Ladens von Anzeigen kann dazu führen, dass ein Benutzer, der darauf wartet, seinen Inhalt wiederzugeben, unannehmbar lange verzögert ist, insbesondere wenn das Manifest mehrere Anzeigen-URLs enthält.

**Lazy Ad Resolving:**

1. TVSDK lädt die Wiedergabeliste herunter.
1. TVSDK *löst und lädt* Alle Pre-Roll-Anzeigen verschieben den Player in den Status VORBEREITET , und die Inhaltswiedergabe beginnt.
1. TVSDK *auflöst* Jede Anzeige unterbricht vor ihrer Position basierend auf dem Wert, der in `PTAdMetadata::delayAdLoadingTolerance`.

Zum Beispiel standardmäßig `delayAdLoadingTolerance` auf 5 Sekunden eingestellt ist. Wenn eine AdBreak für 3:00 Uhr festgelegt ist, wird sie mit 2 aufgelöst:55:00 Sie können diesen Wert erhöhen, wenn Sie glauben, dass Ihre Anzeigenauflösung länger als 5 Sekunden dauert.

>[!IMPORTANT]
>
>**Faktoren, die bei der verzögerten Anzeigenauflösung berücksichtigt werden sollten:**
>* Die verzögerte Anzeigenauflösung wird nur für VOD-Streams mit den Modi SERVER_MAP-Anzeigensignalisierungsmodus unterstützt.
>* Die verzögerte Anzeigenauflösung ist standardmäßig nicht aktiviert. Sie müssen `PTAdMetadata::delayAdLoading` = JA , um es zu aktivieren.
>* Die verzögerte Anzeigenauflösung ist mit der Funktion &quot;Instant On&quot;nicht kompatibel. Weitere Informationen zu Instant On finden Sie unter [Sofort aktiviert](../../tvsdk-3x-ios-prog/ios-3x-instant-on-ios.md).
>* Der Modus Bild-im-Bild wird bei verzögerter Anzeigenauflösung nicht unterstützt. Deaktivieren Sie alle Bild-im-Bild-Modi, wenn Sie Lazy Ad Resolving aktivieren.
>* Eine verzögerte Anzeigenauflösung wirkt sich nicht auf Pre-Roll-Anzeigen aus.
>
**Verzögertes Auflösen von Anzeigen aktivieren**

Sie können die Funktion &quot;Lazy Ad Resolving&quot;mithilfe des vorhandenen Lazy Ad Loading-Mechanismus aktivieren oder deaktivieren (Lazy Ad Resolving ist standardmäßig deaktiviert).

Sie können die verzögerte Anzeigenauflösung aktivieren, indem Sie `PTAdMetadata::delayAdLoading`= JA beim Einrichten Ihrer Anzeigenmetadaten.

**Für verzögerte Anzeigenauflösung relevante APIs:**

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
