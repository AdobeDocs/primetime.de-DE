---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# Befehlszeilenverwendung {#command-line-usage}

Verwenden Sie die folgende Syntax, um das Tool auszuführen:

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

* `signaturefile` gibt den Pfad zur Datei signatures.xml der AIR-Anwendung an, die sich in den Anwendungen befindet [!DNL META-INF] directory

* `signingcert` gibt das Zertifikat an, das zum Signieren der AIR-Anwendung verwendet wird

>[!NOTE]
>
>Um die Herausgeber-ID für eine iOS-Anwendung zu ermitteln, verwenden Sie die `-s` und geben Sie das Zertifikat an, das zum Signieren der iOS-Anwendung verwendet wird. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die zugriffsgeschützte Inhalte wiedergeben können***.
