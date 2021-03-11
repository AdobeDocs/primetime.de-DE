---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# Befehlszeilenverwendung {#command-line-usage}

Verwenden Sie zum Ausführen des Tools die folgende Syntax:

```
java -jar AdobePublisherIDUtility.jar 
<i class="+ topic ph hi-d="" i "="">
 <i class="+ topic ph hi-d="" i "="">
  signaturefile 
  java -jar AdobePublisherIDUtility.jar -s 
  <i class="+ topic ph hi-d="" i "="">
    signingcert
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* 
   * `signaturefile`* gibt den Pfad zur Datei &quot;signatures.xml&quot;der AIR-Anwendung im  [!DNL META-INF] Anwendungsverzeichnis an

* `signingcert` gibt das Zertifikat an, das zum Signieren der AIR-Anwendung verwendet wird

>[!NOTE]
>
>Um die Herausgeber-ID für eine iOS-Anwendung zu ermitteln, verwenden Sie die Option `-s` und geben Sie das Zertifikat an, das zum Signieren der iOS-Anwendung verwendet wird. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die zugriffsgeschützte Inhalte*** wiedergeben können.

