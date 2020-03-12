---
description: TVSDK sendet zeitgesteuerte Metadaten-Ereignis und generiert zeitgesteuerte Metadaten, wenn Standard- oder benutzerdefinierte Tags gefunden werden oder sich eine Wiedergabeliste in einem Manifest ändert. Ereignis werden in der Reihenfolge ausgelöst, in der sie im Manifest angezeigt werden.
seo-description: TVSDK sendet zeitgesteuerte Metadaten-Ereignis und generiert zeitgesteuerte Metadaten, wenn Standard- oder benutzerdefinierte Tags gefunden werden oder sich eine Wiedergabeliste in einem Manifest ändert. Ereignis werden in der Reihenfolge ausgelöst, in der sie im Manifest angezeigt werden.
seo-title: Zeitgesteuerte Metadaten-Ereignis
title: Zeitgesteuerte Metadaten-Ereignis
uuid: 69c43701-6ffa-45fe-a104-fe81391222e7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Zeitgesteuerte Metadaten-Ereignis{#timed-metadata-events}

TVSDK sendet zeitgesteuerte Metadaten-Ereignis und generiert zeitgesteuerte Metadaten, wenn Standard- oder benutzerdefinierte Tags gefunden werden oder sich eine Wiedergabeliste in einem Manifest ändert. Ereignis werden in der Reihenfolge ausgelöst, in der sie im Manifest angezeigt werden.

Ihr Player führt Aktionen aus den folgenden Ereignissen durch:

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Wird ausgelöst, wenn eine mit ID3 zeitgesteuerte Metadaten verarbeitet wurde.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Wird ausgelöst, wenn zeitgesteuerte Metadaten verarbeitet wurden und keine Gelegenheit erkannt wurde.

