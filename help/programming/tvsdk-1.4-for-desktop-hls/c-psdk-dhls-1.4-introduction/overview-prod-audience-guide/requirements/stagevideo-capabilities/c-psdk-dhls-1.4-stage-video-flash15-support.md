---
description: Ab Flash 15 wird StageVideo, wenn die Hardware-Wiedergabe mit StageVideo nicht verfügbar ist, nahtlos auf ein StageVideo-Softwareobjekt zurückgesetzt.
seo-description: Ab Flash 15 wird StageVideo, wenn die Hardware-Wiedergabe mit StageVideo nicht verfügbar ist, nahtlos auf ein StageVideo-Softwareobjekt zurückgesetzt.
seo-title: Flash 15-Unterstützung für StageVideo
title: Flash 15-Unterstützung für StageVideo
uuid: 49bd8703-016e-4fda-8773-5254d4774ec6
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Flash 15 unterstützt StageVideo{#flash-support-for-stagevideo}

Ab Flash 15 wird StageVideo, wenn die Hardware-Wiedergabe mit StageVideo nicht verfügbar ist, nahtlos auf ein StageVideo-Softwareobjekt zurückgesetzt.

Beachten Sie die folgenden Informationen zum StageVideo-Fallback von Flash 15 auf Software:

* In Ihrer Anwendung sind keine Codeänderungen erforderlich.
* Es ist keine Änderung an TVSDK erforderlich.

   Sie benötigen kein TVSDK-Update, um StageVideo-Fallback zur Software zu verwenden.
* Ihre Anwendungen müssen für Flash 15 neu kompiliert werden.
* Anwendungen, die Sie für Flash 15 neu kompilieren, funktionieren weiterhin mit Flash 14 und früher, sofern diese Anwendungen keine neuen APIs verwenden, die in Flash Player 15 eingeführt wurden.

   Wenn Ihre Flash 14-Anwendung eine neue Flash 15-API verwenden muss, müssen Sie die API mit einer Umwandlung in den Objekttyp dynamisch aufrufen, damit die Anwendung zur Laufzeit nicht in Flash Player 14 fehlschlägt.

## HTML-Überlagerungen {#html-overlays}

In Flash 15 und höher können Sie eine nahtlose Anzeige von HTML-Überlagerungen beibehalten, wenn Hardware-StageVideo nicht mehr verfügbar ist und auf StageVideo zurückfällt. Um diese Funktion zu aktivieren, legen Sie `wmode=opaque` fest.

Einige ältere Browser unterstützen keine Hardwarebeschleunigung. Weitere Informationen zu diesen Anforderungen finden Sie unter [StageVideo-Mindestanforderungen](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). Wenn Sie `wmode=opaque` festlegen, wird das Video mit der Software StageVideo gerendert, was sich auf die Leistung auswirken kann. Normalerweise rendert das Festlegen von `wmode=direct` Videos direkt in GPU, was zu einer wesentlich besseren Leistung führt. Diese Option überschreibt jedoch auch HTML-Überlagerungen.
