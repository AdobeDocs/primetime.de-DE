---
description: Um einen Server zu aktualisieren, auf dem Adobe Access Server für geschütztes Streaming ausgeführt wird, ersetzen Sie die auf Ihrem Anwendungsserver bereitgestellte Datei "flashAccessserver.war"durch die Datei, die im neuesten Adobe Access enthalten ist. Wenn Sie die oben beschriebenen neuen Konfigurationsoptionen verwenden möchten, aktualisieren Sie die Datei "flashaccess-tenant.xml"Ihres Servers. Außerdem müssen Sie die Version jsafe.dll oder libjsafe.so auf die Version aktualisieren, die in der neuesten Version von Adobe Access enthalten ist.
seo-description: Um einen Server zu aktualisieren, auf dem Adobe Access Server für geschütztes Streaming ausgeführt wird, ersetzen Sie die auf Ihrem Anwendungsserver bereitgestellte Datei "flashAccessserver.war"durch die Datei, die im neuesten Adobe Access enthalten ist. Wenn Sie die oben beschriebenen neuen Konfigurationsoptionen verwenden möchten, aktualisieren Sie die Datei "flashaccess-tenant.xml"Ihres Servers. Außerdem müssen Sie die Version jsafe.dll oder libjsafe.so auf die Version aktualisieren, die in der neuesten Version von Adobe Access enthalten ist.
seo-title: Ausführen des Adobe Access Servers für geschütztes Streaming
title: Ausführen des Adobe Access Servers für geschütztes Streaming
uuid: 3819500d-ad2f-49eb-8aa4-e50a55461608
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Ausführen des Adobe Access Servers für geschütztes Streaming{#running-the-adobe-access-server-for-protected-streaming}

Um einen Server zu aktualisieren, auf dem Adobe Access Server für geschütztes Streaming ausgeführt wird, ersetzen Sie die auf Ihrem Anwendungsserver bereitgestellte Datei &quot;flashAccessserver.war&quot;durch die Datei, die im neuesten Adobe Access enthalten ist. Wenn Sie die oben beschriebenen neuen Konfigurationsoptionen verwenden möchten, aktualisieren Sie die Datei &quot;flashaccess-tenant.xml&quot;Ihres Servers. Außerdem müssen Sie die Version jsafe.dll oder libjsafe.so auf die Version aktualisieren, die in der neuesten Version von Adobe Access enthalten ist.

Bevor Sie Adobe Access Server for Protected Streaming ausführen, empfiehlt Adobe, dass Sie überprüfen, ob die Konfigurationsdateien gültig sind, indem Sie die Hilfsprogramme verwenden, die mit dem Lizenzserver bereitgestellt werden. Weitere Informationen finden Sie unter &quot;[Konfigurationsvalidator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Um Tomcat und den Lizenzserver zu Beginn, führen Sie &quot;catalina.bat Beginn&quot;oder &quot;catalina.sh Beginn&quot;aus dem Verzeichnis &quot;bin&quot;von Tomcat aus.

Nachdem der Server gestartet wurde, überprüfen Sie, ob er ordnungsgemäß konfiguriert ist, indem Sie ** https:// in einem Browserfenster öffnen. Wenn die Mandantenkonfiguration erfolgreich geladen wurde, wird eine Bestätigungsmeldung angezeigt.
