---
description: Der Referenz-Implementierungsserver kann Ihnen dabei helfen, einen voll funktionsfähigen Lizenzserver zu erstellen, der alle Funktionen des Adobe Primetime DRM Java SDK verwendet.
title: Lizenzserver
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---


# Lizenzserver {#license-server}

Der Referenz-Implementierungsserver kann Ihnen dabei helfen, einen voll funktionsfähigen Lizenzserver zu erstellen, der alle Funktionen des Adobe Primetime DRM Java SDK verwendet.

Bei dieser Implementierung werden Benutzer anhand von Benutzereinträgen in einer Datenbank authentifiziert. Der Server enthält eine Geschäftslogik zur Demonstration von Lizenzen und bietet Kompatibilitätsunterstützung für Flash Media Rights Management Server 1.0 und 1.5.

## Lizenzserveranforderungen {#license-server-requirements}

Lizenzserver-Anforderungen:

* Installieren Sie Tomcat 6.0 oder höher
* Installieren einer Datenbank, z. B. MySQL (auf der DVD verfügbar, in [!DNL Third Party\MySQL])
* Vergewissern Sie sich, dass Java 1.6 oder höher installiert ist.
* Um die Musteraufbauskripte auszuführen, stellen Sie sicher, dass Sie über Ant 1.8 oder höher verfügen

Wenden Sie sich nach der Installation von Tomcat und MySQL an die Adobe, um die erforderlichen DRM-Anmeldeinformationen anzuzeigen.

## Erstellen Sie den Lizenzserver {#build-the-license-server}

>[!NOTE]
>
>Das Erstellen des Lizenzservers ist nur erforderlich, wenn Sie den Quellcode ändern möchten. Zu Testzwecken können Sie die WAR-Dateien einfach so verwenden, wie sie im Lieferumfang enthalten sind.

Der Referenz-Implementierungslizenzserver enthält den gesamten Quellcode des Lizenzservers ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`) sowie ein Ant-Build-Skript ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`), mit dem Sie den Lizenzserver an Ihre geschäftlichen Anforderungen anpassen können.

1. Ändern Sie das Ant-Build-Skript, um die Speicherorte Ihres Primetime DRM-SDK, Tomcat, MySQL und Log4J anzugeben.

   Öffnen Sie die Datei [!DNL build-refimpl.xml] in einem Texteditor und legen Sie die folgenden Eigenschaftswerte fest:

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Führen Sie das Ant-Build-Skript mit der Eigenschaft `all` in dem Ordner aus, in dem sich das Ant-Build-Skript befindet.

   ```
   ant -f build-refimpl.xml all
   ```

   Das Ant-Build-Skript erstellt einen Ordner [!DNL refimpl-build/wars], der die WAR-Dateien des Servers enthält.
