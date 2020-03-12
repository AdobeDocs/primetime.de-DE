---
description: Wenn ab Flash 15 kein Hardware-Rendering mit StageVideo verfügbar ist, wird StageVideo nahtlos auf ein StageVideo-Softwareobjekt zurückgesetzt.
seo-description: Wenn ab Flash 15 kein Hardware-Rendering mit StageVideo verfügbar ist, wird StageVideo nahtlos auf ein StageVideo-Softwareobjekt zurückgesetzt.
seo-title: Flash 15-Unterstützung für StageVideo
title: Flash 15-Unterstützung für StageVideo
uuid: 49bd8703-016e-4fda-8773-5254d4774ec6
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Flash 15-Unterstützung für StageVideo{#flash-support-for-stagevideo}

Wenn ab Flash 15 kein Hardware-Rendering mit StageVideo verfügbar ist, wird StageVideo nahtlos auf ein StageVideo-Softwareobjekt zurückgesetzt.

Beachten Sie die folgenden Informationen zum Flash 15 StageVideo-Fallback zur Software:

* In Ihrer Anwendung sind keine Codeänderungen erforderlich.
* Es ist keine Änderung an TVSDK erforderlich.

   Sie benötigen kein TVSDK-Update, um StageVideo-Fallback zur Software zu verwenden.
* Ihre Anwendungen müssen für Flash 15 neu kompiliert werden.
* Anwendungen, die Sie für Flash 15 neu kompilieren, funktionieren weiterhin mit Flash 14 und früher, solange diese Anwendungen keine neuen APIs verwenden, die in Flash Player 15 eingeführt wurden.

   Wenn Ihre Flash 14-Anwendung eine neue Flash 15-API verwenden muss, müssen Sie die API dynamisch mit einer Umwandlung in den Objekttyp aufrufen, damit die Anwendung zur Laufzeit in Flash Player 14 nicht fehlschlägt.

## HTML-Überlagerungen {#html-overlays}

In Flash 15 und höher können Sie eine nahtlose Anzeige von HTML-Überlagerungen beibehalten, wenn die Hardware StageVideo nicht mehr verfügbar ist und auf StageVideo zurückfällt. Um diese Funktion zu aktivieren, legen Sie sie fest `wmode=opaque`.

Einige ältere Browser unterstützen keine Hardwarebeschleunigung. Weitere Informationen zu diesen Anforderungen finden Sie unter [StageVideo-Mindestanforderungen](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). Wenn Sie `wmode=opaque`das Video einstellen, wird es mit der Software StageVideo gerendert, was sich auf die Leistung auswirken kann. Normalerweise wird Video durch `wmode=direct` direkte Einstellung in GPU gerendert, was zu einer wesentlich besseren Leistung führt. Diese Option überschreibt jedoch auch HTML-Überlagerungen.
