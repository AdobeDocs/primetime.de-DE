---
title: Einrichten eines Domänenservers
description: Einrichten eines Domänenservers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Einrichten eines Domänenservers {#set-up-a-domain-server}

Führen Sie die folgenden Aufgaben aus, um den Domänenserver für eine bestehende Installation des Lizenzservers zu konfigurieren:

1. Öffnen Sie die [!DNL flashaccess-refimpl.properties] Datei unter [!DNL tomcat/lib].

1. Unter dem `Domain CA certificate` Geben Sie die Details zum Zertifikat der Zertifizierungsstelle für die Domäne ein. Dieses Zertifikat wird für die Akzeptanz der Domänen-Token verwendet.
1. Unter dem `Domain CA credential` -Option, füllen Sie die `Domain CA credential certificate (PFX)` Details. Dieses Zertifikat wird zum Signieren von Domänenzertifikaten und -Token verwendet.

1. Geben Sie den Wert für `DomainServerlURL`. Wenn dieser Wert NULL ist, kann die Domänenauthentifizierung erfolgreich sein. Beim Beitritt zur Domäne tritt jedoch ein Fehler bei der Join-Domäne auf.
