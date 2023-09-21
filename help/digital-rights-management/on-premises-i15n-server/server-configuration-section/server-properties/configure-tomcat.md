---
title: Tomcat konfigurieren
description: Tomcat konfigurieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Tomcat konfigurieren{#configure-tomcat}

Ändern Sie auf dem Individualisierungsserver die [!DNL conf/server.xml] -Datei, um zusätzliche Informationen in das Zugriffsprotokoll aufzunehmen. Sie können diese Informationen zu Berichtszwecken verwenden.

1. Suchen Sie die Konfiguration für die `AccessLogValve` in [!DNL server.xml] und ändern Sie das Muster wie folgt:

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` speichert den Wert der `x-forwarded-for` -Kopfzeile. Wenn Sie einen Apache-Reverse-Proxy verwenden, um Anforderungen an den Tomcat-Server weiterzuleiten, enthält dieser Header die IP-Adresse des ursprünglichen Clients, während `%h` erfasst die IP-Adresse des Apache-Servers. `%{request-id}r` erfasst die Anforderungskennung, die der im Protokoll der Individualisierungsanwendung enthaltenen Anforderungs-ID entspricht.

1. Bearbeiten [!DNL conf/server.xml] und legen Sie die `unpackwars` -Eigenschaft auf &quot;false&quot;gesetzt.

   Sowohl für die Individualisierungs- als auch für die Schlüsselgenerierungsserver ist es empfehlenswert, die [!DNL conf/server.xml] und legen Sie die `unpackwars` Eigenschaft auf `false`. Andernfalls müssen Sie beim Aktualisieren der WAR-Dateien möglicherweise auch die entpackten WAR-Ordner bereinigen.

>[!NOTE]
>
>Zukünftige DRM-Clients erfordern, dass Sie den für Tomcat verfügbaren CORS-Filter (Cross-Origin Resource Sharing) aktivieren und konfigurieren. Derzeit ist dies für DRM-Clients nicht erforderlich.
