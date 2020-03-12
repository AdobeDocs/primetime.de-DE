---
description: MediaPlayerNotification stellt Informationen bereit, die sich auf den Status des Players beziehen.
seo-description: MediaPlayerNotification stellt Informationen bereit, die sich auf den Status des Players beziehen.
seo-title: Benachrichtigungsinhalt
title: Benachrichtigungsinhalt
uuid: c2321a49-1b60-4e44-b8e2-a023b764d779
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Benachrichtigungsinhalt{#notification-content}

MediaPlayerNotification stellt Informationen bereit, die sich auf den Status des Players beziehen.

TVSDK stellt eine chronologische Liste der `MediaPlayerNotification` Benachrichtigungen bereit. Jede Benachrichtigung enthält die folgenden Informationen:

* Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * Typ INFO, WARN oder FEHLER
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Anmeldung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel/Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Ein Schlüssel mit dem Namen `URL` stellt beispielsweise einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf ein anderes `MediaPlayerNotification` Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen zur späteren Analyse lokal speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.
