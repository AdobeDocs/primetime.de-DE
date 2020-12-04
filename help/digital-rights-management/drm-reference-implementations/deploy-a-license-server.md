---
description: 'null'
seo-description: 'null'
seo-title: Lizenzserver bereitstellen
title: Lizenzserver bereitstellen
uuid: bee7ead1-ed13-4894-80f9-5196bf2f818f
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Bereitstellen des Lizenzservers{#deploy-the-license-server}

1. Kopieren Sie die Kriegsdateien für die Referenzimplementierung in den Ordner `webapps` auf Ihrem Tomcat-Server.

   Um den Referenz-Implementierungslizenzserver unverändert zu verwenden, können Sie einfach die WAR-Datei des Lizenzservers ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`) in den Ordner `webapps` auf Ihrem Tomcat-Server kopieren.

   Wenn Sie den Referenz-Implementierungslizenzserver anpassen, kopieren Sie die von Ihnen erstellten Serverkriegsdateien von `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` in den Ordner `webapps`.

   >[!NOTE]
   >
   >Wenn Sie zuvor WAR-Dateien des Lizenzservers bereitgestellt haben, müssen Sie möglicherweise die entpackten WAR-Ordner im Ordner [!DNL webapps] auf dem Tomcat-Server löschen:
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]


   >[!NOTE]
   >
   >Stellen Sie [!DNL edsws.war] nur dann bereit, wenn Sie eine Abwärtskompatibilität mit Flash Media Rights Management (FMRMS) v1.5-Inhalten benötigen. (Dies ist eine sehr seltene Anforderung.)
   >
   >Wenn Sie verhindern möchten, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie `server.xml` im Ordner `conf` und setzen Sie `unpackWARs` auf `false`.

1. Kopieren Sie den gesamten Inhalt des Ordners `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` in den Ordner [!DNL tomcat].

   Der Ordner [!DNL resources] enthält:

   * [!DNL flashaccesstools.properties] - Die Eigenschaftendatei des Lizenzservers.
   * [!DNL log4j.xml] - Konfiguration der Lizenzserverprotokollierung
   * [!DNL *.pol] - Beispiel für DRM-Richtliniendateien.

   Darüber hinaus können Sie auch die Zertifizierungsdateien für die Adobe an diesen Speicherort kopieren.

1. Ändern Sie die Lizenzservereinstellungen in [!DNL flashaccesstools.properties], um Ihre Servereinrichtung anzuzeigen.

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

1. Bearbeiten Sie die Datei `catalina.properties` im Ordner Tomcat `conf`; fügen Sie den Speicherort Ihres [!DNL resources]-Ordners (oder den alternativen Speicherort, an dem Sie Ihre Eigenschaftendatei und andere Ressourcendateien gespeichert haben) zur `shared.loader`-Eigenschaft hinzu.

   Wenn Sie beispielsweise `flashaccess-refimpl.properties` in [!DNL [Tomcat home]\resources\] haben:

   ```
   shared.loader=..\resources
   ```

   Dadurch wird `flashaccess-refimpl.properties` auf den Klassenpfad gesetzt.
1. Vergewissern Sie sich, dass sich Ihre anderen Ressourcendateien ( [!DNL log4j.xml], Richtliniendateien, Zertifizierungen) entweder im Ordner [!DNL resources] befinden oder sich anderweitig im Klassenpfad befinden und ihr Speicherort in [!DNL flashaccess-refimpl.properties] angegeben ist.

   Sie möchten `log4j` wahrscheinlich zunächst im Debug-Modus ausführen. Setzen Sie [!DNL log4j.xml] auf true:`debug`

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Beginn Sie im Ordner Tomcat [!DNL bin] Ihren Server.

   Unter Linux:

   ```
   catalina.sh start
   ```

   Windows:

   ```
   catalina.bat start
   ```
