---
seo-title: Dauer der Lizenzzwischenspeicherung
title: Dauer der Lizenzzwischenspeicherung
uuid: 378940a2-f072-478d-bee1-05ccba888b5c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Dauer der Lizenzzwischenspeicherung{#license-caching-duration}

Gibt an, wie lange eine Lizenz im lokalen Lizenzspeicher des Clients zwischengespeichert werden kann, ohne dass eine erneute Akquise vom Lizenzserver erforderlich ist. Sie können auch ein absolutes Datum/eine Uhrzeit angeben, nach dem eine Lizenz nicht mehr zwischengespeichert werden kann.

Nach Ablauf des Cache-Ablaufdatums ist die Lizenz nicht mehr gültig und der Client muss eine neue Lizenz vom Lizenzserver anfordern.

Verwendungsbeispiel: Verwenden Sie die Lizenzzwischenspeicherungsdauer, um eine feste Zeitdauer für eine bestimmte Lizenz anzugeben, z. B. im Fall einer Vermietung. Eine 30-tägige Vermietung kann angegeben werden (mit Lizenz-Caching), um die gesamte Lizenzdauer anzugeben, innerhalb derer die Inhalte genutzt werden sollen.
