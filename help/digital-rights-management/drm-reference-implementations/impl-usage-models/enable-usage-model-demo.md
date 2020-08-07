---
seo-title: Demo zum Verwendungsmodell aktivieren
title: Demo zum Verwendungsmodell aktivieren
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# Demo zum Verwendungsmodell aktivieren{#enable-the-usage-model-demo}

1. Geben Sie die benutzerdefinierte Eigenschaft `RI_UsageModelDemo=true` zur Verpackungszeit an.

   Wenn Sie Inhalte mit dem Befehlszeilenwerkzeug von Media Packager verpacken, geben Sie Folgendes ein:

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>Wenn Sie den optionalen Demo-Modus nicht während der Paketerstellung aktivieren, gibt der Lizenzserver eine Lizenz aus, die auf der ersten gültigen DRM-Richtlinie basiert, die er verarbeitet.

