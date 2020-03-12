---
seo-title: Erstellen des Lizenzservers
title: Erstellen des Lizenzservers
uuid: d7ca8a8f-c778-41a2-b823-93fac9ab07c5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Erstellen des Lizenzservers {#building-the-license-server}

Der Referenz-Implementierungslizenzserver enthält WAR-Dateien zum Bereitstellen des Lizenzservers. Es enthält auch den gesamten Quellcode des Lizenzservers und ein Ant Build-Skript (Referenz Implementation\Server\refimpl\build-refimpl.xml), damit Sie problemlos Änderungen am Code vornehmen können.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Dieser Schritt ist nur erforderlich, wenn Sie den Quellcode ändern möchten. Zu Testzwecken können Sie diesen Schritt überspringen und die WAR-Dateien wie ausgeliefert verwenden.

Bevor Sie das Ant-Skript ausführen, ändern Sie das Skript, um die Speicherorte von Adobe Access SDK, Tomcat, MySQL und Log4J anzugeben. Öffnen Sie die Datei &quot;build-refimpl.xml&quot;in einem Texteditor und bearbeiten Sie die Werte der Eigenschaften `sdkdir, tomcatdir, mysqldir, and log4jdir`. Um den Quellcode zu kompilieren und die WAR-Dateien für die Referenzimplementierung zu erstellen, führen Sie das Skript mit `ant -f build-refimpl.xml all` dem Ordner aus, der das Ant-Skript enthält. Nach Abschluss des Skripts wird ein [!DNL refimpl-build/wars] Ordner mit den WAR-Dateien des Servers erstellt.
