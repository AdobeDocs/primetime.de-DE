---
seo-title: Demo zum Verwendungsmodell aktivieren
title: Demo zum Verwendungsmodell aktivieren
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Demo zum Verwendungsmodell aktivieren{#enable-the-usage-model-demo}

1. Geben Sie die benutzerdefinierte Eigenschaft `RI_UsageModelDemo=true` zur Verpackungszeit an.

   Wenn Sie Inhalte mit dem Befehlszeilenwerkzeug von Media Packager verpacken, geben Sie Folgendes ein:

   ```
   java -jar AdobeMediaPackager.jar [
   
<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true

```
>[!NOTE] {class="- topic/note "}
>
>If you do not activate the optional demo mode at packaging time, the license server issues a license based on the first valid DRM policy it processes.

