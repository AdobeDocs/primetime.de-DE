---
title: Demo des Nutzungsmodells aktivieren
description: Demo des Nutzungsmodells aktivieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Demo des Nutzungsmodells aktivieren{#enable-the-usage-model-demo}

1. Festlegen der benutzerdefinierten Eigenschaft `RI_UsageModelDemo=true` zum Zeitpunkt der Verpackung.

   Wenn Sie Inhalte mit dem Befehlszeilen-Tool Media Packager verpacken, geben Sie Folgendes ein:

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>Wenn Sie den optionalen Demo-Modus nicht während der Verpackung aktivieren, stellt der Lizenzserver eine Lizenz basierend auf der ersten gültigen DRM-Richtlinie aus, die er verarbeitet.
