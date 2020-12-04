---
description: 'Die com.adobe.mediacore.timeline.TimelineMarker-Schnittstelle enthält jetzt eine neue Methode '
seo-description: 'Die com.adobe.mediacore.timeline.TimelineMarker-Schnittstelle enthält jetzt eine neue Methode '
seo-title: 'Aktualisierung von 2.5.x Lazy Ad Resolving auf 3.0.0 Lazy Ad Resolving (API/Workflow-Änderungen) '
title: 'Aktualisierung von 2.5.x Lazy Ad Resolving auf 3.0.0 Lazy Ad Resolving (API/Workflow-Änderungen) '
uuid: 5870ceb4-93a8-4c8b-b716-673396122644
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '176'
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
