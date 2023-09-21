---
description: Geschlossene Untertitel weisen einige eindeutige Unterschiede auf und ermöglichen sie auf unterschiedliche Weise.
title: Untertitel und geschlossene Untertitel
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Anforderungen an Untertitel und geschlossene Untertitel {#requirements-for-subtitles-and-closed-captions}

Geschlossene Untertitel weisen einige eindeutige Unterschiede auf und ermöglichen sie auf unterschiedliche Weise.

Untertitel-Streams werden parallel zum Hauptinhalt ausgeführt. Geschlossene Untertitel sind Teil der Datenpakete der MPEG-2-Videostreams.

Beachten Sie die folgenden Anforderungen für Untertitel und Untertitel:

* **Geschlossene Untertitel**

   * Geschlossene Untertitel sind in der Regel in derselben Sprache wie das Audio und stellen Hintergrundgeräusche als Text dar.
   * Geschlossene Untertitel sind Teil der Datenpakete der MPEG-2-Videostreams im Videoübertragungsstream.
   * Geschlossene Untertitel werden in dem durch das AV Foundation-Framework bereitgestellten Umfang unterstützt.

* **Untertitel**

   * Untertitel sind in der Regel in einer anderen Sprache und enthalten keine Hintergrundgeräusche.
   * Untertitel befinden sich in Streams, die parallel zum Hauptinhalt ausgeführt werden.

     Die `PTMediaPlayer` gibt den Hauptinhalt und die Anzeigen wieder, wobei der Hauptinhalt live/linear oder VOD sein kann und Anzeigen Pre-Roll, Mid-Roll oder Post-Roll sein können.

  Im Folgenden finden Sie einige zusätzliche Anforderungen für Untertitel in iOS:

   * Bei Zeitstempeln wird die `X-TIMESTAMP-MAP` -Wert, der im Kopfzeilenabschnitt des `WebVTT` -Datei, muss mit dem Video-Zeitstempel übereinstimmen.

   * Für das System müssen Sie iOS 6.1 oder höher verwenden.

>[!IMPORTANT]
>
>Die Anforderungen an Untertitel gelten nicht für geschlossene Untertitel.
