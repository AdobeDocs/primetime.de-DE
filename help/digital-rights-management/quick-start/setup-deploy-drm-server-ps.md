---
title: Einrichten und Bereitstellen des Servers für das geschützte Streaming
description: Einrichten und Bereitstellen des Servers für das geschützte Streaming
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Einrichten und Bereitstellen des Servers für das geschützte Streaming {#set-up-and-deploy-the-server-for-protected-streaming}

1. Richten Sie den Konfigurationsordner auf der Primetime DRM-DVD ein:

   `\Adobe Access Server for Protected Streaming\configs\`
1. Kopieren Sie den Ordner `configs` in den Ordner `<Tomcat_installation_dir>` und benennen Sie den kopierten Ordner in `licenseserver` um.

   Der Pfad zum Ordner &quot;configs&quot;sollte nun &quot;`<Tomcat_install_dir>\licenseserver\`&quot;lauten.
1. Führen Sie `Scrambler.bat` aus, um die verschlüsselten Kennwörter für die PFX-Dateien des Transport- und Lizenzservers im Ordner Primetime DRM `<DVD>` `\Adobe Access Server for Protected Streaming\` abzurufen:

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. Kopieren Sie die PFX-Dateien in den Ordner `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\`.
1. Bearbeiten Sie die entsprechende Mandantenkonfiguration in `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml` mit den folgenden Einstellungen:

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. Führen Sie das Dienstprogramm `Validator.bat` aus, um zu überprüfen, ob die Konfiguration gültig ist:

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. Kopieren Sie die Datei `flashaccessserver.war` von der CD in den Ordner `<TomcatInstallDir>\webapps\`.
1. Wenn Tomcat ausgeführt wird, beenden Sie die laufende Tomcat-Instanz, indem Sie im Befehlsfenster `<CTRL-C>` drücken (wenn sie aus dem Befehlsfenster gestartet wurde). Sie können den Server auch von der Windows-Services-Anwendung aus beenden, wenn Tomcat als Windows-Dienst installiert wurde.
1. Geben Sie zum Beginn Tomcat folgenden Befehl ein:

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. Geben Sie zur Überprüfung der Einrichtung die folgende URL in einen Browser ein:

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
