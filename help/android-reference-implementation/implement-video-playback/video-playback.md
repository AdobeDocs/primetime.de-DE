---
title: Grundlegende Vorgänge der Videowiedergabe
description: Der PlaybackManager bietet wichtige Vorgänge des HLS-Streaming.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Grundlegende Vorgänge der Videowiedergabe {#essential-operations-of-video-playback}

Der PlaybackManager bietet wichtige Vorgänge des HLS-Streaming:

* Ruft die [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html), die angemessen auf Videoereignisse reagieren kann.
* Bietet Wiedergabevorgang wie Wiedergabe, Pause und Suchen.
* Gibt Informationen zum Player zurück, z. B. Player-Status, Wiedergabefeld und Live-Stream des Videos.
* Bestimmt, ob ABR aktiviert ist, und legt die ABR- und Puffersteuerungsparameter entsprechend den bereitgestellten Konfigurationsdaten fest.
* Bestimmt, ob die Puffersteuerung aktiviert ist, und legt die Parameter der Puffersteuerung entsprechend den bereitgestellten Konfigurationsdaten fest.
