---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# AIR Publisher ID-Dienstprogramm {#air-publisher-id-utility}

Beim Erstellen einer AIR-Datei generiert das AIR Developer Tool (ADT) automatisch eine Herausgeber-ID. Das AIR Publisher ID-Dienstprogramm ( [!DNL AdobePublisherIDUtility.jar]) berechnet die Herausgeber-ID für eine AIR-Anwendung.

Die Herausgeber-ID entspricht dem Zertifikat, das Sie zum Erstellen einer AIR-Datei verwenden. Wenn Sie dasselbe Zertifikat für mehrere AIR-Anwendungen wiederverwenden, haben alle AIR-Anwendungen dieselbe Herausgeber-ID. In einer AIR-Version mit Version 1.5.2 wird die generierte Herausgeber-ID nicht zu einer Datei hinzugefügt. Wenn Sie eine AIR-Anwendungs-Zulassungsliste verwenden möchten, ermitteln Sie daher mit diesem Tool die Herausgeber-ID.

>[!NOTE]
>
>Die Herausgeber-ID, die für die Durchsetzung der AIR-Zulassungsliste verwendet wird, ist nicht die gleiche wie die Herausgeber-ID, die der Herausgeber der Anwendung im Abschnitt [!DNL application.xml] -Datei.

## Befehlszeilenverwendung des AIR Publisher ID-Dienstprogramms {#air-publisher-id-utility-command-line-usage}

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

* `signaturefile` gibt einen Pfad zum AIR-Programm an. [!DNL signatures.xml] -Datei in den Anwendungen [!DNL META-INF] directory

* `signingcert` gibt das Zertifikat an, das zum Signieren einer AIR-Anwendung verwendet wird

>[!NOTE]
>
>Um die Herausgeber-ID für eine Android-Anwendung zu ermitteln, müssen Sie die `-s` -Option, um das Zertifikat anzugeben, das zum Signieren des Android-Anwendungspakets (APK) verwendet wird. Primetime DRM ist erforderlich, um Android-Anwendungen zu erstellen, die Primetime-DRM-geschützte Inhalte wiedergeben können.
