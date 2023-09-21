---
title: Einrichten eines Domänenservers
description: Einrichten eines Domänenservers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Einrichten eines Domänenservers{#set-up-a-domain-server}

So konfigurieren Sie einen Domänenserver für eine bestehende Installation des Lizenzservers:

1. Im [!DNL tomcat/lib] Verzeichnis, öffnen Sie die [!DNL flashaccess-refimpl.properties] -Datei.
1. Unter dem `Domain CA certificate` -Option das Zertifikat der Zertifizierungsstelle für die Domäne ausfüllen.

   Dieses Zertifikat wird dann für die Akzeptanz der Domänen-Token verwendet.
1. Unter dem `Domain CA credential` -Option, beenden Sie die `Domain CA credential certificate (PFX)` Details.

   Dieses Zertifikat wird dann zum Signieren von Domänenzertifikaten und -Token verwendet.
1. Geben Sie den Wert für `DomainServerlURL`.

   Wenn dieser Wert auf `NULL`, kann die Domänenauthentifizierung erfolgreich sein. Beim Beitritt zur Domäne kann es jedoch zu einem Fehler bei der Join-Domäne kommen.
