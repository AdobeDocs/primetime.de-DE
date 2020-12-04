---
seo-title: WAR-Dateien bereitstellen
title: WAR-Dateien bereitstellen
uuid: 435a6a6e-c981-46fb-bca9-7f5f34eecd6a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---


# WAR-Dateien {#deploy-the-war-files} bereitstellen

1. Kopieren Sie die WAR-Datei in den Ordner [!DNL webapps] von Tomcat.

   * Individualisierungsserver: [!DNL flashaccess.war]
   * Key Generation Server: [!DNL flashaccess-kgs.war]

1. Kopieren Sie den Ordner [!DNL ROOT] aus dem von der Adobe bereitgestellten Paket in den Ordner [!DNL webapps].

   Der Individualisierungsserver muss auch die Datei [!DNL crossdomain.xml] hosten. (Der Ordner [!DNL ROOT] enthält die Datei [!DNL crossdomain.xml]. [!DNL ROOT] muss sich in Großbuchstaben befinden.) Der Key Generation-Server benötigt diese Datei nicht.

