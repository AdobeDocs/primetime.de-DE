---
title: Übersicht
description: Übersicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# AIR-Herausgeber-ID-Dienstprogramm {#air-publisher-id-utility}

Beim Erstellen einer AIR-Datei generiert das AIR Developer Tool (ADT) automatisch eine Herausgeber-ID. Das AIR Publisher-ID-Dienstprogramm ( [!DNL AdobePublisherIDUtility.jar]) berechnet die Herausgeber-ID für eine AIR-Anwendung.

Die Herausgeber-ID ist eindeutig für das Zertifikat, mit dem Sie eine AIR-Datei erstellen. Wenn Sie dasselbe Zertifikat für mehrere AIR-Anwendungen wiederverwenden, haben alle AIR-Anwendungen dieselbe Herausgeber-ID. In einer AIR-Version, die auf Version 1.5.2 folgt, wird die generierte Herausgeber-ID keiner Datei hinzugefügt. Wenn Sie daher eine AIR-Anwendungs-Zulassungsliste verwenden möchten, verwenden Sie dieses Tool, um die Herausgeber-ID zu ermitteln.

>[!NOTE]
>
>Die Herausgeber-ID, die für die Durchsetzung der AIR-Zulassungsliste verwendet wird, ist nicht mit der Herausgeber-ID identisch, die der Anwendungsherausgeber in der Anwendungsdatei [!DNL application.xml] angegeben hat.

## Befehlszeilenverwendung des AIR Publisher-ID-Dienstprogramms {#air-publisher-id-utility-command-line-usage}

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
   * `signaturefile`* gibt einen Pfad zur  [!DNL signatures.xml] Datei der AIR-Anwendung an, die sich im  [!DNL META-INF] Anwendungsordner befindet.

* `signingcert` gibt das Zertifikat an, das zum Signieren einer AIR-Anwendung verwendet wird

>[!NOTE]
>
>Um die Herausgeber-ID für eine Android-Anwendung zu ermitteln, müssen Sie die Option `-s` verwenden, um das Zertifikat anzugeben, mit dem das Android-Anwendungspaket (APK) signiert wird. Primetime DRM ist erforderlich, um Android-Anwendungen zu erstellen, die Primetime-DRM-geschützte Inhalte wiedergeben können.