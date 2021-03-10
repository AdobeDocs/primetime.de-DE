---
title: Java-Systemeigenschaften
description: Java-Systemeigenschaften
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Java-Systemeigenschaften {#java-system-properties}

Die folgenden beiden Java-Systemeigenschaften können optional festgelegt werden, um den Speicherort der Konfigurations- und Protokolldateien für den Lizenzserver zu ändern:

* *LicenseServer.ConfigRoot* — Verzeichnis, das alle Konfigurationsdateien für den Lizenzserver enthält. Weitere Informationen zum Inhalt dieser Dateien finden Sie unter &quot;[Konfigurationsdateien des Lizenzservers](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)&quot;. Ist dies nicht der Fall, ist der Standardwert *CATALINA_BASE/licenseserver*.
* *LicenseServer.LogRoot* — Verzeichnis des &quot;logs&quot;-Ordners, in dem die Anwendungsprotokolle des Lizenzservers geschrieben werden. Ist dies nicht der Fall, ist der Standardwert *LicenseServer.ConfigRoot*.

Wenn Sie [!DNL catalina.bat] oder [!DNL catalina.sh] für Beginn Tomcat verwenden, können diese Systemeigenschaften problemlos mit der Variablen `JAVA_OPTS` der Umgebung eingestellt werden. Alle hier festgelegten Java-Optionen werden beim Start von Tomcat verwendet. Beispiel:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

