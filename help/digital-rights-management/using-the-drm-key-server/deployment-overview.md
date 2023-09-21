---
title: Übersicht über das Bereitstellen des Primetime DRM Key Server
description: Übersicht über das Bereitstellen des Primetime DRM Key Server
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# Primetime-DRM-Schlüsselserver bereitstellen {#deploy-the-primetime-drm-key-server}

Stellen Sie vor der Bereitstellung des Primetime DRM Key Servers sicher, dass Sie die erforderlichen Versionen von Java und Tomcat installiert haben. Siehe [DRM-Schlüsselserveranforderungen](../../digital-rights-management/using-the-drm-key-server/requirements.md).

Der Primetime-DRM-Key-Server-Download beinhaltet [!DNL faxsks.war]. Um diese WAR-Datei bereitzustellen, kopieren Sie die Datei in das [!DNL webapps] Verzeichnis. Wenn Sie die WAR-Datei bereits bereitgestellt haben, müssen Sie möglicherweise den entpackten WAR-Ordner manuell löschen. [!DNL faxsks] in Tomcat [!DNL webapps] Verzeichnis). Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die [!DNL server.xml] -Datei in Tomcat [!DNL conf] und legen Sie `unpackWARs` Attribut `false`.

Der Primetime-DRM-Schlüsselserver verwendet optional eine plattformspezifische Bibliothek (`jsafe.dll` unter Windows oder `libjsafe.so` auf Linux) zur Verbesserung der Leistung. Kopieren Sie die entsprechende Bibliothek für Ihre Plattform aus `thirdparty/cryptoj/platform` an einen Ort, der durch die `PATH` Umgebungsvariable (oder `LD_LIBRARY_PATH` auf Linux).

>[!NOTE]
>
>Die 64-Bit-Version der [!DNL jsafe] -Bibliothek sollte nur verwendet werden, wenn sowohl das Betriebssystem als auch JDK 64-Bit unterstützen. Verwenden Sie andernfalls die 32-Bit-Version.

## SSL-Konfiguration {#ssl-configuration}

SSL ist für die Remote HTTPS-Schlüsselbereitstellung erforderlich. Die SSL-Verbindungen können vom Anwendungsserver verarbeitet werden (d. h. durch Konfiguration von SSL in Tomcat) oder auf einem anderen Server (z. B. einem Lastenausgleich, SSL-Beschleuniger oder Apache) verarbeitet werden. Für die Remote-HTTPS-Schlüsselbereitstellung ist eine SSL-Verbindung erforderlich. Der Server benötigt ein von einer vertrauenswürdigen Zertifizierungsstelle ausgestelltes SSL-Zertifikat.

Es gibt verschiedene Optionen zum Konfigurieren von SSL. Im Folgenden finden Sie Beispiele für die Konfiguration von SSL mit Client-Authentifizierung in Apache und Tomcat.

Das folgende Beispiel zeigt die Apache SSL-Konfiguration:

```
SSLEngineon 
SSLCertificateFile "certs/server_cert.pem" 
SSLCertificateKeyFile "certs/server_key.pem" 
SSLOptions +StdEnvVars +FakeBasicAuth -ExportCertData +StrictRequire 
SSLRequireSSL 
ProxyRequests Off 
ProxyPass /https://keyserver-name:port/ 
ProxyPassReverse /https://keyserver-name:port/
```

Das folgende Beispiel zeigt die Tomcat-SSL-Konfiguration. So generieren Sie Zertifikat- und Schlüsseldateien:

```
Generate key:  
 openssl genrsa -des3 -out server.key 1024 
Generate CSR: 
 openssl req -new -key server.key -out server.csr 
Generate Certificate: 
 openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.cer
```

Wenn Sie nach dem allgemeinen Namen gefragt werden, verwenden Sie den vollständig qualifizierten Domänennamen (FQDN) Ihres Servers.

Kopieren [!DNL server.cer], und [!DNL server.key] in das Verzeichnis Tomcat. Geben Sie den folgenden Connector in [!DNL conf/server.xml]:

```
<Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true" 
 maxThreads="150" scheme="https" secure="true" 
 sslProtocol="TLS" 
 SSLCertificateFile="${catalina.base}/server.cer" 
 SSLCertificateKeyFile="${catalina.base}/server.key" 
 SSLPassword="password-for-key-file" 
 SSLVerifyClient="require"/>
```

