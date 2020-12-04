---
description: 'null'
seo-description: 'null'
seo-title: Einrichten eines Domänenservers
title: Einrichten eines Domänenservers
uuid: bf85305e-9a00-4bc0-ba36-c870979456e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '95'
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
