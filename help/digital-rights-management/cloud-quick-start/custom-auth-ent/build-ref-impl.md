---
seo-title: Aufbau der Referenzimplementierung von BEES
title: Aufbau der Referenzimplementierung von BEES
uuid: c9358188-e626-4f99-a02c-4928b06d6ae2
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Aufbau der Referenzimplementierung von BEES {#build-the-bees-reference-implementation}

Stellen Sie sicher, dass Sie Java 1.6.0_24 oder höher verwenden.
1. Füllen Sie die erforderlichen leeren Pfade aus, z. B. `tomcatdir` und `fasterxmldir` in [!DNL build-bees.xml]

   FasterXML/Jackson ist enthalten. Sie können es auch unter [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core)herunterladen.
1. Aktualisieren Sie die tatsächlichen JAR-Dateinamen in, [!DNL build.common.xml] wenn Sie eine andere Version der Jackson-Bibliotheken verwenden möchten.
1. Führen Sie die `all` Zielgruppe aus [!DNL build-bees.xml]:

   ```
   ant -f build-bees.xml
   ```

Die [!DNL bees.war] wird im [!DNL bees-build/wars] Ordner erstellt.