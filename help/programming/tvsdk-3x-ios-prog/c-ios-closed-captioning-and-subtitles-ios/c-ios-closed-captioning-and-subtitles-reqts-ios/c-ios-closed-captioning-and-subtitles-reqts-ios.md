---
description: Untertitel und Untertitel weisen einige einzigartige Unterschiede auf und ermöglichen die Aktivierung auf unterschiedliche Weise.
title: Anforderungen an Untertitel und Untertitel
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
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