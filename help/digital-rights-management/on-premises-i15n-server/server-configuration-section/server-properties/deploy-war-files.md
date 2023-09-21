---
title: WAR-Dateien bereitstellen
description: WAR-Dateien bereitstellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---

# WAR-Dateien bereitstellen{#deploy-the-war-files}

1. Kopieren Sie die WAR-Datei in die Datei von Tomcat. [!DNL webapps] Verzeichnis.

   * Individualisierungsserver: [!DNL flashaccess.war]
   * Key Generation Server: [!DNL flashaccess-kgs.war]

1. Kopieren Sie die [!DNL ROOT] -Ordner aus dem von Adobe bereitgestellten Paket zum [!DNL webapps] Verzeichnis.

   Der Individualisierungsserver muss außerdem die [!DNL crossdomain.xml] -Datei. (Die [!DNL ROOT] -Ordner enthält [!DNL crossdomain.xml] Datei; [!DNL ROOT] muss sich in Großbuchstaben befinden.) Der Key Generation Server benötigt diese Datei nicht.
