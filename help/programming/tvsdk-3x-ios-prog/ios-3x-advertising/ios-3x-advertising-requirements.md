---
description: Sie können Anzeigen in Ihre VOD- und Live-/Linearinhalte einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für die Anzeigenentscheidung verwenden.
title: Werbeanforderungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# Werbeanforderungen {#advertising-requirements}

Sie können Anzeigen in Ihre VOD- und Live-/Linearinhalte einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für die Anzeigenentscheidung verwenden.

<!--<a id="section_A2966DC850E140FE9400A1D9E412F819"></a>-->

Die Primetime-Anzeigenentscheidung funktioniert mit TVSDK, um Anzeigenchancen zu identifizieren, Anzeigen zu lösen und gelöste Anzeigen in Ihre Videostreams einzufügen.

Um Anzeigen in Ihren Videoinhalt zu integrieren, stellen Sie sicher, dass die Anzeigen- und Hauptvideoinhalte die folgenden Anforderungen erfüllen:

* Die HLS-Version des Werbeinhalts darf nicht höher sein als die HLS-Version des Hauptinhalts.
* Anzeigen müssen mehrfach geschaltet werden und eine reine Audiowiedergabe enthalten, unabhängig davon, ob der Hauptinhalt mehrfach dargestellt wird.
* Anzeigenplaylisten sollten die gleichen Bitratendarstellungen haben wie die Darstellungen in der Wiedergabeliste für den Hauptinhalt.
* Die Dauer der Zielgruppe und die Dauer der einzelnen Fragmente einer Anzeige dürfen die Zielgruppe des Hauptinhalts nicht überschreiten.
* Wenn der Hauptinhalt einen reinen Audiostream enthält, muss der Werbeinhalt auch einen reinen Audiostream enthalten.
* Wenn der Hauptinhalt Untertitel-Streams enthält, muss der Werbeinhalt unverschlüsselt sein.
* Ist der Hauptinhalt mit einer Bitrate (MBR) versehen, muss der Werbeinhalt auch MBR sein.
* Wenn der Hauptinhalt über alternative Audiospuren verfügt, muss jede Anzeige über mindestens einen reinen Audiostream verfügen.

Wenn die Anzeige nicht über mindestens einen rein audiovisuellen Stream verfügt, wird die Anzeige übersprungen.