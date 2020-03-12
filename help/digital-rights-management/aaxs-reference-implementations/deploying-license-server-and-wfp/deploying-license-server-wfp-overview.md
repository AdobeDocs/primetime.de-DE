---
seo-title: Überblick über die Bereitstellung des Lizenzservers und des Packager für überwachte Ordner
title: Überblick über die Bereitstellung des Lizenzservers und des Packager für überwachte Ordner
uuid: 4b71f2f4-f971-4382-ae41-171f7dfdfe21
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Überblick über die Bereitstellung des Lizenzservers und des Packager für überwachte Ordner {#deploying-the-license-server-and-watched-folder-packager-overview}

Kopieren Sie die WAR-Dateien des Lizenzservers in den [!DNL webapps] Ordner von Tomcat. Wenn Sie die WAR-Datei bereits bereitgestellt haben, müssen Sie möglicherweise die entpackten WAR-Ordner ( [!DNL flashaccess], [!DNL edcws]und [!DNL flashaccess-packager] im [!DNL webapps] Verzeichnis von Tomcat) manuell löschen. Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die [!DNL server.xml] Datei im conf-Verzeichnis von Tomcat und setzen Sie das `unpackWARs` Attribut auf `false`.

Die Eigenschaftendatei ( [!DNL flashaccess-refimpl.properties]) muss sich im Klassenpfad befinden, damit der Server die Eigenschaften laden kann. Kopieren Sie diese Datei in ein Verzeichnis und aktualisieren Sie die Datei mit den entsprechenden Werten. Bearbeiten Sie die [!DNL catalina.properties] Datei im [!DNL conf] Verzeichnis von Tomcat und fügen Sie den Ordner hinzu, der [!DNL flashaccess-refimpl.properties] die `shared.loader` Eigenschaft enthält. Die [!DNL log4j.xml] Datei zum Konfigurieren der Protokollierung muss sich ebenfalls im Klassenpfad befinden (siehe [!DNL resources\log4j.xml] ein Beispiel).

Der Referenz-Implementierungsserver verwendet mehrere Zertifikatdateien, Richtliniendateien und andere Ressourcen. Diese Dateien befinden sich alle in einem Ressourcenordner. Standardmäßig ist der Ressourcenordner [!DNL C:\flashaccess-server-resources]festgelegt, dieser Speicherort kann jedoch geändert werden [!DNL flashaccess-refimpl.properties]. Stellen Sie sicher, dass alle erforderlichen Ressourcen an diesen Speicherort kopiert werden, bevor Sie den Server starten.

Um Beginn Tomcat und den Lizenzserver zu erhalten, führen Sie die Ausführung `catalina.bat start` aus dem Tomcat- [!DNL bin] Verzeichnis aus.
