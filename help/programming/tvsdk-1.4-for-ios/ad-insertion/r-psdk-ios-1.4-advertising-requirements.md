---
description: 'null'
seo-description: 'null'
seo-title: Werbeanforderungen
title: Werbeanforderungen
uuid: 60e299df-4f42-455a-8983-8964f7a197e1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Werbeanforderungen {#advertising-requirements}

Sie können Anzeigen in Ihre VOD- und Live-/Linearinhalte einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für die Anzeigenentscheidung verwenden.

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