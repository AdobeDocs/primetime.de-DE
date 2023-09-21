---
title: Übersicht über das Bereitstellen des Lizenzservers und den überwachten Ordner-Packager
description: Übersicht über das Bereitstellen des Lizenzservers und den überwachten Ordner-Packager
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Übersicht über das Bereitstellen des Lizenzservers und den überwachten Ordner-Packager {#deploying-the-license-server-and-watched-folder-packager-overview}

Kopieren Sie die WAR-Dateien des Lizenzservers in die Datei von Tomcat. [!DNL webapps] Verzeichnis. Wenn Sie die WAR-Datei bereits bereitgestellt haben, müssen Sie möglicherweise die entpackten WAR-Ordner manuell löschen ( [!DNL flashaccess], [!DNL edcws], und [!DNL flashaccess-packager] in Tomcat [!DNL webapps] Verzeichnis). Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die [!DNL server.xml] -Datei im Verzeichnis &quot;conf&quot;von Tomcat und legen Sie die `unpackWARs` Attribut `false`.

Die Eigenschaftendatei ( [!DNL flashaccess-refimpl.properties]) muss sich im Klassenpfad befinden, damit der Server die Eigenschaften laden kann. Kopieren Sie diese Datei in ein Verzeichnis und aktualisieren Sie die Datei mit den entsprechenden Werten. Bearbeiten Sie die [!DNL catalina.properties] -Datei in Tomcat [!DNL conf] und fügen Sie den Ordner hinzu, der [!DNL flashaccess-refimpl.properties] der `shared.loader` -Eigenschaft. Die [!DNL log4j.xml] -Datei zum Konfigurieren der Protokollierung muss sich ebenfalls im Klassenpfad befinden (siehe [!DNL resources\log4j.xml] Beispiel).

Der Referenz-Implementierungsserver verwendet mehrere Zertifikatdateien, Richtliniendateien und andere Ressourcen. Diese Dateien befinden sich alle in einem Ressourcenordner. Standardmäßig ist der Ordner der Ressource [!DNL C:\flashaccess-server-resources], aber dieser Speicherort kann in [!DNL flashaccess-refimpl.properties]. Kopieren Sie alle erforderlichen Ressourcen an diesen Speicherort, bevor Sie den Server starten.

Um Tomcat und den Lizenzserver zu starten, führen Sie `catalina.bat start` von Tomcat [!DNL bin] Verzeichnis.
