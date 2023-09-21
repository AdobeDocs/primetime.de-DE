---
title: DRM-Metadaten für On-Premises generieren
description: DRM-Metadaten für On-Premises generieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# DRM-Metadaten für On-Premises generieren{#generate-the-on-premises-drm-metadata}

A [!DNL CreateMetadata.jar] -Dienstprogramm ist im [!DNL create_metadata] Ordner. Der Zweck dieses Dienstprogramms besteht darin, DRM-Metadaten für On-Premises zu erstellen, die den Client zur Durchführung des Individualisierungsprozesses mit dem angegebenen On-Premises-Individualisierungsserver veranlassen.

1. Aktualisieren Sie die Primetime DRM Reference Implementation - Command Line Tools mit den folgenden Dateien:

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

     Die beiden JAR-Dateien können sich im [!DNL Command Line Tools/libs] Ordner. Die [!DNL createMetadata.properties] -Datei kann sich neben der [!DNL flashaccesstools.properties] -Datei.

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

enthalten ist eine [!DNL examplecreate.sh] -Skript, das eine Beispielerstellung von Metadaten demonstriert. Stellen Sie sicher, dass Sie die Lizenzserver-URL und die URL des Individualisierungsservers in den Skript- und Eigenschaftendateien konfigurieren, bevor Sie versuchen, Metadaten zu generieren.

Die Eingaben für das Dienstprogramm lauten wie folgt:

* `createMetadata.properties` - Eigenschaftendatei mit einer Standardrichtlinie, Zertifikatspeicherorten und Kennwörtern usw.
* `indivCert` - PKCS12-Datei mit Zertifikat für den Individualisierungs-Transport
* `indivURL` - URL des On-Premises-Individualisierungsservers

Die Ausgabedatei ist eine DRM-Metadatendatei für On-Premises, die vom DRM-Client verwendet wird. Beispiel:

```
java -jar libs/CreateMetadata.jar -c createMetadata.properties -indivCert i15n_transport.cer
-indivURL https://[YOURINDIVSERVER:PORT] onpremdrm.metadata
```

.
