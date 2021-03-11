---
title: Generieren von Zufallszahlen
description: Generieren von Zufallszahlen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---


# Generieren von Zufallszahlen{#generating-random-numbers}

Hardware-Zufallszahlengeneratoren können auf Linux-Servern verwendet werden, um sicherzustellen, dass eine ausreichende Entropie erzeugt wird. Wenn der Computer nicht genügend Entropie generieren kann, blockieren Adobe Access-Vorgänge, bei denen eine zufällige Quelle erforderlich ist, während auf Daten von `/dev/random` gewartet wird.
