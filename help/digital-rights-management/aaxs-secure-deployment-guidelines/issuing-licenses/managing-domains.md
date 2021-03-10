---
title: Verwalten von Domänen
description: Verwalten von Domänen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Verwalten von Domänen{#managing-domains}

Um zu verhindern, dass Benutzer ihre Dateien sichern und wiederherstellen können, um die Domänenderegistrierung zu umgehen, wird empfohlen, einen der folgenden Ansätze für das Domänenmanagement zu implementieren:

* Schränken Sie die Gültigkeitsdauer der Domänenberechtigungen ein. Kunden müssen sich mit dem Domänenserver in Verbindung setzen, um nach Ablauf erneut Domänenberechtigungen zu erwerben. Zu diesem Zeitpunkt kann der Domänenserver sicherstellen, dass der Computer weiterhin berechtigt ist, Mitglied der Domäne zu sein.
* Rollover der Domänenschlüssel jedes Mal, wenn sich ein Benutzer abmeldet. License Server sollte nur Lizenzen für Clients mit dem neuesten Domänenschlüssel ausstellen. Hierbei wird davon ausgegangen, dass sich der Lizenzserver mit dem Domänenserver abstimmen kann, um zu erfahren, welcher Schlüssel der neueste ist. Das Rollieren über die Domänenschlüssel beinhaltet die Generierung eines neuen Schlüsselpaars für die Domäne. Stellen Sie beim Rollover über die Schlüssel für eine bestimmte Domäne sicher, dass Sie die Schlüsselversion in `generateDomainCredential` inkrementieren. Weitere Informationen zur Implementierung eines Schlüsselaktualisierungsservers finden Sie unter *RefImplDomainReqHandler* in der Referenzimplementierung.
* Wenn der Domänenserver mit dem Lizenzserver identisch ist, kann der Server den Rollback-Zähler zum Erkennen von Sicherung und Wiederherstellung verwenden. Siehe *Adobe-Zugriffsanfragen für Verarbeitungszwecke *in *Verwenden des Adobe Access SDK zum Inhaltsschutz.*

