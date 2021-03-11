---
title: Dauer der Lizenzzwischenspeicherung
description: Dauer der Lizenzzwischenspeicherung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Dauer der Lizenzzwischenspeicherung{#license-caching-duration}

Gibt an, wie lange eine Lizenz im lokalen Lizenzspeicher des Clients zwischengespeichert werden kann, ohne dass eine erneute Akquise vom Lizenzserver erforderlich ist. Sie können auch ein absolutes Datum/eine Uhrzeit angeben, nach dem eine Lizenz nicht mehr zwischengespeichert werden kann.

Nach Ablauf des Cache-Ablaufdatums ist die Lizenz nicht mehr gültig und der Client muss eine neue Lizenz vom Lizenzserver anfordern.

Verwendungsbeispiel: Verwenden Sie die Lizenzzwischenspeicherungsdauer, um eine feste Zeitdauer anzugeben, die für eine bestimmte Lizenz gültig ist, z. B. im Fall einer Vermietung. Eine 30-tägige Vermietung kann angegeben werden (mit Lizenz-Caching), um die gesamte Lizenzdauer anzugeben, innerhalb derer die Inhalte genutzt werden sollen.
