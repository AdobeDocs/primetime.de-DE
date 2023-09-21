---
title: Politikkritik
description: Politikkritik
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Politikkritik{#policy-criticality}

Wenn in den Richtlinien neue Nutzungsregeln verwendet werden und diese Richtlinien in Inhalten verwendet werden, die für ältere Lizenzserver verpackt sind (die die neuen Nutzungsregeln nicht verstehen), können Sie angeben, wie sich ältere Lizenzserver verhalten sollen. Standardmäßig ist die Richtlinienkritik &quot;true&quot;, d. h. der Lizenzserver muss alle Teile der Richtlinie verstehen, um eine Lizenz mithilfe der Richtlinie zu generieren. Wenn die Richtlinienkritik auf &quot;false&quot;gesetzt ist, kann ein älterer Lizenzserver Teile der Richtlinie ignorieren, die er nicht versteht, und vom Server generierte Lizenzen enthalten keine neuen Nutzungsregeln.

Adobe Access-Server, die Version 2.0.2 des SDK und höher verwenden, berücksichtigen die Einstellung für Richtlinienkritik.
