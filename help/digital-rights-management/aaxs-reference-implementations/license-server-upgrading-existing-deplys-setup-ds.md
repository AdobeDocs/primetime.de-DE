---
title: Einrichten eines Domänenservers
description: Einrichten eines Domänenservers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Einrichten eines Domänenservers {#set-up-a-domain-server}

So konfigurieren Sie den Domänenserver bei einer vorhandenen Lizenzserverinstallation:

1. Öffnen Sie die Datei [!DNL flashaccess-refimpl.properties] unter [!DNL tomcat/lib].

1. Geben Sie unter der Option `Domain CA certificate` die Details zum CA-Zertifikat der Domäne ein. Dieses Zertifikat wird für die Annahme der Domänentoken verwendet.
1. Geben Sie unter der Option `Domain CA credential` die `Domain CA credential certificate (PFX)`-Details ein. Dieses Zertifikat wird zum Signieren von Domänenzertifikaten und -Token verwendet.

1. Geben Sie den Wert für `DomainServerlURL` an. Wenn dieser Wert NULL ist, kann die Domänenauthentifizierung erfolgreich sein. Beim Betreten der Domäne wird jedoch ein Fehler wegen einer Verbindungsdomäne ausgegeben.

