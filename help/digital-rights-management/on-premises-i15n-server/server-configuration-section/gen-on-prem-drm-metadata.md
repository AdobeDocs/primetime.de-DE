---
seo-title: DRM-Metadaten für "On Premises"erstellen
title: DRM-Metadaten für "On Premises"erstellen
uuid: 89d53924-1a8d-42d4-a716-ce4f4566b6bf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# DRM-Metadaten für &quot;On Premises&quot;erstellen{#generate-the-on-premises-drm-metadata}

Ein [!DNL CreateMetadata.jar] Dienstprogramm ist im [!DNL create_metadata] Ordner enthalten. Der Zweck dieses Dienstprogramms besteht darin, DRM-Metadaten zu &quot;On Premises&quot;zu erstellen, die den Client veranlassen, den Individualisierungsprozess mit dem angegebenen On Premises-Individualisierungsserver durchzuführen.

1. Aktualisieren Sie die Primetime-DRM-Referenzimplementierung - Befehlszeilenwerkzeuge mit den folgenden Dateien:

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

      Die beiden JAR-Dateien können sich im [!DNL Command Line Tools/libs] Ordner befinden. Die [!DNL createMetadata.properties] Datei kann sich neben der [!DNL flashaccesstools.properties] Datei befinden.

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

Es ist ein [!DNL examplecreate.sh] Skript enthalten, das eine Beispielerstellung von Metadaten demonstriert. Konfigurieren Sie vor dem Generieren von Metadaten unbedingt die Lizenzserver-URL und die Individualisierungsserver-URL in den Skript- und Eigenschaftendateien.

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