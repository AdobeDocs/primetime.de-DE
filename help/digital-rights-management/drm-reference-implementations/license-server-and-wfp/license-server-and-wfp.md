---
description: The reference implementation server can help you create a fully functional license server that uses all of the features of the Adobe Primetime DRM Java SDK.
seo-description: The reference implementation server can help you create a fully functional license server that uses all of the features of the Adobe Primetime DRM Java SDK.
seo-title: License server
title: License server
uuid: 39cb0d0f-f3dc-48e9-b6fd-6960a9ade291
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# License server {#license-server}

The reference implementation server can help you create a fully functional license server that uses all of the features of the Adobe Primetime DRM Java SDK.

In this implementation, users are authenticated based on user entries in a database. Der Server enthält eine Geschäftslogik zur Demonstration von Lizenzen und bietet Kompatibilitätsunterstützung für Flash Media Rights Management Server 1.0 und 1.5.

## Lizenzserveranforderungen {#license-server-requirements}

Lizenzserver-Anforderungen:

* Installieren Sie Tomcat 6.0 oder höher
* Installieren einer Datenbank, z. B. MySQL (auf der DVD verfügbar unter [!DNL Third Party\MySQL])
* Vergewissern Sie sich, dass Java 1.6 oder höher installiert ist.
* Um die Musteraufbauskripte auszuführen, stellen Sie sicher, dass Sie über Ant 1.8 oder höher verfügen

Wenden Sie sich nach der Installation von Tomcat und MySQL an die Adobe, um die erforderlichen DRM-Anmeldeinformationen anzuzeigen.

## Lizenzserver erstellen {#build-the-license-server}

>[!NOTE]
>
>Das Erstellen des Lizenzservers ist nur erforderlich, wenn Sie den Quellcode ändern möchten. Zu Testzwecken können Sie die WAR-Dateien einfach so verwenden, wie sie im Lieferumfang enthalten sind.

The reference implementation license server includes all of the license server source code ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`), along with an Ant build script ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`) with which you can customize the license server to suit your business needs.

1. Ändern Sie das Ant-Build-Skript, um die Speicherorte Ihres Primetime DRM-SDK, Tomcat, MySQL und Log4J anzugeben.

   Öffnen Sie die [!DNL build-refimpl.xml] Datei in einem Texteditor und legen Sie die folgenden Eigenschaftenwerte fest:

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Führen Sie das Ant-Build-Skript mit der `all` -Eigenschaft in dem Ordner aus, in dem sich das Ant-Build-Skript befindet.

   ```
   ant -f build-refimpl.xml all
   ```

   Das Ant-Build-Skript erstellt einen [!DNL refimpl-build/wars] Ordner, der die WAR-Dateien des Servers enthält.
