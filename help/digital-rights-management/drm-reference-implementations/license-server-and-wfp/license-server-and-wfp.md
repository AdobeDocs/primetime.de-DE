---
description: Der Referenz-Implementierungsserver kann Ihnen dabei helfen, einen voll funktionsfähigen Lizenzserver zu erstellen, der alle Funktionen des Adobe Primetime DRM Java SDK verwendet.
seo-description: Der Referenz-Implementierungsserver kann Ihnen dabei helfen, einen voll funktionsfähigen Lizenzserver zu erstellen, der alle Funktionen des Adobe Primetime DRM Java SDK verwendet.
seo-title: Lizenzserver
title: Lizenzserver
uuid: 39cb0d0f-f3dc-48e9-b6fd-6960a9ade291
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Lizenzserver {#license-server}

Der Referenz-Implementierungsserver kann Ihnen dabei helfen, einen voll funktionsfähigen Lizenzserver zu erstellen, der alle Funktionen des Adobe Primetime DRM Java SDK verwendet.

Bei dieser Implementierung werden Benutzer anhand von Benutzereinträgen in einer Datenbank authentifiziert. Der Server enthält eine Geschäftslogik zur Demonstration von Lizenzen und bietet Kompatibilitätsunterstützung für Flash Media Rights Management Server 1.0 und 1.5.

## Lizenzserveranforderungen {#license-server-requirements}

Lizenzserver-Anforderungen:

* Installieren Sie Tomcat 6.0 oder höher
* Installieren einer Datenbank, z. B. MySQL (auf der DVD verfügbar unter [!DNL Third Party\MySQL])
* Vergewissern Sie sich, dass Java 1.6 oder höher installiert ist.
* Um die Musteraufbauskripte auszuführen, stellen Sie sicher, dass Sie über Ant 1.8 oder höher verfügen

Wenden Sie sich nach der Installation von Tomcat und MySQL an Adobe, um die erforderlichen DRM-Anmeldeinformationen zu erhalten.

## Lizenzserver erstellen {#build-the-license-server}

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Das Erstellen des Lizenzservers ist nur erforderlich, wenn Sie den Quellcode ändern möchten. Zu Testzwecken können Sie die WAR-Dateien einfach so verwenden, wie sie im Lieferumfang enthalten sind.

Der Referenz-Implementierungslizenzserver enthält den gesamten Quellcode des Lizenzservers ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`) sowie ein Ant-Build-Skript ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`), mit dem Sie den Lizenzserver an Ihre geschäftlichen Anforderungen anpassen können.

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
