---
seo-title: Java-Systemeigenschaften
title: Java-Systemeigenschaften
uuid: ad1f3d9b-7d95-4e19-a0f8-fd7d4dd4dc32
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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

