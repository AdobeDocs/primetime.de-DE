---
description: TVSDK sendet zeitgesteuerte Metadaten-Ereignis und generiert zeitgesteuerte Metadaten, wenn Standard- oder benutzerdefinierte Tags gefunden werden oder sich eine Wiedergabeliste in einem Manifest ändert. Ereignis werden in der Reihenfolge ausgelöst, in der sie im Manifest angezeigt werden.
title: Zeitgesteuerte Metadaten-Ereignis
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# Zeitgesteuerte Metadaten-Ereignis{#timed-metadata-events}

TVSDK sendet zeitgesteuerte Metadaten-Ereignis und generiert zeitgesteuerte Metadaten, wenn Standard- oder benutzerdefinierte Tags gefunden werden oder sich eine Wiedergabeliste in einem Manifest ändert. Ereignis werden in der Reihenfolge ausgelöst, in der sie im Manifest angezeigt werden.

Ihr Player führt Aktionen aus den folgenden Ereignissen durch:

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Wird ausgelöst, wenn eine mit ID3 zeitgesteuerte Metadaten verarbeitet wurde.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Wird ausgelöst, wenn zeitgesteuerte Metadaten verarbeitet wurden und keine Gelegenheit erkannt wurde.

