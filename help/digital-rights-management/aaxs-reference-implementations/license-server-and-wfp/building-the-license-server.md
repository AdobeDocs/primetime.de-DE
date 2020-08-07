---
seo-title: Erstellen des Lizenzservers
title: Erstellen des Lizenzservers
uuid: d7ca8a8f-c778-41a2-b823-93fac9ab07c5
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Erstellen des Lizenzservers {#building-the-license-server}

Der Referenz-Implementierungslizenzserver enthält WAR-Dateien zum Bereitstellen des Lizenzservers. It also includes all the license server source code and an Ant build script (Reference Implementation\Server\refimpl\build-refimpl.xml) so you can easily make changes to the code.

>[!NOTE]
>
>This step is only needed if you want to modify the source code. Zu Testzwecken können Sie diesen Schritt überspringen und die WAR-Dateien wie ausgeliefert verwenden.

Before running the Ant script, modify the script to specify the locations of the Adobe Access SDK, Tomcat, MySQL, and Log4J. Öffnen Sie die Datei &quot;build-refimpl.xml&quot;in einem Texteditor und bearbeiten Sie die Werte der Eigenschaften `sdkdir, tomcatdir, mysqldir, and log4jdir`. Um den Quellcode zu kompilieren und die WAR-Dateien für die Referenzimplementierung zu erstellen, führen Sie das Skript mit `ant -f build-refimpl.xml all` dem Ordner aus, der das Ant-Skript enthält. Nach Abschluss des Skripts wird ein [!DNL refimpl-build/wars] Ordner mit den WAR-Dateien des Servers erstellt.
