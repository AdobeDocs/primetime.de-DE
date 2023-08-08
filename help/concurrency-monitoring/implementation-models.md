---
title: Implementierungsmodelle
description: Implementierungsmodelle
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# Implementierungsmodelle {#imp-models}

## Serverseitige Richtlinien {#ss-policies}

Dieses Modell nutzt CM als politischen Entscheidungspunkt und delegiert so die Zugriffsentscheidung an den Dienst.

Da der Client keine Annahme in Bezug auf die angewendeten Richtlinien treffen sollte, muss die Implementierung die Entscheidung über die Sitzungsinitialisierung während der Wiedergabe von der Heartbeat-Antwort sowie regelmäßig überprüfen.
