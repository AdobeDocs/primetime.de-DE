---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
exl-id: 67056085-beb5-4f54-8962-369bc32d7907
source-git-commit: 79cab347d0daa01549fbf8a9b37bf0a91c14648e
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

* `signaturefile` gibt den Pfad zur Datei &quot;signatures.xml&quot;der AIR-Anwendung an, die sich in den Anwendungen befindet [!DNL META-INF] directory

* `signingcert` gibt das Zertifikat an, das zum Signieren der AIR-Anwendung verwendet wird

>[!NOTE]
>
>Um die Herausgeber-ID für eine iOS-Anwendung zu ermitteln, verwenden Sie die `-s` und geben Sie das Zertifikat an, das zum Signieren der iOS-Anwendung verwendet wird. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die zugriffsgeschützte Inhalte wiedergeben können.***.
