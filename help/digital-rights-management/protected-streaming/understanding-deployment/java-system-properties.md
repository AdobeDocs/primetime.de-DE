---
description: Es gibt mehrere Java-Systemeigenschaften, die Sie auf dem Lizenzserver konfigurieren können, um den Speicherort der Konfigurations- und Protokolldateien zu steuern.
seo-description: Es gibt mehrere Java-Systemeigenschaften, die Sie auf dem Lizenzserver konfigurieren können, um den Speicherort der Konfigurations- und Protokolldateien zu steuern.
seo-title: Java-Systemeigenschaften
title: Java-Systemeigenschaften
uuid: d8c72359-bf61-47e0-9cd5-b21225d5fe49
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Java-Systemeigenschaften{#java-system-properties}

Es gibt mehrere Java-Systemeigenschaften, die Sie auf dem Lizenzserver konfigurieren können, um den Speicherort der Konfigurations- und Protokolldateien zu steuern.

Sie können optional die folgenden Java-Systemeigenschaften konfigurieren:

* *`LicenseServer.ConfigRoot`* — Name des Ordners, der die Konfigurationsdateien für den Lizenzserver enthält.

   Weitere Informationen zum Inhalt dieser Dateien finden Sie unter *Konfigurationsdateien des Lizenzservers*. Wenn der Standardwert nicht konfiguriert ist, ist `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot* — Name des  [!DNL logs] Ordners, in dem sich die Anwendungsprotokolle des Lizenzservers befinden. Wenn Sie den Namen dieses Ordners nicht geändert haben, wird der Name dieses Ordners standardmäßig als *LicenseServer.ConfigRoot* konfiguriert.

Wenn Sie die Datei [!DNL catalina.bat] oder [!DNL catalina.sh] für Beginn Tomcat verwenden, können Sie die Systemeigenschaften mit der Variablen `JAVA_OPTS` &quot;Umgebung&quot;konfigurieren. Alle Java-Optionen, die Sie konfigurieren, werden automatisch angewendet, wenn Tomcat-Beginn.

Sie können beispielsweise die Variable &quot;Umgebung&quot;wie folgt konfigurieren:`JAVA_OPTS`

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

