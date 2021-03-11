---
description: MediaPlayerNotification stellt Informationen bereit, die sich auf den Status des Players beziehen.
title: Benachrichtigungsinhalt
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Benachrichtigungsinhalt{#notification-content}

MediaPlayerNotification stellt Informationen bereit, die sich auf den Status des Players beziehen.

TVSDK stellt eine chronologische Liste der `MediaPlayerNotification`-Benachrichtigungen bereit. Jede Benachrichtigung enthält die folgenden Informationen:

* Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * Typ INFO, WARN oder FEHLER
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Anmeldung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel/Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Beispielsweise stellt ein Schlüssel mit dem Namen `URL` einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf ein anderes  `MediaPlayerNotification` Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen zur späteren Analyse lokal speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.
