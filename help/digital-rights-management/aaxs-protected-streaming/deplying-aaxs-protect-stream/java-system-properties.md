---
title: Java-Systemeigenschaften
description: Java-Systemeigenschaften
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Java-Systemeigenschaften {#java-system-properties}

Die folgenden beiden Java-Systemeigenschaften können optional festgelegt werden, um den Speicherort der Konfiguration und Protokolldateien für den Lizenzserver zu ändern:

* *LicenseServer.ConfigRoot* — Verzeichnis mit allen Konfigurationsdateien für den Lizenzserver. Weitere Informationen zum Inhalt dieser Dateien finden Sie unter[Konfigurationsdateien des Lizenzservers](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)&quot;. Wenn nicht festgelegt, ist der Standardwert *CATALINA_BASE/licenseserver*.
* *LicenseServer.LogRoot* — Verzeichnis des Ordners &quot;logs&quot;, in dem die Anwendungsprotokolle des Lizenzservers geschrieben sind. Wenn nicht festgelegt, ist der Standardwert *LicenseServer.ConfigRoot*.

Wenn Sie [!DNL catalina.bat] oder [!DNL catalina.sh] um Tomcat zu starten, können diese Systemeigenschaften einfach mithilfe der `JAVA_OPTS` Umgebungsvariable. Alle hier festgelegten Java-Optionen werden beim Start von Tomcat verwendet. Beispiel:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```
