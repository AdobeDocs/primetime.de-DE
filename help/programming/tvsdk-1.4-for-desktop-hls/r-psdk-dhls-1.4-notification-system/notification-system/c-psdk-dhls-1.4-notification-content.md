---
description: MediaPlayerNotification stellt Informationen bereit, die sich auf den Status des Players beziehen.
title: Benachrichtigungsinhalt
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Benachrichtigungsinhalt{#notification-content}

MediaPlayerNotification stellt Informationen bereit, die sich auf den Status des Players beziehen.

TVSDK bietet eine chronologische Liste von `MediaPlayerNotification` Benachrichtigungen. Jede Benachrichtigung enthält die folgenden Informationen:

* Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * Typ INFO, WARN oder ERROR
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Benachrichtigung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel-Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Beispiel: ein Schlüssel mit dem Namen `URL` stellt einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf einen anderen `MediaPlayerNotification` -Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen lokal zur späteren Analyse speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.