## Java-Systemeigenschaften {#java-system-properties}

Sie können die folgenden beiden Java-Systemeigenschaften festlegen, um den Speicherort der Konfiguration und Protokolldateien für den Primetime DRM Key Server zu ändern:

* `KeyServer.ConfigRoot` - Dieser Ordner enthält alle Konfigurationsdateien für den Primetime DRM Key Server. Weitere Informationen zum Inhalt dieser Dateien finden Sie unter [Wichtige Server-Konfigurationsdateien](#key-server-configuration-files). Wenn nicht festgelegt, ist der Standardwert [!DNL CATALINA_BASE/keyserver].

* `KeyServer.LogRoot` - Dies ist ein Protokollordner, der iOS Key Server-Anwendungsprotokolle enthält. Wenn nicht festgelegt, ist der Standardwert identisch mit `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot` - Dies ist ein Protokollordner, der die Protokolle der Xbox Key Server-Anwendung enthält. Wenn nicht festgelegt, ist der Standardwert identisch mit `KeyServer.ConfigRoot`.

Wenn Sie [!DNL catalina.bat] oder [!DNL catalina.sh] um Tomcat zu starten, können diese Systemeigenschaften einfach mithilfe der `JAVA_OPTS` Umgebungsvariable. Alle hier festgelegten Java-Optionen werden beim Start von Tomcat verwendet. Beispiel:

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Primetime DRM-Anmeldeinformationen {#primetime-drm-credentials}

Um wichtige Anfragen von Primetime DRM iOS- und Xbox 360-Clients zu verarbeiten, muss der Primetime DRM Key Server mit einer Reihe von Berechtigungen konfiguriert werden, die von Adobe ausgestellt wurden. Diese Anmeldeinformationen können entweder in PKCS#12 ( [!DNL .pfx]) oder auf einem HSM.

Die [!DNL .pfx] -Dateien können sich überall befinden. Zur einfachen Konfiguration empfiehlt Adobe jedoch, die [!DNL .pfx] -Dateien im Konfigurationsverzeichnis des Mandanten. Weitere Informationen finden Sie unter [Wichtige Server-Konfigurationsdateien](#key-server-configuration-files).

### HSM-Konfiguration {#section_13A19E3E32934C5FA00AEF621F369877}

Wenn Sie zum Speichern Ihrer Serverberechtigungen ein HSM verwenden möchten, müssen Sie die privaten Schlüssel und Zertifikate auf das HSM laden und eine *pkcs11.cfg* Konfigurationsdatei. Diese Datei muss sich im *KeyServer.ConfigRoot* Verzeichnis. Siehe `<Primetime DRM Key Server>/configs` -Verzeichnis für eine Beispiel-PKCS 11-Konfigurationsdatei. Informationen zum Format von [!DNL pkcs11.cfg], siehe die Dokumentation zum Sun PKCS11-Provider .

Um sicherzustellen, dass die Konfigurationsdateien für HSM und Sun PKCS11 ordnungsgemäß konfiguriert sind, können Sie den folgenden Befehl aus dem Ordner verwenden, in dem die [!DNL pkcs11.cfg] Datei befindet sich ( [!DNL keytool] wird mit Java JRE und JDK installiert):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Wenn Ihre Anmeldeinformationen in der Liste angezeigt werden, ist das HSM ordnungsgemäß konfiguriert und der Key Server kann auf die Anmeldeinformationen zugreifen.

## Wichtige Server-Konfigurationsdateien {#key-server-configuration-files}

Für den Primetime-DRM-Schlüsselserver sind zwei Arten von Konfigurationsdateien erforderlich:

* eine globale Konfigurationsdatei, [!DNL flashaccess-keyserver-global.xml]
* eine Mandantenkonfigurationsdatei für jeden Mandanten, [!DNL flashaccess-keyserver-tenant.xml]

Wenn Änderungen an den Konfigurationsdateien vorgenommen werden, muss der Server neu gestartet werden, damit die Änderungen wirksam werden.

Um zu vermeiden, dass Passwörter in unverschlüsseltem Text in den Konfigurationsdateien verfügbar gemacht werden, müssen alle in den globalen und Mandantenkonfigurationsdateien angegebenen Passwörter verschlüsselt werden. Weitere Informationen zum Verschlüsseln von Kennwörtern finden Sie unter [*Password Scrambler* in *Verwenden des Primetime-DRM-Servers für geschütztes Streaming*](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md).

## Konfigurationsordnerstruktur {#configuration-directory-structure}

Die Konfigurationsordner haben die folgende Struktur:

```
KeyServer.ConfigRoot/  
--flashaccess-keyserver-global.xml 
--pkcs11.cfg (optional) 
--faxsks/ 
----tenants/ 
------tenantname/
---------flashaccess-keyserver-tenant.xml 
---------credential.pfx (optional) 
```

## Globale Konfigurationsdatei {#global-configuration-file}

Die [!DNL flashaccess-keyserver-global.xml] Die Konfigurationsdatei enthält Einstellungen, die für alle Mandanten des Key Servers gelten. Diese Datei muss sich unter `KeyServer.ConfigRoot`. Siehe [!DNL configs] -Verzeichnis für eine globale Beispielkonfigurationsdatei. Die globale Konfigurationsdatei enthält Folgendes:

* Protokollierung - Gibt die Protokollierungsstufe und die Häufigkeit des Rollierens von Protokolldateien an.
* HSM-Kennwort - Nur erforderlich, wenn HSM zum Speichern von Server-Anmeldeinformationen verwendet wird.

Siehe die Kommentare in der Beispiel-globalen Konfigurationsdatei unter `<Primetime DRM Key Server>/configs` für weitere Details.

## Mandantenkonfigurationsdateien {#tenant-configuration-files}

Die [!DNL flashaccess-ioskeyserver-tenant.xml] und [!DNL flashaccess-xboxkeyserver-tenant.xml] Konfigurationsdateien enthalten Einstellungen, die für einen bestimmten Mandanten des Primetime-DRM-Schlüsselservers gelten. Jeder Mandant verfügt über eine eigene Instanz dieser Konfigurationsdateien in [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]. Siehe [!DNL configs/faxsks/tenants/sampletenant] -Verzeichnis für eine Beispiel-Mandantenkonfigurationsdatei.

Sie können alle Dateipfade in der Mandantenkonfigurationsdatei entweder als absolute Pfade oder als Pfade relativ zum Konfigurationsverzeichnis des Mandanten angeben ( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]).

Alle Mandantenkonfigurationsdateien umfassen:

* Key Server Credentials - Gibt eine oder mehrere von Adobe ausgestellte Key Server-Anmeldeinformationen (Zertifikat und privater Schlüssel) an. Kann als Pfad zu einem [!DNL .pfx] und ein Kennwort oder einen Alias für eine auf einem HSM gespeicherte Berechtigung. Hier können mehrere solcher Anmeldeinformationen angegeben werden, entweder als Dateipfade, als Schlüssel-Alias oder beides.

Die **iOS** Die Mandantenkonfigurationsdatei enthält:

* Key Delivery Window - (Optional) Gibt das Gültigkeitsfenster des Zeitstempels für die Schlüsselbereitstellungsanfrage an (in Sekunden). Der Standardwert ist 500 Sekunden.

Die **Xbox 360** Die Mandantenkonfigurationsdatei enthält:

* XSTS-Berechtigung - Gibt die Berechtigung des Anwendungsentwicklers an, die zum Entschlüsseln von XSTS-Token verwendet wird
* XSTS-Signaturzertifikat - Gibt das Zertifikat an, das zum Überprüfen der Signatur auf XSTS-Token verwendet wird.
* Packager-Zulassungsliste - Packager-Zertifikate, denen der Key Server vertraut. Wenn keine Paketzertifikate in der Liste enthalten sind, werden alle Packager-Zertifikate als vertrauenswürdig eingestuft.

## Protokolldateien {#log-files}

Die von der Primetime DRM Key Server-Anwendung generierten Protokolldateien ( [!DNL flashaccess-ioskeyserver_*.log] und [!DNL flashaccess-xboxkeyserver_*.log]) befindet sich in dem Verzeichnis, das durch `KeyServer.LogRoot`.

Die Protokolldateien werden nach Client-Typ unterschieden. Pro Client-Typ gibt es zwei Protokolle:

* Ein *Zugriffsprotokoll* - überwacht nur Anfragen und Antworten.
* A *Kontextprotokoll* - Enthält detaillierte Fehlermeldungen und Stacktraces.

## Starten des Key Servers {#starting-the-key-server}

Starten Sie Tomcat, um den Key Server zu starten.
