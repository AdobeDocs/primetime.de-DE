---
title: Erstellen der Referenzimplementierung des BEES
description: Erstellen der Referenzimplementierung des BEES
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Erstellen der Referenzimplementierung des BEES {#build-the-bees-reference-implementation}

Stellen Sie sicher, dass Sie Java 1.6.0_24 oder höher verwenden.
1. Füllen Sie die erforderlichen leeren Pfade aus, z. B. `tomcatdir` und `fasterxmldir` in [!DNL build-bees.xml]

   FasterXML/Jackson ist enthalten. Sie können es auch von herunterladen. [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core).
1. Aktualisieren der tatsächlichen JAR-Dateinamen in [!DNL build.common.xml] , wenn Sie eine andere Version der Jackson-Bibliotheken verwenden möchten.
1. Führen Sie die `all` Zielgruppe [!DNL build-bees.xml]:

   ```
   ant -f build-bees.xml
   ```

Die [!DNL bees.war] wird im [!DNL bees-build/wars] Ordner.
