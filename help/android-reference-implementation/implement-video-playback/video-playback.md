---
title: Grundlegende Vorgänge bei der Videowiedergabe
description: Der PlaybackManager bietet wesentliche Vorgänge für das HLS-Streaming
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# Grundlegende Vorgänge der Videowiedergabe {#essential-operations-of-video-playback}

Der PlaybackManager bietet wesentliche Vorgänge für das HLS-Streaming:

* Ruft den [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html) auf, der auf Video-Ereignis angemessen reagieren kann.
* Bietet Wiedergabevorgang wie &quot;Abspielen&quot;, &quot;Anhalten&quot;und &quot;Suchen&quot;.
* Gibt Informationen zum Player zurück, z. B. Player-Status, Wiedergabefeld und den Live-Stream des Videos.
* Bestimmt, ob ABR aktiviert ist, und legt die ABR- und Puffersteuerungsparameter je nach den bereitgestellten Konfigurationsdaten fest.
* Bestimmt, ob die Puffersteuerung aktiviert ist, und legt die Parameter für die Puffersteuerung je nach den bereitgestellten Konfigurationsdaten fest.