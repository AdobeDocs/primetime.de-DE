---
description: Um zu verhindern, dass Benutzer eine Sicherung durchführen und Dateien wiederherstellen, um die Domänenderegistrierung zu umgehen, müssen Sie einige Ansätze zur Domänenverwaltung implementieren.
title: Verwalten von Domänen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Verwalten von Domänen {#managing-domains}

Um zu verhindern, dass Benutzer eine Sicherung durchführen und Dateien wiederherstellen, um die Domänenderegistrierung zu umgehen, müssen Sie einige Ansätze zur Domänenverwaltung implementieren.

Im Folgenden finden Sie einige Ansätze zur Domain-Verwaltung:

* Schränken Sie die Gültigkeitsdauer der Domain-Anmeldedaten ein.

  Clients müssen sich an den Domänenserver wenden, um nach Ablauf der Anmeldeinformationen erneut Domain-Anmeldeinformationen zu erhalten. Zu diesem Zeitpunkt kann der Domänenserver überprüfen, ob der Computer weiterhin berechtigt ist, Mitglied der Domäne zu sein.
* Führen Sie jedes Mal, wenn ein Benutzer deregisters, einen Rollover über die Domänenschlüssel aus.

  Der Lizenzserver sollte nur Lizenzen für Clients mit dem neuesten Domain-Schlüssel ausstellen. Bei diesem Ansatz wird davon ausgegangen, dass sich der Lizenzserver mit dem Domänenserver abstimmen kann, um zu erfahren, welcher Schlüssel der neueste ist. Wenn Sie den Umstieg über die Domänenschlüssel durchführen, wird ein neues Schlüsselpaar für die Domäne generiert. Wenn Sie die Schlüssel für eine Domäne aktualisieren, erhöhen Sie die Schlüsselversion in `generateDomainCredential`.
* Wenn der Domänenserver mit dem Lizenzserver identisch ist, kann der Server den Rollback-Zähler verwenden, um eine Sicherung und Wiederherstellung zu erkennen.

  Weitere Informationen finden Sie unter [Verarbeitung von Adobe Primetime DRM-Anfragen](../../protecting-content/implementing-the-license-server/processing-drm-requests.md).
