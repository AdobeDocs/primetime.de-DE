---
title: WAR-Dateien bereitstellen
description: WAR-Dateien bereitstellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

