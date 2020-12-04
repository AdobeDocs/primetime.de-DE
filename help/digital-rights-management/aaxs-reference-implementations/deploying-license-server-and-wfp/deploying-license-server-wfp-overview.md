---
seo-title: Überblick über die Bereitstellung des Lizenzservers und des Packager für überwachte Ordner
title: Überblick über die Bereitstellung des Lizenzservers und des Packager für überwachte Ordner
uuid: 4b71f2f4-f971-4382-ae41-171f7dfdfe21
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Übersicht über den Lizenzserver und den überwachten Ordner-Packager bereitstellen{#deploying-the-license-server-and-watched-folder-packager-overview}

Kopieren Sie die WAR-Dateien des Lizenzservers in den Ordner [!DNL webapps] von Tomcat. Wenn Sie die WAR-Datei bereits bereitgestellt haben, müssen Sie möglicherweise die entpackten WAR-Ordner ( [!DNL flashaccess], [!DNL edcws] und [!DNL flashaccess-packager] im Ordner [!DNL webapps] von Tomcat) manuell löschen. Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die Datei [!DNL server.xml] im conf-Verzeichnis von Tomcat und setzen Sie das `unpackWARs`-Attribut auf `false`.

Die Eigenschaftendatei ( [!DNL flashaccess-refimpl.properties]) muss sich im Klassenpfad befinden, damit der Server die Eigenschaften laden kann. Kopieren Sie diese Datei in ein Verzeichnis und aktualisieren Sie die Datei mit den entsprechenden Werten. Bearbeiten Sie die Datei [!DNL catalina.properties] im Ordner [!DNL conf] von Tomcat und fügen Sie den Ordner mit [!DNL flashaccess-refimpl.properties] der Eigenschaft `shared.loader` hinzu. Die [!DNL log4j.xml]-Datei zum Konfigurieren der Protokollierung muss sich ebenfalls im Klassenpfad befinden (ein Beispiel finden Sie unter [!DNL resources\log4j.xml]).

Der Referenz-Implementierungsserver verwendet mehrere Zertifikatdateien, Richtliniendateien und andere Ressourcen. Diese Dateien befinden sich alle in einem Ressourcenordner. Standardmäßig ist der Ressourcenordner [!DNL C:\flashaccess-server-resources], aber dieser Speicherort kann unter [!DNL flashaccess-refimpl.properties] geändert werden. Stellen Sie sicher, dass alle erforderlichen Ressourcen an diesen Speicherort kopiert werden, bevor Sie den Server starten.

Führen Sie zum Beginn Tomcat und des Lizenzservers `catalina.bat start` aus dem Tomcat-Ordner [!DNL bin] aus.
