---
title: Fehlerbehebung
description: Fehlerbehebung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---

# Fehlerbehebung{#troubleshooting}

* Bei einigen älteren Geräten mit API-Stufe 10 oder älter kann logcat das Protokollgerät aufgrund eines Berechtigungsproblems nicht öffnen. Die folgende Ausnahme wird angezeigt: `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Problemumgehung:**

   1. Öffnen [!DNL AndroidManifest.xml] unter [!DNL CatalogActivity] Projekt im Arbeitsbereich.

   1. Fügen Sie die folgende Berechtigung zum [!DNL `AndroidManfest.xml`] Datei:

      ```
      android.permission.READ_LOGS
      ```
