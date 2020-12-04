---
seo-title: Tomcat installieren
title: Tomcat installieren
uuid: f7663eda-ad18-4a6e-bb9f-01c74721b047
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# Tomcat {#install-tomcat} installieren

Sie müssen Tomcat auf beiden Servern installieren.
1. Installieren Sie Tomcat aus dem Ordner  [!DNL \Third Party\Tomcat\6.0.18\] auf der Installations-DVD.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Tomcat an einem Speicherort installiert ist, an dem sich keine Leerzeichen im Pfad befinden. Sie können `C:\Program Files\Tomcat`, aber nicht `C:\Tomcat\` eingeben.

1. Geben Sie zum Beginn Tomcat `TomcatInstallDir>\bin\catalina.bat run` ein.
1. Um die Installation zu überprüfen, gehen Sie zur Tomcat-Landingpage, indem Sie `https://<Hostname>:8080/` eingeben.
1. Erstellen Sie eine `crossdomain.xml`-Datei und legen Sie die Datei im Ordner `<TomcatInstallDir>\webapps\ROOT\` ab.

   Sie können auch eine Datei aus dem Ordner `https://drmtest2.adobe.com/crossdomain.xml` kopieren.
