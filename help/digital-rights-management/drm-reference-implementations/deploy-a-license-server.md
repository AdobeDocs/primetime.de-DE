---
description: 'null'
seo-description: 'null'
seo-title: Lizenzserver bereitstellen
title: Lizenzserver bereitstellen
uuid: bee7ead1-ed13-4894-80f9-5196bf2f818f
translation-type: tm+mt
source-git-commit: 29149594c4b41956a091ef27093304e74ff15f2f

---


# Lizenzserver bereitstellen{#deploy-the-license-server}

1. Kopieren Sie die Kriegsdateien für die Referenzimplementierung in den `webapps` Ordner auf Ihrem Tomcat-Server.

   Um den Referenz-Implementierungslizenzserver unverändert zu verwenden, können Sie einfach die WAR-Datei () des Lizenzservers in den `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war``webapps` Ordner auf Ihrem Tomcat-Server kopieren.

   Wenn Sie den Referenz-Implementierungslizenzserver anpassen, kopieren Sie die von Ihnen erstellten Serverkriegsdateien in `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` den `webapps` Ordner.

   >[!NOTE]
   >
   >Wenn Sie zuvor WAR-Dateien des Lizenzservers bereitgestellt haben, müssen Sie möglicherweise die entpackten WAR-Ordner im [!DNL webapps] Ordner auf dem Tomcat-Server löschen:        >
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]


   >[!NOTE]
   >
   >Bereitstellung nur dann möglich, [!DNL edsws.war] wenn Sie eine Abwärtskompatibilität mit Flash Media Rights Management (FMRMS) v1.5-Inhalten benötigen. (Dies ist eine sehr seltene Anforderung.)
   >
   >Wenn Sie verhindern möchten, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie `server.xml` im `conf` Verzeichnis und legen Sie `unpackWARs` die Einstellung auf `false`.

1. Kopieren Sie den gesamten Inhalt des `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` Ordners in Ihren [!DNL tomcat] Ordner.

   Der [!DNL resources] Ordner enthält:

   * [!DNL flashaccesstools.properties] - Die Eigenschaftendatei des Lizenzservers.
   * [!DNL log4j.xml] - Konfiguration der Lizenzserverprotokollierung
   * [!DNL *.pol] - Beispiel für DRM-Richtliniendateien.
   Darüber hinaus können Sie die Adobe-Zertifizierungsdateien an diesen Speicherort kopieren.

1. Ändern Sie die Einstellungen des Lizenzservers in, [!DNL flashaccesstools.properties] um Ihre Servereinrichtung anzuzeigen.

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

1. Bearbeiten Sie die `catalina.properties` Datei im Tomcat- `conf` Ordner. Fügen Sie der Eigenschaft den Speicherort Ihres [!DNL resources] Ordners (oder den alternativen Speicherort, an dem Sie Ihre Eigenschaftendatei und andere Ressourcendateien gespeichert haben) hinzu `shared.loader` .

   Beispiel: Wenn Sie sich `flashaccess-refimpl.properties` in [!DNL [Tomcat home]\resources\] befinden:

   ```
   shared.loader=..\resources
   ```

   Das steht `flashaccess-refimpl.properties` auf dem Klassenpfad.
1. Stellen Sie sicher, dass sich Ihre anderen Ressourcendateien ( [!DNL log4j.xml]Richtliniendateien, Zertifizierungen) entweder im Ordner befinden oder sich anderweitig im Klassenpfad befinden und ihr Speicherort in [!DNL resources] [!DNL flashaccess-refimpl.properties]angegeben ist.

   Sie sollten zunächst `log4j` im Debugmodus ausführen. Legen Sie in [!DNL log4j.xml]true `debug` fest:

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Beginn Sie im Tomcat- [!DNL bin] Ordner Ihren Server.

   Unter Linux:

   ```
   catalina.sh start
   ```

   Windows:

   ```
   catalina.bat start
   ```
