---
seo-title: Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming
title: Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming
uuid: 83ef8237-0026-4677-b42b-ea4b6de19630
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Bevor Sie den Adobe Primetime DRM-Server für geschütztes Streaming bereitstellen können, müssen Sie die Java- und Tomcat-Versionen wie im Abschnitt &quot;Anforderungen&quot;aufgeführt installiert haben.

Das Primetime-DRM-Server für das geschützte Streaming-Paket enthält [!DNL flashaccesserver.war]. Wenn Sie:

* Möchten Sie diese WAR-Datei bereitstellen, müssen Sie sie in den Ordner [!DNL webapps] von Tomcat kopieren.
* Haben Sie zuvor die WAR-Datei bereitgestellt, müssen Sie möglicherweise den entpackten WAR-Ordner ( [!DNL flashaccessserver] im [!DNL webapps]-Verzeichnis von Tomcat) löschen.

* Soll verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die Datei [!DNL server.xml] im Ordner [!DNL conf] von Tomcat und konfigurieren Sie das `unpackWARs`-Attribut, indem Sie es auf `false` setzen.

>[!NOTE]
>
>Wenn Sie Tomcat so konfiguriert haben, dass er [!DNL commons-logging.jar] in den Systemklasspath einbezieht (nicht erforderlich für den Primetime DRM-Server für geschütztes Streaming), müssen Sie die Befehlsprotokollierung für die Verwendung von Log4J konfigurieren.

Der Server verwendet optional eine plattformspezifische Bibliothek ( [!DNL jsafe.dll] unter Microsoft Windows oder [!DNL libjsafe.so] unter Linux für optimale Leistung. Sie können die entsprechende Plattformbibliothek von [!DNL thirdparty/cryptoj/]*platform* in einen Speicherort kopieren, der durch die Variable `PATH` Umgebung oder `LD_LIBRARY_PATH` unter Linux angegeben wird.

>[!NOTE]
>
>Sie sollten die 64-Bit-Version nur dann verwenden, wenn sowohl das Betriebssystem als auch das JDK 64 Bit unterstützen. Andernfalls müssen Sie die 32-Bit-Version verwenden.

