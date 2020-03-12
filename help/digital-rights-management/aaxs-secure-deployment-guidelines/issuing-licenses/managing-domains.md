---
seo-title: Verwalten von Domänen
title: Verwalten von Domänen
uuid: aee02196-8704-46ee-add9-82b371722f0f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verwalten von Domänen{#managing-domains}

Um zu verhindern, dass Benutzer ihre Dateien sichern und wiederherstellen können, um die Domänenderegistrierung zu umgehen, wird empfohlen, einen der folgenden Ansätze für das Domänenmanagement zu implementieren:

* Schränken Sie die Gültigkeitsdauer der Domänenberechtigungen ein. Kunden müssen sich mit dem Domänenserver in Verbindung setzen, um nach Ablauf erneut Domänenberechtigungen zu erwerben. Zu diesem Zeitpunkt kann der Domänenserver sicherstellen, dass der Computer weiterhin berechtigt ist, Mitglied der Domäne zu sein.
* Rollover der Domänenschlüssel jedes Mal, wenn sich ein Benutzer abmeldet. License Server sollte nur Lizenzen für Clients mit dem neuesten Domänenschlüssel ausstellen. Hierbei wird davon ausgegangen, dass sich der Lizenzserver mit dem Domänenserver abstimmen kann, um zu erfahren, welcher Schlüssel der neueste ist. Das Rollieren über die Domänenschlüssel beinhaltet die Generierung eines neuen Schlüsselpaars für die Domäne. Stellen Sie beim Rollover über die Schlüssel für eine bestimmte Domäne sicher, dass Sie die Schlüsselversion in inkrementieren `generateDomainCredential`. Weitere Informationen zur Implementierung eines Schlüsselaktualisierungsservers finden Sie unter *RefImplDomainReqHandler* in der Referenzimplementierung.
* Wenn der Domänenserver mit dem Lizenzserver identisch ist, kann der Server den Rollback-Zähler zum Erkennen von Sicherung und Wiederherstellung verwenden. Siehe *Verarbeitung von Adobe Access-Anfragen *in *Verwenden des Adobe Access-SDK zum Schutz von Inhalten.*

