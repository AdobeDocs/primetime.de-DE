---
title: Wiederholungsschutz
description: Wiederholungsschutz
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Wiederholungsschutz{#replay-protection}

Der Schutz vor Wiederholung verhindert, dass ein Angreifer eine Lizenzanforderungsmeldung wiedergibt und möglicherweise einen DoS-Angriff (Denial-of-Service, Diensteverweigerung) gegen den Client auslöst (A *Einen DoS-Angriff ist ein Versuch von Angreifern, legitime Benutzer eines Dienstes daran zu hindern, diesen Dienst zu verwenden.)* Beispielsweise könnte ein erneuter play-Angriff mit dem Rollback-Zähler dazu verwendet werden, den License Server zu &quot;trick&quot;zu der Annahme zu führen, dass der DRM-Client seinen Status zurückfährt, was eine Aussetzung des Kontos zur Folge hat.

Weitere Informationen zum Wiederholungsschutz finden Sie unter `AbstractRequestMessage.getMessageId()` der *API-Referenz für den Zugriff auf Adoben*.
