---
seo-title: WAR-Dateien bereitstellen
title: WAR-Dateien bereitstellen
uuid: 435a6a6e-c981-46fb-bca9-7f5f34eecd6a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# WAR-Dateien bereitstellen{#deploy-the-war-files}

1. Kopieren Sie die WAR-Datei in das [!DNL webapps] Verzeichnis von Tomcat.

   * Individualisierungsserver: [!DNL flashaccess.war]
   * Key Generation Server: [!DNL flashaccess-kgs.war]

1. Kopieren Sie den [!DNL ROOT] Ordner aus dem von Adobe bereitgestellten Paket in den [!DNL webapps] Ordner.

   Der Individualisierungsserver muss die [!DNL crossdomain.xml] Datei auch hosten. (Der [!DNL ROOT] Ordner enthält die [!DNL crossdomain.xml] Datei. muss in Großbuchstaben sein.) [!DNL ROOT] Der Key Generation-Server benötigt diese Datei nicht.

