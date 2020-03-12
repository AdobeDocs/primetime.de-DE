---
seo-title: Befehlszeilenverwendung
title: Befehlszeilenverwendung
uuid: 54b1e867-c6cc-4355-b8e6-a7ec910bd33d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

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
   * `signaturefile`* gibt den Pfad zur Datei &quot;signatures.xml&quot;der AIR-Anwendung im Anwendungsverzeichnis an [!DNL META-INF]

* `signingcert` gibt das Zertifikat an, das zum Signieren der AIR-Anwendung verwendet wird

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Um die Herausgeber-ID für eine iOS-Anwendung zu ermitteln, verwenden Sie die `-s` Option und geben Sie das Zertifikat an, das zum Signieren der iOS-Anwendung verwendet wird. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die zugriffsgeschützte Inhalte*** wiedergeben können.

