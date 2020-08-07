---
seo-title: Deploying the Adobe Primetime DRM Server for Protected Streaming
title: Deploying the Adobe Primetime DRM Server for Protected Streaming
uuid: 83ef8237-0026-4677-b42b-ea4b6de19630
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Deploying the Adobe Primetime DRM Server for Protected Streaming{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Before you can deploy the Adobe Primetime DRM Server for Protected Streaming, you must have installed the versions of Java and Tomcat as listed in the Requirements topic.

The Primetime DRM Server for Protected Streaming package includes [!DNL flashaccesserver.war]. If you:

* Want to deploy this WAR file, you need to copy it to Tomcat&#39;s [!DNL webapps] directory.
* Have previously deployed the WAR file, you may need to delete the unpacked WAR directory ( [!DNL flashaccessserver] in Tomcat&#39;s [!DNL webapps] directory).

* Soll verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die [!DNL server.xml] Datei im [!DNL conf] Verzeichnis von Tomcat und konfigurieren Sie das `unpackWARs` Attribut, indem Sie es auf `false`.

>[!NOTE]
>
>If you have configured Tomcat to include [!DNL commons-logging.jar] on the System classpath (not required for the Primetime DRM Server for Protected Streaming) then you must configure commons-logging to use Log4J.

The server optionally uses a platform-specific library ( [!DNL jsafe.dll] on Microsoft Windows or [!DNL libjsafe.so] on Linux for optimal performance. You can copy the appropriate library for your platform from [!DNL thirdparty/cryptoj/]*platform *to a location that is specified by the`PATH`environment variable or`LD_LIBRARY_PATH`on Linux.

>[!NOTE]
>
>Sie sollten die 64-Bit-Version nur dann verwenden, wenn sowohl das Betriebssystem als auch das JDK 64 Bit unterstützen. Andernfalls müssen Sie die 32-Bit-Version verwenden.

