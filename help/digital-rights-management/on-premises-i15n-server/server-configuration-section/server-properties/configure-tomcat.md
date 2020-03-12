---
seo-title: Tomcat konfigurieren
title: Tomcat konfigurieren
uuid: 5f23aa33-29d7-4b41-87a4-59dc5b433de4
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Tomcat konfigurieren{#configure-tomcat}

Ändern Sie auf dem Individualisierungsserver die [!DNL conf/server.xml] Datei von Tomcat, um weitere Informationen in das Zugriffsprotokoll aufzunehmen. Sie können diese Informationen zum Berichte verwenden.

1. Suchen Sie die Konfiguration für die `AccessLogValve` in [!DNL server.xml] und ändern Sie das Muster wie im Folgenden gezeigt:

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` erfasst den Wert der `x-forwarded-for` Kopfzeile. Wenn Sie einen Apache Reverse-Proxy verwenden, um Anforderungen an den Tomcat-Server zu senden, enthält dieser Header die IP-Adresse des ursprünglichen Clients, während die IP-Adresse des Apache-Servers `%h` aufgezeichnet wird. `%{request-id}r` erfasst die Anforderungs-ID, die der Anforderungs-ID im Anwendungsprotokoll Individualisierung entspricht.

1. Bearbeiten [!DNL conf/server.xml] und die `unpackwars` Eigenschaft auf &quot;false&quot;setzen.

   Sowohl für die Server für die Personalisierung als auch für die Schlüsselgenerierung sollten Sie die [!DNL conf/server.xml] Eigenschaft bearbeiten `unpackwars` und auf `false`. Andernfalls müssen Sie beim Aktualisieren der WAR-Dateien möglicherweise auch die entpackten WAR-Ordner bereinigen.

>[!NOTE]
>
>Zukünftige DRM-Clients erfordern, dass Sie den für Tomcat verfügbaren CORS-Filter (Cross-Herkunft Resource Sharing) aktivieren und konfigurieren. Zurzeit haben keine DRM-Clients diese Anforderung.

