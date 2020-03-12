---
seo-title: Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming
title: Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming
uuid: 83ef8237-0026-4677-b42b-ea4b6de19630
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Bereitstellen des Adobe Primetime DRM-Servers für geschütztes Streaming{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Bevor Sie Adobe Primetime DRM Server für geschütztes Streaming bereitstellen können, müssen Sie die Java- und Tomcat-Versionen wie im Abschnitt &quot;Anforderungen&quot;aufgeführt installiert haben.

Das Primetime DRM Server for Protected Streaming-Paket enthält [!DNL flashaccesserver.war]. Wenn Sie:

* Wenn Sie diese WAR-Datei bereitstellen möchten, müssen Sie sie in das [!DNL webapps] Verzeichnis von Tomcat kopieren.
* Sie haben zuvor die WAR-Datei bereitgestellt, müssen Sie möglicherweise den entpackten WAR-Ordner ( [!DNL flashaccessserver] im [!DNL webapps] Verzeichnis von Tomcat) löschen.

* Soll verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die [!DNL server.xml] Datei im [!DNL conf] Verzeichnis von Tomcat und konfigurieren Sie das `unpackWARs` Attribut, indem Sie es auf `false`.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Wenn Sie Tomcat so konfiguriert haben, dass er [!DNL commons-logging.jar] in den Systemklasspath eingeschlossen wird (nicht erforderlich für den Primetime DRM-Server für geschütztes Streaming), müssen Sie die Befehlsprotokollierung für die Verwendung von Log4J konfigurieren.

Der Server verwendet optional eine plattformspezifische Bibliothek ( [!DNL jsafe.dll] unter Microsoft Windows oder [!DNL libjsafe.so] unter Linux), um eine optimale Leistung zu erzielen. Sie können die entsprechende Bibliothek für Ihre Plattform von der [!DNL thirdparty/cryptoj/]*Plattform *an einen Speicherort kopieren, der durch die Variable &quot;`PATH`Umgebung&quot;oder`LD_LIBRARY_PATH`unter Linux angegeben wird.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Sie sollten die 64-Bit-Version nur dann verwenden, wenn sowohl das Betriebssystem als auch das JDK 64 Bit unterstützen. Andernfalls müssen Sie die 32-Bit-Version verwenden.

