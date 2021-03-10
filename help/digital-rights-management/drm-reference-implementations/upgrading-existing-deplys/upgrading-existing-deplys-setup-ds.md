---
title: Einrichten eines Domänenservers
description: Einrichten eines Domänenservers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Einrichten eines Domänenservers{#set-up-a-domain-server}

So konfigurieren Sie einen Domänenserver bei einer vorhandenen Lizenzserverinstallation:

1. Öffnen Sie im Ordner [!DNL tomcat/lib] die Datei [!DNL flashaccess-refimpl.properties].
1. Füllen Sie unter der Option `Domain CA certificate` das CA-Domänenzertifikat aus.

   Dieses Zertifikat wird dann für die Annahme der Domänentoken verwendet.
1. Füllen Sie unter der Option `Domain CA credential` die `Domain CA credential certificate (PFX)`-Details aus.

   Dieses Zertifikat wird dann zum Signieren von Domänenzertifikaten und -Token verwendet.
1. Geben Sie den Wert für `DomainServerlURL` an.

   Wenn dieser Wert auf `NULL` festgelegt ist, kann die Domänenauthentifizierung erfolgreich sein. Beim Beitritt zur Domäne kann es jedoch zu einem Fehler in der Verbindungsdomäne kommen.
