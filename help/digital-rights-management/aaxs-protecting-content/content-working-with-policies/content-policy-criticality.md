---
title: Politikkritik
description: Politikkritik
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Richtlinienkritik{#policy-criticality}

Wenn neue Nutzungsregeln in den Richtlinien verwendet werden und diese Richtlinien in Inhalten verwendet werden, die für ältere Lizenzserver verpackt wurden (die die neuen Nutzungsregeln nicht verstehen), können Sie angeben, wie sich ältere Lizenzserver verhalten sollen. Standardmäßig lautet die Richtlinienkritik &quot;true&quot;, d. h. der Lizenzserver muss alle Teile der Richtlinie verstehen, um eine Lizenz mit der Richtlinie zu generieren. Wenn die Richtlinienkritik auf &quot;false&quot;gesetzt ist, kann ein älterer Lizenzserver Teile der Richtlinie ignorieren, die er nicht versteht, und vom Server generierte Lizenzen enthalten nicht die neuen Nutzungsregeln.

Adobe Access-Server mit Version 2.0.2 des SDK und höher berücksichtigen die Einstellung für die Richtlinienkritik.
