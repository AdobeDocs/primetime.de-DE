---
title: Übersicht über das Bereitstellen von Adobe Access Server für geschütztes Streaming
description: Übersicht über das Bereitstellen von Adobe Access Server für geschütztes Streaming
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Übersicht über das Bereitstellen von Adobe Access Server für geschütztes Streaming {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Stellen Sie vor der Bereitstellung von Adobe Access Server für geschütztes Streaming sicher, dass Sie die im Abschnitt Anforderungen aufgelisteten Versionen von Java und Tomcat installiert haben.

Das Adobe Access Server for Protected Streaming-Paket umfasst [!DNL flashaccesserver.war]. Um diese WAR-Datei bereitzustellen, kopieren Sie sie in das [!DNL webapps] Verzeichnis. Wenn Sie die WAR-Datei bereits bereitgestellt haben, müssen Sie möglicherweise das entpackte WAR-Verzeichnis ( [!DNL flashaccessserver] in Tomcat [!DNL webapps] Verzeichnis). Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die [!DNL server.xml] -Datei in Tomcat [!DNL conf] und legen Sie `unpackWARs` Attribut `false`.

>[!NOTE]
>
>Wenn Sie Tomcat so konfiguriert haben, dass [!DNL commons-logging.jar] im Systemklasspath (nicht für die Adobe Access Server für geschütztes Streaming erforderlich), muss die gemeinsame Protokollierung für die Verwendung von Log4J konfiguriert werden.

Der Server verwendet optional eine plattformspezifische Bibliothek ( [!DNL jsafe.dll] unter Microsoft Windows oder [!DNL libjsafe.so] auf Linux) für optimale Leistung. Kopieren Sie die entsprechende Bibliothek für Ihre Plattform aus [!DNL thirdparty/cryptoj/]*platform* an einen Ort, der durch die `PATH` Umgebungsvariable (oder `LD_LIBRARY_PATH` auf Linux).

>[!NOTE]
>
>Die 64-Bit-Version sollte nur verwendet werden, wenn sowohl das Betriebssystem als auch JDK 64-Bit unterstützen. Verwenden Sie andernfalls die 32-Bit-Version.
