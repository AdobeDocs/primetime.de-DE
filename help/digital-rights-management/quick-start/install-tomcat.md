---
title: Installieren von Tomcat
description: Installieren von Tomcat
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Installieren von Tomcat {#install-tomcat}

Sie müssen Tomcat auf beiden Servern installieren.
1. Installieren Sie Tomcat aus dem [!DNL \Third Party\Tomcat\6.0.18\] auf der Installations-DVD.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Tomcat an einem Speicherort installiert ist, an dem sich keine Leerzeichen im Pfad befinden. Sie können `C:\Program Files\Tomcat`, aber nicht `C:\Tomcat\`.

1. Um Tomcat zu starten, geben Sie `TomcatInstallDir>\bin\catalina.bat run`.
1. Gehen Sie zur Überprüfung der Installation zur Tomcat-Landingpage, indem Sie `https://<Hostname>:8080/`.
1. Erstellen Sie eine `crossdomain.xml` und speichern Sie die Datei in der `<TomcatInstallDir>\webapps\ROOT\` Verzeichnis.

   Sie können auch eine Datei aus dem `https://drmtest2.adobe.com/crossdomain.xml` Verzeichnis.
