---
seo-title: Überblick über das Bereitstellen des Adobe Access Server für geschütztes Streaming
title: Überblick über das Bereitstellen des Adobe Access Server für geschütztes Streaming
uuid: 48a7e452-520a-4ff8-97e9-11210221256d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Überblick über das Bereitstellen des Adobe Access Server für geschütztes Streaming {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Before deploying the Adobe Access Server for Protected Streaming, make sure you have installed the versions of Java and Tomcat listed in the Requirements section.

The Adobe Access Server for Protected Streaming package includes [!DNL flashaccesserver.war]. To deploy this WAR file, copy it to Tomcat&#39;s [!DNL webapps] directory. If you have previously deployed the WAR file, you may need to manually delete the unpacked WAR directory ( [!DNL flashaccessserver] in Tomcat&#39;s [!DNL webapps] directory). To prevent Tomcat from unpacking WAR files, edit the [!DNL server.xml] file in Tomcat&#39;s [!DNL conf] directory and set the `unpackWARs` attribute to `false`.

>[!NOTE]
>
>If you have configured Tomcat to include [!DNL commons-logging.jar] on the System classpath (not required for the Adobe Access Server for Protected Streaming), commons-logging must be configured to use Log4J.

The server optionally uses a platform-specific library ( [!DNL jsafe.dll] on Microsoft Windows or [!DNL libjsafe.so] on Linux) for optimal performance. Kopieren Sie die entsprechende Bibliothek für Ihre Plattform von der [!DNL thirdparty/cryptoj/]*Plattform *an einen Speicherort, der durch die Variable &quot;`PATH`Umgebung&quot;(oder`LD_LIBRARY_PATH`unter Linux) angegeben wird.

>[!NOTE]
>
>Die 64-Bit-Version sollte nur verwendet werden, wenn sowohl das Betriebssystem als auch JDK 64-Bit unterstützen, andernfalls die 32-Bit-Version.

