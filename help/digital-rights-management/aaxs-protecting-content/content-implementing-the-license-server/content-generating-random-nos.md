---
title: Generieren von Zufallszahlen
description: Generieren von Zufallszahlen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Generieren von Zufallszahlen{#generating-random-numbers}

Hardware-Zufallszahlengeneratoren können auf Linux-Servern verwendet werden, um sicherzustellen, dass eine ausreichende Entropie generiert wird. Wenn der Computer nicht genügend Entropie generieren kann, blockieren Adobe-Access-Vorgänge, bei denen eine Zufallsquelle erforderlich ist, während auf Daten aus `/dev/random`.
