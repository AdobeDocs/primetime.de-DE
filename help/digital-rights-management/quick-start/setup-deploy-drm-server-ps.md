---
seo-title: Einrichten und Bereitstellen des Servers für das geschützte Streaming
title: Einrichten und Bereitstellen des Servers für das geschützte Streaming
uuid: 300a1b63-0bf0-48a8-977d-212563025c19
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Einrichten und Bereitstellen des Servers für das geschützte Streaming {#set-up-and-deploy-the-server-for-protected-streaming}

1. Richten Sie den Konfigurationsordner auf der Primetime DRM-DVD ein:

   `\Adobe Access Server for Protected Streaming\configs\`
1. Kopieren Sie den Beispielordner in Ihren `configs` Ordner `<Tomcat_installation_dir>` und benennen Sie den kopierten Ordner um in `licenseserver`.

   Der Pfad zum Ordner &quot;configs&quot;sollte nun `<Tomcat_install_dir>\licenseserver\`sein.
1. Führen Sie `Scrambler.bat` folgende Schritte aus, um die verschlüsselten Kennwörter für die Transport- und Lizenzserver-PFX-Dateien im Primetime-DRM- `<DVD>``\Adobe Access Server for Protected Streaming\` Ordner abzurufen:

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. Kopieren Sie die PFX-Dateien in den `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\` Ordner.
1. Bearbeiten Sie die entsprechende Mandantenkonfiguration mit `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`den folgenden Einstellungen:

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. Führen Sie das `Validator.bat` Dienstprogramm aus, um zu überprüfen, ob die Konfiguration gültig ist:

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. Kopieren Sie die `flashaccessserver.war` Datei von der CD in den `<TomcatInstallDir>\webapps\` Ordner.
1. Wenn Tomcat ausgeführt wird, beenden Sie die laufende Tomcat-Instanz, indem Sie `<CTRL-C>` im Befehlsfenster drücken (sofern sie aus dem Befehlsfenster gestartet wurde). Sie können den Server auch von der Windows-Services-Anwendung aus beenden, wenn Tomcat als Windows-Dienst installiert wurde.
1. Geben Sie zum Beginn Tomcat folgenden Befehl ein:

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. Geben Sie zur Überprüfung der Einrichtung die folgende URL in einen Browser ein:

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
