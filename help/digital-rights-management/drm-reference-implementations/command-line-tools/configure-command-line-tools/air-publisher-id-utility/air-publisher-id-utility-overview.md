---
seo-title: Übersicht
title: Übersicht
uuid: f45c6b58-53c5-41e0-be3d-590231dd214a
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# AIR Publisher-ID-Dienstprogramm {#air-publisher-id-utility}

Beim Erstellen einer AIR-Datei generiert das AIR Developer Tool (ADT) automatisch eine Herausgeber-ID. Das AIR Publisher-ID-Dienstprogramm ( [!DNL AdobePublisherIDUtility.jar]) berechnet die Herausgeber-ID für eine AIR-Anwendung.

Die Herausgeber-ID ist eindeutig für das Zertifikat, mit dem Sie eine AIR-Datei erstellen. Wenn Sie dasselbe Zertifikat für mehrere AIR-Anwendungen wiederverwenden, haben alle AIR-Anwendungen dieselbe Herausgeber-ID. In einer AIR-Version, die auf Version 1.5.2 folgt, wird die generierte Herausgeber-ID keiner Datei hinzugefügt. Wenn Sie daher eine zulassungsliste einer AIR-Anwendung verwenden möchten, verwenden Sie dieses Tool, um die Herausgeber-ID zu ermitteln.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Die Herausgeber-ID, die für die Durchsetzung der AIR-zulassungsliste verwendet wird, ist nicht mit der Herausgeber-ID identisch, die der Anwendungsherausgeber in der [!DNL application.xml] Anwendungsdatei angegeben hat.

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
   * `signaturefile`* gibt einen Pfad zur [!DNL signatures.xml] Datei der AIR-Anwendung an, die sich im Anwendungsverzeichnis befindet [!DNL META-INF]

* `signingcert` gibt das Zertifikat an, das zum Signieren einer AIR-Anwendung verwendet wird

>[!NOTE]
>
>Um die Herausgeber-ID für eine Android-Anwendung zu ermitteln, müssen Sie mit der `-s` Option das Zertifikat angeben, das zum Signieren des Android-Anwendungspakets (APK) verwendet wird. Primetime DRM ist erforderlich, um Android-Anwendungen zu erstellen, die Primetime-DRM-geschützte Inhalte wiedergeben können.