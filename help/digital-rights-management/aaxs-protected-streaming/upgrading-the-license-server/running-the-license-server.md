---
description: Um einen Server zu aktualisieren, auf dem Adobe Access Server für geschütztes Streaming ausgeführt wird, ersetzen Sie die auf Ihrem Anwendungsserver bereitgestellte Datei "flashaccess.war"durch die Datei, die mit dem neuesten Adobe-Zugriff geliefert wurde. Wenn Sie die oben beschriebenen neuen Konfigurationsoptionen verwenden möchten, aktualisieren Sie die Datei "flashaccess-tenant.xml"Ihres Servers. Außerdem müssen Sie jsafe.dll oder libjsafe.so auf die Version aktualisieren, die mit dem neuesten Adobe-Access-Paket enthalten ist.
title: Ausführen der Adobe Access Server für geschütztes Streaming
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Ausführen der Adobe Access Server für geschütztes Streaming{#running-the-adobe-access-server-for-protected-streaming}

Um einen Server zu aktualisieren, auf dem Adobe Access Server für geschütztes Streaming ausgeführt wird, ersetzen Sie die auf Ihrem Anwendungsserver bereitgestellte Datei &quot;flashaccess.war&quot;durch die Datei, die mit dem neuesten Adobe-Zugriff geliefert wurde. Wenn Sie die oben beschriebenen neuen Konfigurationsoptionen verwenden möchten, aktualisieren Sie die Datei &quot;flashaccess-tenant.xml&quot;Ihres Servers. Außerdem müssen Sie jsafe.dll oder libjsafe.so auf die Version aktualisieren, die mit dem neuesten Adobe-Access-Paket enthalten ist.

Bevor Sie Adobe Access Server für geschütztes Streaming ausführen, empfiehlt Adobe, dass Sie mithilfe der mit dem Lizenzserver bereitgestellten Dienstprogramme überprüfen, ob die Konfigurationsdateien gültig sind. Weitere Informationen finden Sie unter &quot;[Konfigurationsvalidator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Um Tomcat und den Lizenzserver zu starten, führen Sie &quot;catalina.bat start&quot; oder &quot;catalina.sh start&quot; aus dem Verzeichnis bin von Tomcat aus.

Nachdem der Server gestartet wurde, überprüfen Sie, ob er ordnungsgemäß konfiguriert ist, indem Sie *https:// license-server-host:port/flashaccserver/tenant-name/flashaccess/license/v1* in einem Browserfenster. Wenn die Mandantenkonfiguration erfolgreich geladen wurde, wird eine Bestätigungsmeldung angezeigt.
