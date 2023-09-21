---
title: Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming
description: Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Bevor Sie den Adobe Primetime DRM-Server für geschütztes Streaming bereitstellen können, müssen Sie die Java- und Tomcat-Versionen installiert haben, die im Abschnitt Anforderungen aufgeführt sind.

Der Primetime-DRM-Server für das geschützte Streaming-Paket umfasst [!DNL flashaccesserver.war]. Wenn Sie:

* Wenn Sie diese WAR-Datei bereitstellen möchten, müssen Sie sie in die Datei von Tomcat kopieren. [!DNL webapps] Verzeichnis.
* Haben Sie die WAR-Datei bereits bereitgestellt, müssen Sie möglicherweise das entpackte WAR-Verzeichnis ( [!DNL flashaccessserver] in Tomcat [!DNL webapps] Verzeichnis).

* Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die [!DNL server.xml] -Datei in Tomcat [!DNL conf] und konfigurieren Sie `unpackWARs` Attribut durch Festlegen von `false`.

>[!NOTE]
>
>Wenn Sie Tomcat so konfiguriert haben, dass [!DNL commons-logging.jar] im Systemklasspath (nicht erforderlich für den Primetime DRM-Server für geschütztes Streaming) müssen Sie die gemeinsame Protokollierung für die Verwendung von Log4J konfigurieren.

Der Server verwendet optional eine plattformspezifische Bibliothek ( [!DNL jsafe.dll] unter Microsoft Windows oder [!DNL libjsafe.so] auf Linux für optimale Leistung. Sie können die entsprechende Bibliothek für Ihre Plattform aus kopieren. [!DNL thirdparty/cryptoj/]*platform* an einen Ort, der durch die Variable `PATH` Umgebungsvariable oder `LD_LIBRARY_PATH` auf Linux.

>[!NOTE]
>
>Sie sollten die 64-Bit-Version nur verwenden, wenn sowohl das Betriebssystem als auch das JDK 64-Bit unterstützen. Ansonsten müssen Sie die 32-Bit-Version verwenden.
