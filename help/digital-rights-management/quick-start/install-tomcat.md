---
seo-title: Tomcat installieren
title: Tomcat installieren
uuid: f7663eda-ad18-4a6e-bb9f-01c74721b047
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Tomcat installieren {#install-tomcat}

Sie müssen Tomcat auf beiden Servern installieren.
1. Installieren Sie Tomcat aus dem Ordner [!DNL\Third Party\Tomcat\6.0.18\] auf der Installations-DVD.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Tomcat an einem Speicherort installiert ist, an dem sich keine Leerzeichen im Pfad befinden. Sie können eintreten, `C:\Program Files\Tomcat`aber nicht `C:\Tomcat\`.

1. Um Beginn Tomcat, geben Sie ein `TomcatInstallDir>\bin\catalina.bat run`.
1. Um die Installation zu überprüfen, gehen Sie zur Tomcat-Landingpage, indem Sie `https://<Hostname>:8080/`.
1. Erstellen Sie eine `crossdomain.xml` Datei und legen Sie die Datei im `<TomcatInstallDir>\webapps\ROOT\` Verzeichnis ab.

   Sie können auch eine Datei aus dem `https://drmtest2.adobe.com/crossdomain.xml` Verzeichnis kopieren.
