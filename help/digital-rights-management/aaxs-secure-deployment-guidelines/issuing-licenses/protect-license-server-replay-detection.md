---
title: Wiederholungsschutz
description: Wiederholungsschutz
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Wiederholungsschutz{#replay-protection}

Der Wiederholungsschutz verhindert, dass ein Angreifer eine Lizenzanforderungsnachricht wiederholt und möglicherweise einen Denial-of-Service-Angriff (DoS) gegen den Client (A *Dienstverweigerung* -Angriff ist ein Versuch von Angreifern, zu verhindern, dass legitime Benutzer eines Dienstes diesen Dienst verwenden.) Beispielsweise könnte ein Wiedergabeangriff mit dem Rollback-Zähler verwendet werden, um den Lizenzserver zu der Annahme zu &quot;verleiten&quot;, dass der DRM-Client seinen Status zurücksetzt, was zu einer Aussetzung des Kontos führt.

Weitere Informationen zum Wiederholungsschutz finden Sie unter `AbstractRequestMessage.getMessageId()` die *Adobe Access API-Referenz*.
