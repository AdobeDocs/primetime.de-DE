---
title: Einrichten und Bereitstellen des Servers für geschütztes Streaming
description: Einrichten und Bereitstellen des Servers für geschütztes Streaming
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Einrichten und Bereitstellen des Servers für geschütztes Streaming {#set-up-and-deploy-the-server-for-protected-streaming}

1. Richten Sie den Konfigurationsordner auf der Primetime DRM-DVD ein:

   `\Adobe Access Server for Protected Streaming\configs\`
1. Kopieren Sie das Beispiel `configs` Ordner in `<Tomcat_installation_dir>` und benennen Sie den kopierten Ordner in `licenseserver`.

   Der Pfad zum Ordner &quot;configs&quot;sollte jetzt `<Tomcat_install_dir>\licenseserver\`.
1. Ausführen `Scrambler.bat` um die verschlüsselten Kennwörter für die Transport- und Lizenzserver-PFX-Dateien im Primetime DRM zu erhalten. `<DVD>` `\Adobe Access Server for Protected Streaming\` directory:

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. Kopieren Sie die PFX-Dateien in die `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\` Verzeichnis.
1. Bearbeiten Sie die entsprechende Mandantenkonfiguration in `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`mit den folgenden Einstellungen:

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. Führen Sie die `Validator.bat` Dienstprogramm zur Überprüfung der Gültigkeit der Konfiguration:

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. Kopieren Sie die `flashaccessserver.war` -Datei von der CD in die `<TomcatInstallDir>\webapps\` Verzeichnis.
1. Wenn Tomcat ausgeführt wird, stoppen Sie die laufende Tomcat-Instanz, indem Sie `<CTRL-C>` im Befehlsfenster (wenn es über das Befehlsfenster gestartet wurde). Sie können den Server auch von der Windows Services-Anwendung aus stoppen, wenn Tomcat als Windows-Dienst installiert wurde.
1. Geben Sie den folgenden Befehl ein, um Tomcat zu starten:

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. Geben Sie zur Überprüfung der Einrichtung die folgende URL in einen Browser ein:

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
