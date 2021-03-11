---
description: Damit Benutzer keine Dateien sichern und wiederherstellen können, um die Domänenderegistrierung zu umgehen, müssen Sie einige Domänenverwaltungsansätze implementieren.
title: Verwalten von Domänen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# Verwalten von Domänen {#managing-domains}

Damit Benutzer keine Dateien sichern und wiederherstellen können, um die Domänenderegistrierung zu umgehen, müssen Sie einige Domänenverwaltungsansätze implementieren.

Im Folgenden finden Sie einige Ansätze zum Domänenmanagement:

* Schränken Sie die Gültigkeitsdauer der Domänenberechtigungen ein.

   Kunden müssen sich mit dem Domänenserver in Verbindung setzen, um nach Ablauf der Anmeldeinformationen erneut Domänenberechtigungen zu erhalten. Zu diesem Zeitpunkt kann der Domänenserver überprüfen, ob der Computer weiterhin berechtigt ist, Mitglied der Domäne zu sein.
* Bewegen Sie den Mauszeiger jedes Mal über die Domänenschlüssel, wenn ein Benutzer sich anmeldet.

   License Server sollte nur Lizenzen für Clients mit dem neuesten Domänenschlüssel ausstellen. Bei diesem Ansatz wird davon ausgegangen, dass sich der Lizenzserver mit dem Domänenserver abstimmen kann, um zu erfahren, welcher Schlüssel der neueste ist. Das Rollieren über die Domänenschlüssel beinhaltet die Generierung eines neuen Schlüsselpaars für die Domäne. Wenn Sie die Schlüssel für eine Domäne aktualisieren, inkrementieren Sie die Schlüsselversion in `generateDomainCredential`.
* Wenn der Domänenserver mit dem Lizenzserver identisch ist, kann der Server den Rollback-Zähler verwenden, um eine Sicherung und Wiederherstellung zu erkennen.

   Weitere Informationen finden Sie unter [Adobe Primetime DRM-Anforderungen bearbeiten](../../protecting-content/implementing-the-license-server/processing-drm-requests.md).

