---
seo-title: Wiederholungsschutz
title: Wiederholungsschutz
uuid: 5e6488e6-0834-4dcf-bc26-55019f5db320
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Wiederholungsschutz{#replay-protection}

Der Schutz vor Wiederholung verhindert, dass ein Angreifer eine Lizenzanforderungsmeldung wiedergibt und möglicherweise einen DoS-Angriff (Denial-of-Service, Diensteverweigerung) gegen den Client auslöst (A *Einen DoS-Angriff ist ein Versuch von Angreifern, legitime Benutzer eines Dienstes daran zu hindern, diesen Dienst zu verwenden.)* Beispielsweise könnte ein erneuter play-Angriff mit dem Rollback-Zähler dazu verwendet werden, den License Server zu &quot;trick&quot;zu der Annahme zu führen, dass der DRM-Client seinen Status zurückfährt, was eine Aussetzung des Kontos zur Folge hat.

Weitere Informationen zum Wiederholungsschutz finden Sie unter `AbstractRequestMessage.getMessageId()` der *API-Referenz für den Zugriff auf Adoben*.
