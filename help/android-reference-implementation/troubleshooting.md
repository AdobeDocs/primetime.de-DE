---
title: Fehlerbehebung
description: Fehlerbehebung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---


# Fehlerbehebung{#troubleshooting}

* Bei einigen älteren Geräten, auf denen API-Level 10 oder älter ausgeführt wird, kann logcat das Protokollgerät aufgrund eines Berechtigungsproblems nicht öffnen. Die folgende Ausnahme wird angezeigt: `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Problemumgehung:**

   1. Öffnen Sie [!DNL AndroidManifest.xml] unter dem [!DNL CatalogActivity]-Projekt im Arbeitsbereich.

   1. hinzufügen Sie die folgende Berechtigung für die Datei [!DNL `AndroidManfest.xml`]:

      ```
      android.permission.READ_LOGS
      ```
