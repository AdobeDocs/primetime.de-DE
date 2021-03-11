---
title: Aufbau der Referenzimplementierung von BEES
description: Aufbau der Referenzimplementierung von BEES
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# Erstellen Sie die BEES-Referenzimplementierung {#build-the-bees-reference-implementation}

Stellen Sie sicher, dass Sie Java 1.6.0_24 oder höher verwenden.
1. Füllen Sie die erforderlichen leeren Pfade wie `tomcatdir` und `fasterxmldir` in [!DNL build-bees.xml] aus.

   FasterXML/Jackson ist enthalten. Sie können es auch von [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core) herunterladen.
1. Aktualisieren Sie die tatsächlichen JAR-Dateinamen in [!DNL build.common.xml], wenn Sie eine andere Version der Jackson-Bibliotheken verwenden möchten.
1. Führen Sie die `all`-Zielgruppe von [!DNL build-bees.xml] aus:

   ```
   ant -f build-bees.xml
   ```

Das [!DNL bees.war] wird im Ordner [!DNL bees-build/wars] erstellt.