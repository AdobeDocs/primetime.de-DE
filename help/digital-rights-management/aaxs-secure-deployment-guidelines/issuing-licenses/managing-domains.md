---
title: Verwalten von Domänen
description: Verwalten von Domänen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Verwalten von Domänen{#managing-domains}

Um zu verhindern, dass Benutzer ihre Dateien sichern und wiederherstellen können, um die Domänenderegistrierung zu umgehen, wird empfohlen, einen der folgenden Ansätze für die Domänenverwaltung zu implementieren:

* Schränken Sie die Gültigkeitsdauer der Domain-Anmeldedaten ein. Clients müssen sich an den Domänenserver wenden, um nach Ablauf der Domain-Anmeldeinformationen erneut zu erfassen. Zu diesem Zeitpunkt kann der Domänenserver sicherstellen, dass der Computer weiterhin berechtigt ist, Mitglied der Domäne zu sein.
* Rollover der Domänenschlüssel jedes Mal, wenn ein Benutzer die Registrierung aufhebt. Der Lizenzserver sollte nur Lizenzen für Clients mit dem neuesten Domain-Schlüssel ausstellen. Dies setzt voraus, dass der Lizenzserver sich mit dem Domain Server abstimmen kann, um zu erfahren, welcher Schlüssel der neueste ist. Wenn Sie den Umstieg über die Domänenschlüssel durchführen, wird ein neues Schlüsselpaar für die Domäne generiert. Wenn Sie die Schlüssel für eine bestimmte Domäne aktualisieren, müssen Sie die Schlüsselversion in `generateDomainCredential`. Weitere Informationen zur Implementierung eines Schlüsselaktualisierungs-Programms finden Sie unter *RefImplDomainReqHandler* in der Referenzimplementierung.
* Wenn der Domain-Server mit dem Lizenzserver identisch ist, kann der Server den Rollback-Zähler verwenden, um Backup und Wiederherstellung zu erkennen. Siehe *Verarbeitung von Adobe-Zugriffsanfragen *in *Verwenden des Adobe Access SDK zum Schutz von Inhalten.*
