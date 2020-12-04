---
description: Untertitel und Untertitel weisen einige einzigartige Unterschiede auf und ermöglichen die Aktivierung auf unterschiedliche Weise.
seo-description: Untertitel und Untertitel weisen einige einzigartige Unterschiede auf und ermöglichen die Aktivierung auf unterschiedliche Weise.
seo-title: Anforderungen an Untertitel und Untertitel
title: Anforderungen an Untertitel und Untertitel
uuid: 18ed6ac1-4b25-4590-8c61-3ffb0464d093
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---


# Anforderungen für Untertitel und Untertitel {#requirements-for-subtitles-and-closed-captions}

Untertitel und Untertitel weisen einige einzigartige Unterschiede auf und ermöglichen die Aktivierung auf unterschiedliche Weise.

Untertitelstreams werden parallel zum Hauptinhalt ausgeführt. Untertitel sind Teil der Datenpakete der MPEG-2-Videostreams.

Für Untertitel und Untertitel sollten Sie die folgenden Anforderungen beachten:

* **Untertitel**

   * Untertitel sind in der Regel in derselben Sprache wie die Audiodaten und stellen Hintergrundgeräusche als Text dar.
   * Untertitel sind Teil der Datenpakete der MPEG-2-Videostreams im Videoübertragungsstream.
   * Untertitel werden in dem durch das AV Foundation-Framework bereitgestellten Umfang unterstützt.

* **Untertitel**

   * Untertitel sind in der Regel in einer anderen Sprache und enthalten keine Hintergrundgeräusche.
   * Untertitel befinden sich in Streams, die parallel zum Hauptinhalt ausgeführt werden.

      Das `PTMediaPlayer` gibt den Hauptinhalt und die Anzeigen wieder, wobei der Hauptinhalt live/linear oder VOD sein könnte und Anzeigen Pre-Roll, Mid-Roll oder Post-Roll sein könnten.
   Hier einige zusätzliche Anforderungen für Untertitel in iOS:

   * Bei Zeitstempeln muss der Wert `X-TIMESTAMP-MAP`, der im Kopfzeilenabschnitt der Datei `WebVTT` angegeben ist, mit dem Video-Zeitstempel übereinstimmen.

   * Für das System müssen Sie iOS 6.1 oder höher verwenden.


>[!IMPORTANT]
>
>Die Anforderungen für Untertitel gelten nicht für Untertitel.