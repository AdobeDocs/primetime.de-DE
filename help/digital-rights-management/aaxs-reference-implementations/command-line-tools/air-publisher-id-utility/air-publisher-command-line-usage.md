---
seo-title: Befehlszeilenverwendung
title: Befehlszeilenverwendung
uuid: 54b1e867-c6cc-4355-b8e6-a7ec910bd33d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
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
>Um die Herausgeber-ID für eine iOS-Anwendung zu ermitteln, verwenden Sie die Option `-s` und geben Sie das Zertifikat an, das zum Signieren der iOS-Anwendung verwendet wird. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die zugriffsgeschützte Inhalte*** abspielen können.

