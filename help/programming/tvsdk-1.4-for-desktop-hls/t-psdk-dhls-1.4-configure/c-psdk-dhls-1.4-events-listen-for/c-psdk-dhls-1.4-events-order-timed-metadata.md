---
description: TVSDK sendet zeitgesteuerte Metadaten-Ereignisse und generiert zeitgesteuerte Metadaten, sobald standardmäßige oder benutzerdefinierte Tags auftreten oder sich eine Wiedergabeliste in einem Manifest ändert. Ereignisse werden in der Reihenfolge gesendet, in der sie im Manifest angezeigt werden.
title: Zeitgesteuerte Metadaten-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Zeitgesteuerte Metadaten-Ereignisse{#timed-metadata-events}

TVSDK sendet zeitgesteuerte Metadaten-Ereignisse und generiert zeitgesteuerte Metadaten, sobald standardmäßige oder benutzerdefinierte Tags auftreten oder sich eine Wiedergabeliste in einem Manifest ändert. Ereignisse werden in der Reihenfolge gesendet, in der sie im Manifest angezeigt werden.

Ihr Player implementiert Aktionen basierend auf den folgenden Ereignissen:

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Wird ausgelöst, wenn eine zeitgesteuerte ID3-Metadaten verarbeitet wurde.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Wird ausgelöst, wenn zeitgesteuerte Metadaten verarbeitet wurden und keine Gelegenheit erkannt wurde.
