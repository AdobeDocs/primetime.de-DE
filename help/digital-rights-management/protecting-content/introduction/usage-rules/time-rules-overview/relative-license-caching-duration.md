---
title: Dauer der Lizenzzwischenspeicherung
description: Dauer der Lizenzzwischenspeicherung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Dauer der Lizenzzwischenspeicherung{#license-caching-duration}

Die Dauer der Lizenzzwischenspeicherung gibt an, wie lange eine Lizenz im lokalen Lizenzspeicher des Clients zwischengespeichert werden kann, ohne dass eine erneute Akquise vom Lizenzserver erforderlich ist. Alternativ können Sie ein absolutes Datum und eine Uhrzeit angeben, nach denen eine Lizenz nicht mehr zwischengespeichert werden kann.

Nach Ablauf des Cache-Ablaufdatums ist die Lizenz nicht mehr gültig und der Client muss eine neue Lizenz vom Lizenzserver anfordern.

Verwendungsbeispiel: Verwenden Sie die Lizenzzwischenspeicherungsdauer, um eine feste Zeitdauer anzugeben, die für eine bestimmte Lizenz gültig ist, z. B. im Fall einer Vermietung. Sie können eine 30-Tage-Vermietung (mit Lizenz-Caching) angeben, um die gesamte Lizenzdauer anzugeben, innerhalb derer der Inhalt genutzt werden soll.
