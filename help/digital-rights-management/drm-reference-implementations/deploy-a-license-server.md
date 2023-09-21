---
title: Lizenzserver bereitstellen
description: Lizenzserver bereitstellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Lizenzserver bereitstellen{#deploy-the-license-server}

1. Kopieren Sie die WAR-Dateien für die Referenzimplementierung in `webapps` auf Ihrem Tomcat-Server.

   Um den Referenz-Implementierungslizenzserver unverändert zu verwenden, können Sie einfach die WAR-Datei des Lizenzservers kopieren ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`) auf `webapps` auf Ihrem Tomcat-Server.

   Wenn Sie den Referenz-Implementierungs-Lizenzserver anpassen, kopieren Sie die Server-WAR-Dateien, aus denen Sie erstellt haben `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` der `webapps` Verzeichnis.

   >[!NOTE]
   >
   >Wenn Sie zuvor die WAR-Dateien des Lizenzservers bereitgestellt haben, müssen Sie möglicherweise die entpackten WAR-Ordner in den [!DNL webapps] Ordner auf dem Tomcat-Server:
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]

   >[!NOTE]
   >
   >Nicht bereitstellen [!DNL edsws.war] es sei denn, Sie benötigen Abwärtskompatibilität mit Flash Media Rights Management (FMRMS) v1.5-Inhalten. (Dies ist eine sehr seltene Anforderung.)
   >
   >Wenn Sie verhindern möchten, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie `server.xml` im `conf` Verzeichnis und festgelegt `unpackWARs` nach `false`.

1. Den gesamten Inhalt der `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` in [!DNL tomcat] Verzeichnis.

   Die [!DNL resources] enthält:

   * [!DNL flashaccesstools.properties] - Die Eigenschaftendatei des Lizenzservers.
   * [!DNL log4j.xml] - Konfiguration der Lizenzserver-Protokollierung
   * [!DNL *.pol] - Beispiele für DRM-Richtliniendateien.

   Außerdem können Sie die Adobe-Zertifizierungsdateien an diesen Speicherort kopieren.

1. Ändern Sie die Einstellungen des Lizenzservers in [!DNL flashaccesstools.properties] , um Ihre Server-Einrichtung widerzuspiegeln.

   Legen Sie mindestens Werte für die folgenden Eigenschaften fest:

   * `config.resourcesDirectory`
   * `HandlerConfiguration.ServerTransportCredential`
   * `HandlerConfiguration.ServerTransportCredential.password`
   * `LicenseHandler.ServerCredential`
   * `LicenseHandler.ServerCredential.password`
   * `MetaDataConverter.SignatureParameters.ServerCredential`
   * `MetaDataConverter.SignatureParameters.ServerCredential.password`
   * `V2KeyParameters.LicenseServerUrl`
   * `V2KeyParameters.KeyOptions.AsymmetricKeyOptions.Certificate`
   * V2KeyParameters.LicenseServerTransportCertificate

1. Bearbeiten Sie die `catalina.properties` Datei in Ihrem Tomcat `conf` Verzeichnis; fügen Sie den Speicherort Ihrer [!DNL resources] Verzeichnis (oder der alternative Speicherort, an dem Sie Ihre Eigenschaftendatei und andere Ressourcendateien gespeichert haben) in der `shared.loader` -Eigenschaft.

   Wenn Sie beispielsweise `flashaccess-refimpl.properties` in [!DNL [Tomcat zu Hause]\resources\]:

   ```
   shared.loader=..\resources
   ```

   Diese Stelle `flashaccess-refimpl.properties` auf den Klassenpfad.
1. Stellen Sie sicher, dass Ihre anderen Ressourcendateien ( [!DNL log4j.xml], Richtliniendateien, Zertifizierungen) entweder im [!DNL resources] oder sich anderweitig im Klassenpfad und dem Speicherort befinden, der in [!DNL flashaccess-refimpl.properties].

   Sie werden wahrscheinlich zunächst `log4j` im Debug-Modus. In [!DNL log4j.xml], set `debug` auf true:

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Vom Tomcat [!DNL bin] -Verzeichnis, starten Sie Ihren Server.

   Unter Linux:

   ```
   catalina.sh start
   ```

   Unter Windows:

   ```
   catalina.bat start
   ```
