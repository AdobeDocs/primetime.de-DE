---
seo-title: Grundlegende Vorgänge bei der Videowiedergabe
title: Grundlegende Vorgänge bei der Videowiedergabe
description: Der PlaybackManager bietet wesentliche Vorgänge für das HLS-Streaming
seo-description: Der PlaybackManager bietet wesentliche Vorgänge für das HLS-Streaming
uuid: 7ac93f1f-9233-4462-a4be-528d1aa524a9
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Grundlegende Vorgänge bei der Videowiedergabe {#essential-operations-of-video-playback}

Der PlaybackManager bietet wesentliche Vorgänge für das HLS-Streaming:

* Ruft den [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)auf, der auf Video-Ereignis angemessen reagieren kann.
* Bietet Wiedergabevorgang wie &quot;Abspielen&quot;, &quot;Anhalten&quot;und &quot;Suchen&quot;.
* Gibt Informationen zum Player zurück, wie z. B. Player-Status, Wiedergabefeld und Live-Stream des Videos.
* Bestimmt, ob ABR aktiviert ist, und legt die ABR- und Puffersteuerungsparameter je nach den bereitgestellten Konfigurationsdaten fest.
* Bestimmt, ob die Puffersteuerung aktiviert ist, und legt die Parameter für die Puffersteuerung je nach den bereitgestellten Konfigurationsdaten fest.