---
seo-title: Übersicht über die Bereitstellung des Primetime-DRM-Key-Servers
title: Übersicht über die Bereitstellung des Primetime-DRM-Key-Servers
uuid: 86630675-c15d-4f32-8212-d7343f4f92e0
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---


# Primetime DRM Key Server {#deploy-the-primetime-drm-key-server} bereitstellen

Bevor Sie den Primetime DRM Key Server bereitstellen, stellen Sie sicher, dass Sie die erforderlichen Java- und Tomcat-Versionen installiert haben. Siehe [DRM Key Server Requirements](../../digital-rights-management/using-the-drm-key-server/requirements.md).

Der Primetime-DRM Key Server-Download enthält [!DNL faxsks.war]. Um diese WAR-Datei bereitzustellen, kopieren Sie die Datei in den Ordner [!DNL webapps] von Tomcat. Wenn Sie die WAR-Datei bereits bereitgestellt haben, müssen Sie möglicherweise den entpackten WAR-Ordner [!DNL faxsks] im Ordner [!DNL webapps] von Tomcat manuell löschen. Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die Datei [!DNL server.xml] im Ordner [!DNL conf] von Tomcat und setzen Sie das `unpackWARs`-Attribut auf `false`.

Der Primetime-DRM-Key-Server verwendet optional eine plattformspezifische Bibliothek (`jsafe.dll` unter Windows oder `libjsafe.so` unter Linux), um die Leistung zu verbessern. Kopieren Sie die entsprechende Bibliothek für Ihre Plattform von `thirdparty/cryptoj/platform` in einen Speicherort, der durch die Variable `PATH` Umgebung (oder `LD_LIBRARY_PATH` unter Linux) angegeben wird.

>[!NOTE]
>
>Die 64-Bit-Version der [!DNL jsafe]-Bibliothek sollte nur verwendet werden, wenn sowohl das Betriebssystem als auch JDK 64-Bit unterstützen, andernfalls die 32-Bit-Version.

## SSL-Konfiguration {#ssl-configuration}

SSL ist für Remote HTTPS-Versand erforderlich. Die SSL-Verbindungen können vom Anwendungsserver (d. h. durch Konfiguration von SSL in Tomcat) oder auf einem anderen Server (z. B. einem Lastenausgleich, einem SSL-Beschleuniger oder Apache) verarbeitet werden. Für den Remote-HTTPS-Versand ist eine SSL-Verbindung erforderlich. Der Server benötigt ein SSL-Zertifikat, das von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt wurde.

Es gibt verschiedene Optionen zum Konfigurieren von SSL. Im Folgenden finden Sie Beispiele für die Konfiguration von SSL mit Clientauthentifizierung in Apache und Tomcat.

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

Das folgende Beispiel zeigt die Tomcat SSL-Konfiguration. So generieren Sie Zertifikat- und Schlüsseldateien:

```
Generate key:  
 openssl genrsa -des3 -out server.key 1024 
Generate CSR: 
 openssl req -new -key server.key -out server.csr 
Generate Certificate: 
 openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.cer
```

Wenn Sie nach dem allgemeinen Namen gefragt werden, verwenden Sie den FQDN (FQDN) Ihres Servers.

Kopieren Sie [!DNL server.cer] und [!DNL server.key] in den Tomcat-Ordner. Geben Sie den folgenden Connector in [!DNL conf/server.xml] an:

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

Sie haben die Möglichkeit, die folgenden beiden Java-Systemeigenschaften festzulegen, um den Speicherort der Konfigurations- und Protokolldateien für den Primetime DRM Key Server zu ändern:

