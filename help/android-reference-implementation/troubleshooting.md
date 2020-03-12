---
seo-title: Fehlerbehebung
title: Fehlerbehebung
uuid: b7a41ea7-86c5-442c-b751-86a9055c5e35
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Fehlerbehebung{#troubleshooting}

* Bei einigen älteren Geräten, auf denen API-Level 10 oder älter ausgeführt wird, kann logcat das Protokollgerät aufgrund eines Berechtigungsproblems nicht öffnen. Die folgende Ausnahme wird angezeigt: `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Problemumgehung:**

   1. Öffnen Sie [!DNL AndroidManifest.xml] im Arbeitsbereich unter dem [!DNL CatalogActivity] Projekt.

   1. Hinzufügen Sie die folgende Berechtigung für die [!DNL `AndroidManfest.xml`] Datei:

      ```
      android.permission.READ_LOGS
      ```
