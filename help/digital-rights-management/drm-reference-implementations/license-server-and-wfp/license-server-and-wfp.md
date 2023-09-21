---
description: Der Referenz-Implementierungsserver kann Ihnen bei der Erstellung eines voll funktionsfähigen Lizenzservers helfen, der alle Funktionen des Adobe Primetime DRM Java SDK verwendet.
title: Lizenzserver
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Lizenzserver {#license-server}

Der Referenz-Implementierungsserver kann Ihnen bei der Erstellung eines voll funktionsfähigen Lizenzservers helfen, der alle Funktionen des Adobe Primetime DRM Java SDK verwendet.

In dieser Implementierung werden Benutzer anhand von Benutzereinträgen in einer Datenbank authentifiziert. Der Server enthält eine Geschäftslogik zur Demonstration von Lizenzen und bietet Kompatibilitätsunterstützung für Flash Media Rights Management Server 1.0 und 1.5.

## Lizenzserver-Anforderungen {#license-server-requirements}

Lizenzserver-Anforderungen:

* Installieren Sie Tomcat 6.0 oder höher
* Installieren Sie eine Datenbank, z. B. MySQL (auf der DVD verfügbar, in [!DNL Third Party\MySQL])
* Stellen Sie sicher, dass Java 1.6 oder höher installiert ist.
* Um die Build-Beispielskripte auszuführen, stellen Sie sicher, dass Sie Ant 1.8 oder höher haben

Wenden Sie sich nach der Installation von Tomcat und MySQL an Adobe, um die erforderlichen DRM-Anmeldeinformationen zu erhalten.

## Lizenzserver erstellen {#build-the-license-server}

>[!NOTE]
>
>Der Aufbau des Lizenzservers ist nur erforderlich, wenn Sie den Quellcode ändern möchten. Zu Testzwecken können Sie einfach die WAR-Dateien wie im Lieferumfang enthalten verwenden.

Der Referenz-Implementierungs-Lizenzserver enthält den gesamten Quell-Code des Lizenzservers ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`) zusammen mit einem Ant-Build-Skript ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`), mit dem Sie den Lizenzserver an Ihre geschäftlichen Anforderungen anpassen können.

1. Ändern Sie das Ant-Build-Skript, um die Speicherorte Ihres Primetime DRM SDK, Tomcat, MySQL und Log4J anzugeben.

   Öffnen Sie die [!DNL build-refimpl.xml] -Datei in einem Texteditor und legen Sie die folgenden Eigenschaftswerte fest:

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Führen Sie das Ant-Build-Skript mit dem `all` -Eigenschaft in dem Ordner, in dem sich das Ant-Build-Skript befindet.

   ```
   ant -f build-refimpl.xml all
   ```

   Das Ant-Build-Skript erstellt eine [!DNL refimpl-build/wars] -Verzeichnis, das die WAR-Dateien des Servers enthält.
