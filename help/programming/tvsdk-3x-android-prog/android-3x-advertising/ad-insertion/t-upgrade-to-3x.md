---
description: Die com.adobe.mediacore.timeline.TimelineMarker -Schnittstelle enthält jetzt eine neue Methode
title: Aktualisieren von 2.5.x Lazy Ad Resolving auf 3.0.0 Lazy Ad Resolving (API-/Workflow-Änderungen)
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Aktualisierung von Lazy Ad Resolving 2.5.x auf Lazy Ad Resolving 3.x (API-/Workflow-Änderungen):{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

Die com.adobe.mediacore.timeline.TimelineMarker -Schnittstelle enthält jetzt eine neue Methode:

**Placement.Type getPlacementType()**

Diese Methode gibt den Platzierungstyp Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL oder Placement.Type.POST_ROLL zurück. Wenn eine Werbeunterbrechung nicht aufgelöst wird, wird die `getDuration()`-Methode in der TimelineMarker-Oberfläche gibt 0 zurück.

>[!NOTE]
>
>Diese Schnittstelle wird nicht immer in den Typ com.mediacore.timeline.advertising.AdBreakTimelineItem umgewandelt, wenn sie noch nicht behoben wurde. Sie kann gegossen werden, wenn die `getDuration()` -Methode der TimelineMarker größer als 0 ist.

**Ereignisänderungen:**

`kEventAdResolutionComplete` wird jetzt abgeschrieben und sofort ausgelöst, nachdem der Player den Status VORBEREITET erreicht hat. Anwendungen, die zuvor nur auf dieses Ereignis gehört haben, um die Scrubbing-Leiste zu zeichnen, sollten dies ändern, um auf `kEventTimelineUpdated` nur. Nachdem einzelne Werbeunterbrechungen behoben wurden, wird ein neuer `kEventTimelineUpdated` -Ereignis ausgelöst wird.
