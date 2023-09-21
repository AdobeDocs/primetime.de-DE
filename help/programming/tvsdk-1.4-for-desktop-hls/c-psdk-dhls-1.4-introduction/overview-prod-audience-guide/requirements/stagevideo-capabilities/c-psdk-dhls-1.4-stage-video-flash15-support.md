---
description: Wenn ab Flash 15 kein Hardware-Rendering mit StageVideo verfügbar ist, kehrt StageVideo nahtlos zu einem StageVideo-Softwareobjekt zurück.
title: Flash 15-Unterstützung für StageVideo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Flash 15-Unterstützung für StageVideo{#flash-support-for-stagevideo}

Wenn ab Flash 15 kein Hardware-Rendering mit StageVideo verfügbar ist, kehrt StageVideo nahtlos zu einem StageVideo-Softwareobjekt zurück.

Beachten Sie die folgenden Informationen zum Flash 15 StageVideo-Fallback zur Software:

* In Ihrer Anwendung sind keine Codeänderungen erforderlich.
* Es ist keine Änderung am TVSDK erforderlich.

  Sie benötigen kein TVSDK-Update, um StageVideo-Fallback für Software zu verwenden.
* Ihre Applikationen müssen für Flash 15 neu kompiliert werden.
* Anwendungen, die Sie für Flash 15 neu kompilieren, funktionieren weiterhin mit Flash 14 und früher, solange diese Anwendungen keine neuen APIs verwenden, die in Flash Player 15 eingeführt wurden.

  Wenn Ihre Flash 14-Anwendung eine neue Flash 15-API verwenden muss, müssen Sie die API dynamisch mit einer Umwandlung in den Objekttyp aufrufen, damit die Anwendung zur Laufzeit in Flash Player 14 nicht fehlschlägt.

## HTML-Überlagerungen {#html-overlays}

In Flash 15 und höher können Sie eine nahtlose Anzeige von HTML-Überlagerungen gewährleisten, wenn die Hardware StageVideo nicht mehr verfügbar ist und auf StageVideo zurückfällt. Um diese Funktion zu aktivieren, legen Sie `wmode=opaque`.

Einige ältere Browser unterstützen keine Hardwarebeschleunigung. Weitere Informationen zu diesen Anforderungen finden Sie unter [Mindestanforderungen für StageVideo](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). Wenn Sie `wmode=opaque`, wird das Video mit der Software StageVideo gerendert, was sich auf die Leistung auswirken kann. In der Regel wird `wmode=direct` rendert Videos direkt an GPU, was zu einer deutlich besseren Leistung führt. Diese Option überschreibt jedoch auch HTML-Überlagerungen.
