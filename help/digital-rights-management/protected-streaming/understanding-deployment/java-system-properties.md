---
description: Es gibt mehrere Java-Systemeigenschaften, die Sie auf dem Lizenzserver konfigurieren können, um den Speicherort der Konfigurations- und Protokolldateien zu steuern.
title: Java-Systemeigenschaften
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Java-Systemeigenschaften{#java-system-properties}

Es gibt mehrere Java-Systemeigenschaften, die Sie auf dem Lizenzserver konfigurieren können, um den Speicherort der Konfigurations- und Protokolldateien zu steuern.

Sie können optional die folgenden Java-Systemeigenschaften konfigurieren:

* *`LicenseServer.ConfigRoot`* — Name des Ordners, der die Konfigurationsdateien für den Lizenzserver enthält.

  Siehe *Konfigurationsdateien des Lizenzservers* für Details zum Inhalt dieser Dateien. Wenn der Standardwert nicht konfiguriert ist, lautet `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot* — Name der [!DNL logs] Verzeichnis, in dem sich die Anwendungsprotokolle des Lizenzservers befinden. Wenn Sie den Namen dieses Ordners nicht geändert haben, wird der Name dieses Ordners als *LicenseServer.ConfigRoot* Standardmäßig.

Wenn Sie die [!DNL catalina.bat] oder [!DNL catalina.sh] -Datei, um Tomcat zu starten, können Sie die Systemeigenschaften mit der `JAVA_OPTS` Umgebungsvariable. Alle Java-Optionen, die Sie konfigurieren, werden beim Start von Tomcat automatisch angewendet.

Sie können beispielsweise die `JAVA_OPTS` Umgebungsvariable wie folgt:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```