* `KeyServer.ConfigRoot` - Dieser Ordner enthält alle Konfigurationsdateien für den Primetime DRM Key Server. Weitere Informationen zum Inhalt dieser Dateien finden Sie unter [Key Server configuration files](#key-server-configuration-files). Ist dies nicht der Fall, ist der Standardwert [!DNL CATALINA_BASE/keyserver].

* `KeyServer.LogRoot` - Dies ist ein Protokollordner, der iOS Key Server-Anwendungsprotokolle enthält. Ist dies nicht der Fall, ist die Standardeinstellung die gleiche wie `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot` - Dies ist ein Protokollordner, der die Protokolle der Xbox-Schlüsselserver-Anwendung enthält. Ist dies nicht der Fall, ist der Standardwert identisch mit `KeyServer.ConfigRoot`.

Wenn Sie [!DNL catalina.bat] oder [!DNL catalina.sh] für Beginn Tomcat verwenden, können diese Systemeigenschaften problemlos mit der Variablen `JAVA_OPTS` der Umgebung eingestellt werden. Alle hier festgelegten Java-Optionen werden beim Start von Tomcat verwendet. Beispiel:

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Primetime-DRM-Anmeldeinformationen {#primetime-drm-credentials}

Zur Verarbeitung von Schlüsselanforderungen von Primetime DRM iOS- und Xbox 360-Clients muss der Primetime-DRM-Schlüsselserver mit einem von der Adobe ausgestellten Berechtigungssatz konfiguriert werden. Diese Anmeldeinformationen können entweder in PKCS#12-Dateien ( [!DNL .pfx]) oder in HSM-Dateien gespeichert werden.

Die [!DNL .pfx]-Dateien können sich an einer beliebigen Stelle befinden. Zur einfachen Konfiguration empfiehlt es sich jedoch, die [!DNL .pfx]-Dateien im Konfigurationsverzeichnis des Mandanten zu platzieren. Weitere Informationen finden Sie unter [Key Server configuration files](#key-server-configuration-files).

### HSM-Konfiguration {#section_13A19E3E32934C5FA00AEF621F369877}

Wenn Sie Ihre Serverberechtigungen mit einem HSM speichern möchten, müssen Sie die privaten Schlüssel und Zertifikate auf das HSM laden und eine Konfigurationsdatei *pkcs11.cfg* erstellen. Diese Datei muss sich im Ordner *KeyServer.ConfigRoot* befinden. Eine Beispielkonfigurationsdatei für PKCS 11 finden Sie im Ordner `<Primetime DRM Key Server>/configs`. Informationen zum Format von [!DNL pkcs11.cfg] finden Sie in der Sun PKCS11 Provider-Dokumentation.

Um sicherzustellen, dass die HSM- und Sun PKCS11-Konfigurationsdateien ordnungsgemäß konfiguriert sind, können Sie den folgenden Befehl aus dem Ordner verwenden, in dem sich die [!DNL pkcs11.cfg]-Datei befindet ( [!DNL keytool] wird mit Java JRE und JDK installiert):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Wenn Ihre Anmeldedaten in der Liste angezeigt werden, ist das HSM korrekt konfiguriert und der Schlüsselserver kann auf die Anmeldeinformationen zugreifen.

## Key Server-Konfigurationsdateien {#key-server-configuration-files}

Der Primetime-DRM-Key-Server erfordert zwei Arten von Konfigurationsdateien:

* Eine globale Konfigurationsdatei, [!DNL flashaccess-keyserver-global.xml]
* Eine Mandant-Konfigurationsdatei für jeden Mandanten, [!DNL flashaccess-keyserver-tenant.xml]

Wenn Änderungen an den Konfigurationsdateien vorgenommen werden, muss der Server neu gestartet werden, damit die Änderungen wirksam werden.

Um zu vermeiden, dass Passwörter in unverschlüsseltem Text in den Konfigurationsdateien verfügbar gemacht werden, müssen alle in den Konfigurationsdateien für Global und Mandant angegebenen Passwörter verschlüsselt sein. Weitere Informationen zum Verschlüsseln von Kennwörtern finden Sie unter [*Kennwort-Scrambler* in *Verwenden des Primetime-DRM-Servers für geschütztes Streaming*](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md).

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

Die Konfigurationsdatei [!DNL flashaccess-keyserver-global.xml] enthält Einstellungen, die für alle Mieter des Schlüsselservers gelten. Diese Datei muss sich unter `KeyServer.ConfigRoot` befinden. Im Ordner [!DNL configs] finden Sie eine globale Konfigurationsdatei. Die globale Konfigurationsdatei enthält Folgendes:

* Protokollierung - Gibt die Protokollierungsstufe und die Häufigkeit des Rollovers von Protokolldateien an.
* HSM-Kennwort: Nur erforderlich, wenn zum Speichern von Serverberechtigungen ein HSM verwendet wird.

Weitere Informationen finden Sie in den Kommentaren in der Beispiel-globalen Konfigurationsdatei unter `<Primetime DRM Key Server>/configs`.

## Mandantenkonfigurationsdateien {#tenant-configuration-files}

Die Konfigurationsdateien [!DNL flashaccess-ioskeyserver-tenant.xml] und [!DNL flashaccess-xboxkeyserver-tenant.xml] enthalten Einstellungen, die für einen bestimmten Mieter des Primetime-DRM-Schlüsselservers gelten. Jeder Mandant hat seine eigene Instanz dieser Konfigurationsdateien in [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]. Eine Beispielkonfigurationsdatei für Mandanten finden Sie im Ordner [!DNL configs/faxsks/tenants/sampletenant].

Sie können alle Dateipfade in der Mietkonfigurationsdatei entweder als absolute Pfade oder als Pfade relativ zum Konfigurationsverzeichnis des Mandanten ( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]) angeben.

Alle Mandant-Konfigurationsdateien umfassen:

* Key Server Credentials - Gibt eine oder mehrere von der Adobe ausgestellte Key Server-Anmeldeinformationen (Zertifikat und privater Schlüssel) an. Kann als Pfad zu einer [!DNL .pfx]-Datei und einem Kennwort oder als Alias für eine auf einem HSM gespeicherte Berechtigung angegeben werden. Hier können mehrere solcher Berechtigungen angegeben werden, entweder als Dateipfade oder als Schlüssel-Aliase oder beides.

Die Konfigurationsdatei für den Mandanten von **iOS** enthält:

* Fenster &quot;Key Versand&quot;- (Optional) Gibt das Zeitstempelfenster für die Schlüsselanforderung für den Versand (in Sekunden) an. Der Standardwert ist 500 Sekunden.

Die Konfigurationsdatei für **Xbox 360**-Mandanten enthält:

* XSTS-Berechtigung - Gibt die Berechtigung des Anwendungsentwicklers zum Entschlüsseln von XSTS-Tokens an.
* XSTS-Signaturzertifikat - Gibt das Zertifikat an, das zum Überprüfen der Signatur auf XSTS-Token verwendet wird.
* Packager-Zulassungsliste - Packager-Zertifikate, denen der Schlüsselserver vertraut. Wenn in der Liste keine Packager-Zertifikate enthalten sind, werden alle Packager-Zertifikate als vertrauenswürdig eingestuft.

## Protokolldateien {#log-files}

Die Protokolldateien, die von der Primetime DRM Key Server-Anwendung ( [!DNL flashaccess-ioskeyserver_*.log] und [!DNL flashaccess-xboxkeyserver_*.log]) generiert werden, befinden sich im Ordner, der von `KeyServer.LogRoot` angegeben wird.

Die Protokolldateien werden nach Clienttyp unterschieden. Es gibt zwei Protokolle pro Clienttyp:

* Ein *Zugriffsprotokoll* - überwacht nur Anfragen und Antworten.
* A *context log* - Enthält detaillierte Fehlermeldungen und Stapelspuren.

## Starten des Schlüsselservers {#starting-the-key-server}

Beginn Tomcat zum Beginn des Schlüsselservers.