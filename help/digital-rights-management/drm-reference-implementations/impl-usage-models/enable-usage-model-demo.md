---
title: Demo zum Verwendungsmodell aktivieren
description: Demo zum Verwendungsmodell aktivieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# Demo zum Gebrauchsmodell aktivieren{#enable-the-usage-model-demo}

1. Geben Sie die benutzerdefinierte Eigenschaft `RI_UsageModelDemo=true` zur Verpackungszeit an.

   Wenn Sie Inhalte mit dem Befehlszeilenwerkzeug von Media Packager verpacken, geben Sie Folgendes ein:

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>Wenn Sie den optionalen Demo-Modus nicht während der Paketerstellung aktivieren, gibt der Lizenzserver eine Lizenz aus, die auf der ersten gültigen DRM-Richtlinie basiert, die er verarbeitet.

