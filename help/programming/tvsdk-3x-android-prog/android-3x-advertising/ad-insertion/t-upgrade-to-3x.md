---
description: 'Die com.adobe.mediacore.timeline.TimelineMarker-Schnittstelle enthält jetzt eine neue Methode '
title: 'Aktualisierung von 2.5.x Lazy Ad Resolving auf 3.0.0 Lazy Ad Resolving (API/Workflow-Änderungen) '
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Aktualisierung von 2.5.x Lazy Ad Resolving auf 3.x Lazy Ad Resolving (API/Workflow-Änderungen):{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

Die com.adobe.mediacore.timeline.TimelineMarker-Schnittstelle enthält jetzt eine neue Methode:

**Placement.Type getPlacementType()**

Diese Methode gibt einen Platzierungstyp von Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL oder Placement.Type.POST_ROLL zurück. Wenn eine Werbeunterbrechung ungelöst ist, gibt die `getDuration()`Methode auf der TimelineMarker-Schnittstelle 0 zurück.

>[!NOTE]
>
>Diese Schnittstelle wird nicht immer in den Typ com.mediacore.timeline.advertising.AdBreakTimelineItem umgewandelt, wenn sie noch nicht behoben wurde. Es kann gegossen werden, wenn die `getDuration()`-Methode von TimelineMarker größer als 0 ist.

**Ereignis ändert sich:**

`kEventAdResolutionComplete` wird nun abgeschrieben und wird sofort ausgelöst, nachdem der Spieler den Status VORBEREITET erreicht hat. Anwendungen, die zuvor nur auf dieses Ereignis gehört haben, um die Scrubbing-Leiste zu zeichnen, sollten dies ändern, damit nur `kEventTimelineUpdated` überwacht wird. Nach Auflösung einzelner Werbeunterbrechungen wird ein neues `kEventTimelineUpdated`-Ereignis gesendet.
