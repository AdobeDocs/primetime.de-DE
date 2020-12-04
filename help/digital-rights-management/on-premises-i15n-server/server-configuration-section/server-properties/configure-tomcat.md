---
seo-title: Tomcat konfigurieren
title: Tomcat konfigurieren
uuid: 5f23aa33-29d7-4b41-87a4-59dc5b433de4
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# Tomcat{#configure-tomcat} konfigurieren

Ändern Sie auf dem Individualisierungsserver die Datei [!DNL conf/server.xml] von Tomcat, um weitere Informationen in das Zugriffsprotokoll aufzunehmen. Sie können diese Informationen zum Berichte verwenden.

1. Suchen Sie die Konfiguration für `AccessLogValve` in [!DNL server.xml] und ändern Sie das Muster wie folgt:

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` erfasst den Wert der  `x-forwarded-for` Kopfzeile. Wenn Sie einen umgekehrten Apache-Proxy verwenden, um Anforderungen an den Tomcat-Server zu senden, enthält dieser Header die IP-Adresse des ursprünglichen Clients, während `%h` die IP-Adresse des Apache-Servers aufzeichnet. `%{request-id}r` erfasst die Anforderungs-ID, die der Anforderungs-ID im Anwendungsprotokoll Individualisierung entspricht.

1. Bearbeiten Sie [!DNL conf/server.xml] und setzen Sie die `unpackwars`-Eigenschaft auf false.

   Sowohl bei den Servern für die Personalisierung als auch bei der Schlüsselgenerierung sollten Sie [!DNL conf/server.xml] bearbeiten und die `unpackwars`-Eigenschaft auf `false` setzen. Andernfalls müssen Sie beim Aktualisieren der WAR-Dateien möglicherweise auch die entpackten WAR-Ordner bereinigen.

>[!NOTE]
>
>Zukünftige DRM-Clients erfordern, dass Sie den für Tomcat verfügbaren CORS-Filter (Cross-Herkunft Resource Sharing) aktivieren und konfigurieren. Zurzeit haben keine DRM-Clients diese Anforderung.

