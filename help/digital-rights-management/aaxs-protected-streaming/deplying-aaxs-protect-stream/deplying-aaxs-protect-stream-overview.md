---
seo-title: Übersicht über das Bereitstellen des Adobe Access Servers für geschütztes Streaming
title: Übersicht über das Bereitstellen des Adobe Access Servers für geschütztes Streaming
uuid: 48a7e452-520a-4ff8-97e9-11210221256d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Übersicht über das Bereitstellen des Adobe Access Servers für geschütztes Streaming {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Bevor Sie Adobe Access Server für geschütztes Streaming bereitstellen, stellen Sie sicher, dass Sie die im Abschnitt &quot;Anforderungen&quot;aufgelisteten Versionen von Java und Tomcat installiert haben.

Das Adobe Access Server for Protected Streaming-Paket enthält [!DNL flashaccesserver.war]. Um diese WAR-Datei bereitzustellen, kopieren Sie sie in den [!DNL webapps] Ordner von Tomcat. Wenn Sie die WAR-Datei bereits bereitgestellt haben, müssen Sie möglicherweise den entpackten WAR-Ordner ( [!DNL flashaccessserver] im [!DNL webapps] Verzeichnis von Tomcat) manuell löschen. Um zu verhindern, dass Tomcat WAR-Dateien entpackt, bearbeiten Sie die [!DNL server.xml] Datei im [!DNL conf] Verzeichnis von Tomcat und setzen Sie das `unpackWARs` Attribut auf `false`.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Wenn Sie Tomcat so konfiguriert haben, dass er [!DNL commons-logging.jar] in den Systemklasspath eingeschlossen wird (nicht erforderlich für den Adobe Access Server für geschütztes Streaming), muss die gemeinsame Protokollierung für die Verwendung von Log4J konfiguriert werden.

Der Server verwendet optional eine plattformspezifische Bibliothek ( [!DNL jsafe.dll] unter Microsoft Windows oder [!DNL libjsafe.so] unter Linux), um eine optimale Leistung zu erzielen. Kopieren Sie die entsprechende Bibliothek für Ihre Plattform von der [!DNL thirdparty/cryptoj/]*Plattform *an einen Speicherort, der durch die Variable &quot;`PATH`Umgebung&quot;(oder`LD_LIBRARY_PATH`unter Linux) angegeben wird.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Die 64-Bit-Version sollte nur verwendet werden, wenn sowohl das Betriebssystem als auch JDK 64-Bit unterstützen, andernfalls die 32-Bit-Version.

