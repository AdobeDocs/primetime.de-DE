---
title: Überblick über das Bereitstellen des Adobe Access Server für geschütztes Streaming
description: Überblick über das Bereitstellen des Adobe Access Server für geschütztes Streaming
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Adobe Access Server für geschütztes Streaming bereitstellen - Überblick {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Bevor Sie das Adobe Access Server für geschütztes Streaming bereitstellen, stellen Sie sicher, dass Sie die im Abschnitt &quot;Anforderungen&quot;aufgelisteten Versionen von Java und Tomcat installiert haben.

Das Adobe Access Server for Protected Streaming-Paket enthält [!DNL flashaccesserver.war]. Um diese WAR-Datei bereitzustellen, kopieren Sie sie in den Ordner [!DNL webapps] von Tomcat. Wenn Sie die WAR-Datei bereits bereitgestellt haben, müssen Sie möglicherweise den entpackten WAR-Ordner ( [!DNL flashaccessserver] im Ordner [!DNL webapps] von Tomcat) manuell löschen. Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die Datei [!DNL server.xml] im Ordner [!DNL conf] von Tomcat und setzen Sie das `unpackWARs`-Attribut auf `false`.

>[!NOTE]
>
>Wenn Sie Tomcat so konfiguriert haben, dass er [!DNL commons-logging.jar] in den Systemclasspath einbezieht (für das Adobe Access Server für das geschützte Streaming nicht erforderlich), muss die Verwendung von Log4J für die Verwendung von Commons-Logging konfiguriert werden.

Der Server verwendet optional eine plattformspezifische Bibliothek ( [!DNL jsafe.dll] unter Microsoft Windows oder [!DNL libjsafe.so] unter Linux), um eine optimale Leistung zu erzielen. Kopieren Sie die entsprechende Plattformbibliothek von [!DNL thirdparty/cryptoj/]*platform* in einen Speicherort, der durch die Variable `PATH` Umgebung (oder `LD_LIBRARY_PATH` unter Linux) angegeben wird.

>[!NOTE]
>
>Die 64-Bit-Version sollte nur verwendet werden, wenn sowohl das Betriebssystem als auch JDK 64-Bit unterstützen, andernfalls die 32-Bit-Version.

