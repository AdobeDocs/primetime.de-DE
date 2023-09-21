---
description: Sie können Anzeigen in Ihren VOD- und Live-/Linearinhalt einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für Anzeigenentscheidungen verwenden.
title: Werbeanforderungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Werbeanforderungen {#advertising-requirements}

Sie können Anzeigen in Ihren VOD- und Live-/Linearinhalt einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für Anzeigenentscheidungen verwenden.

<!--<a id="section_A2966DC850E140FE9400A1D9E412F819"></a>-->

Die Primetime-Anzeigenentscheidung funktioniert mit TVSDK, um Anzeigengelegenheiten zu identifizieren, Anzeigen aufzulösen und gelöste Anzeigen in Ihre Video-Streams einzufügen.

Um Anzeigen in Ihren Videoinhalt zu integrieren, stellen Sie sicher, dass die Werbung und der Hauptvideoinhalt die folgenden Anforderungen erfüllen:

* Die HLS-Version des Werbeinhalts kann nicht höher sein als die HLS-Version des Hauptinhalts.
* Anzeigen müssen durch Multiplexing gekennzeichnet sein und eine Nur-Audio-Darstellung enthalten, unabhängig davon, ob der Hauptinhalt durch Multiplexing gekennzeichnet ist.
* Anzeigenwiedergaben sollten dieselbe Bitrate aufweisen wie die Wiedergaben in der Wiedergabeliste für Hauptinhalte.
* Die Zieldauer und die Dauer einzelner Fragmente einer Anzeige können die Zieldauer des Hauptinhalts nicht überschreiten.
* Wenn der Hauptinhalt einen reinen Audio-Stream enthält, muss der Werbeinhalt auch einen Nur-Audio-Stream enthalten.
* Wenn der Hauptinhalt Untertitel-Streams enthält, muss der Werbeinhalt unverschlüsselt sein.
* Wenn der Hauptinhalt eine Bitrate (MBR) ist, muss der Werbeinhalt auch MBR sein.
* Wenn der Hauptinhalt über alternative Audiospuren verfügt, muss jede Anzeige über mindestens einen reinen Audiostream verfügen oder die Anzeigen sollten demuliert werden. Wenn die Anzeige weder über mindestens einen Nur-Audio-Stream noch über eine Demo verfügt, wird die Anzeige übersprungen.
