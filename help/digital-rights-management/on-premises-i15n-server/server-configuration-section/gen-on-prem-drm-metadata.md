---
title: DRM-Metadaten für "On Premises"erstellen
description: DRM-Metadaten für "On Premises"erstellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 1%

---


# DRM-Metadaten für &quot;On Premises&quot;erstellen{#generate-the-on-premises-drm-metadata}

Ein [!DNL CreateMetadata.jar]-Dienstprogramm ist im Ordner [!DNL create_metadata] enthalten. Der Zweck dieses Dienstprogramms besteht darin, DRM-Metadaten zu &quot;On Premises&quot;zu erstellen, die den Client veranlassen, den Individualisierungsprozess mit dem angegebenen On Premises-Individualisierungsserver durchzuführen.

1. Aktualisieren Sie die Primetime-DRM-Referenzimplementierung - Befehlszeilenwerkzeuge mit den folgenden Dateien:

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

      Die beiden JAR-Dateien können sich im Ordner [!DNL Command Line Tools/libs] befinden. Die Datei [!DNL createMetadata.properties] kann sich neben der Datei [!DNL flashaccesstools.properties] befinden.

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

Es ist ein Skript von [!DNL examplecreate.sh] enthalten, das eine Beispielerstellung von Metadaten demonstriert. Konfigurieren Sie vor dem Generieren von Metadaten unbedingt die Lizenzserver-URL und die Individualisierungsserver-URL in den Skript- und Eigenschaftendateien.

Die Eingaben für das Dienstprogramm lauten wie folgt:

* `createMetadata.properties` - Eigenschaftendatei mit einer Standardrichtlinie, Zertifikatspeicherorten und Kennwörtern usw.
* `indivCert` - PKCS12-Datei mit Zertifikat für den Individualisierungstransport
* `indivURL` - URL des On Premises Individualization Servers

Bei der Ausgabedatei handelt es sich um eine DRM-Metadatendatei, die vom DRM-Client verwendet wird. Beispiel:

```
java -jar libs/CreateMetadata.jar -c createMetadata.properties -indivCert i15n_transport.cer
-indivURL https://[YOURINDIVSERVER:PORT] onpremdrm.metadata
```

.