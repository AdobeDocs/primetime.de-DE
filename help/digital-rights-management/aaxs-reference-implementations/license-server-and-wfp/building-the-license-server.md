---
title: Erstellen des Lizenzservers
description: Erstellen des Lizenzservers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Erstellen des Lizenzservers {#building-the-license-server}

Der Referenz-Implementierungslizenzserver enthält WAR-Dateien zum Bereitstellen des Lizenzservers. Es enthält auch den gesamten Quellcode des Lizenzservers und ein Ant Build-Skript (Referenz Implementation\Server\refimpl\build-refimpl.xml), damit Sie problemlos Änderungen am Code vornehmen können.

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie den Quellcode ändern möchten. Zu Testzwecken können Sie diesen Schritt überspringen und die WAR-Dateien wie ausgeliefert verwenden.

Bevor Sie das Ant-Skript ausführen, ändern Sie das Skript, um die Speicherorte von Adobe Access SDK, Tomcat, MySQL und Log4J anzugeben. Öffnen Sie die Datei &quot;build-refimpl.xml&quot;in einem Texteditor und bearbeiten Sie die Werte der Eigenschaften `sdkdir, tomcatdir, mysqldir, and log4jdir`. Um den Quellcode zu kompilieren und die WAR-Dateien für die Referenzimplementierung zu erstellen, führen Sie das Skript mit `ant -f build-refimpl.xml all` in dem Ordner aus, der das Ant-Skript enthält. Nach Abschluss des Skripts wird ein Ordner [!DNL refimpl-build/wars] erstellt, der die WAR-Dateien des Servers enthält.
