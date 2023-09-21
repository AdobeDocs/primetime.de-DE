---
title: Erstellen des Lizenzservers
description: Erstellen des Lizenzservers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Erstellen des Lizenzservers {#building-the-license-server}

Der Referenz-Implementierungs-Lizenzserver enthält WAR-Dateien für die Bereitstellung des Lizenzservers. Es enthält auch den gesamten Quell-Code des Lizenzservers und ein Ant Build-Skript (Referenz Implementation\Server\refimpl\build-refimpl.xml), damit Sie problemlos Änderungen am Code vornehmen können.

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie den Quellcode ändern möchten. Zu Testzwecken können Sie diesen Schritt überspringen und die WAR-Dateien wie im Lieferumfang enthalten verwenden.

Bevor Sie das Ant-Skript ausführen, ändern Sie das Skript, um die Speicherorte von Adobe Access SDK, Tomcat, MySQL und Log4J anzugeben. Öffnen Sie build-refimpl.xml in einem Texteditor und bearbeiten Sie die Werte der Eigenschaften `sdkdir, tomcatdir, mysqldir, and log4jdir`. Um den Quellcode zu kompilieren und die WAR-Dateien für die Referenzimplementierung zu erstellen, führen Sie das Skript mit `ant -f build-refimpl.xml all` im Verzeichnis, das das Ant-Skript enthält. Wenn das Skript abgeschlossen ist, wird ein [!DNL refimpl-build/wars] -Ordner mit den WAR-Dateien des Servers wird erstellt.
