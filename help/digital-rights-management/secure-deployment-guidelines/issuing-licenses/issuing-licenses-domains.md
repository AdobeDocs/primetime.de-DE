---
description: Damit Benutzer keine Dateien sichern und wiederherstellen können, um die Domänenderegistrierung zu umgehen, müssen Sie einige Domänenverwaltungsansätze implementieren.
seo-description: Damit Benutzer keine Dateien sichern und wiederherstellen können, um die Domänenderegistrierung zu umgehen, müssen Sie einige Domänenverwaltungsansätze implementieren.
seo-title: Verwalten von Domänen
title: Verwalten von Domänen
uuid: 30b73e38-d6ed-43c6-89ba-ae8616383779
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Verwalten von Domänen {#managing-domains}

Damit Benutzer keine Dateien sichern und wiederherstellen können, um die Domänenderegistrierung zu umgehen, müssen Sie einige Domänenverwaltungsansätze implementieren.

Im Folgenden finden Sie einige Ansätze zum Domänenmanagement:

* Schränken Sie die Gültigkeitsdauer der Domänenberechtigungen ein.

   Kunden müssen sich mit dem Domänenserver in Verbindung setzen, um nach Ablauf der Anmeldeinformationen erneut Domänenberechtigungen zu erhalten. Zu diesem Zeitpunkt kann der Domänenserver überprüfen, ob der Computer weiterhin berechtigt ist, Mitglied der Domäne zu sein.
* Bewegen Sie den Mauszeiger jedes Mal über die Domänenschlüssel, wenn ein Benutzer sich anmeldet.

   License Server sollte nur Lizenzen für Clients mit dem neuesten Domänenschlüssel ausstellen. Bei diesem Ansatz wird davon ausgegangen, dass sich der Lizenzserver mit dem Domänenserver abstimmen kann, um zu erfahren, welcher Schlüssel der neueste ist. Das Rollieren über die Domänenschlüssel beinhaltet die Generierung eines neuen Schlüsselpaars für die Domäne. Wenn Sie die Schlüssel für eine Domäne aktualisieren, erhöhen Sie die Schlüsselversion in `generateDomainCredential`.
* Wenn der Domänenserver mit dem Lizenzserver identisch ist, kann der Server den Rollback-Zähler verwenden, um eine Sicherung und Wiederherstellung zu erkennen.

   Weitere Informationen finden Sie unter [Verarbeitung von Adobe Primetime-DRM-Anforderungen](../../protecting-content/implementing-the-license-server/processing-drm-requests.md).

