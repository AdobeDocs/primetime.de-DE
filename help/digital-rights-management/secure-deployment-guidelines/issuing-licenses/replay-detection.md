---
description: Der Schutz vor Wiederholung verhindert, dass ein Angreifer eine Lizenzanforderungsmeldung wiedergibt und möglicherweise einen DoS-Angriff (Denial-of-Service) gegen den Client auslöst.
title: Wiederholungsschutz
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Wiederholungsschutz{#replay-protection}

Der Schutz vor Wiederholung verhindert, dass ein Angreifer eine Lizenzanforderungsmeldung wiedergibt und möglicherweise einen DoS-Angriff (Denial-of-Service) gegen den Client auslöst.

Ein DoS-Angriff ist ein Versuch von Angreifern, legitime Benutzer eines Dienstes daran zu hindern, diesen Dienst zu verwenden. Beispielsweise könnte ein Wiederholungsangriff, der den Rollback-Zähler verwendet, dazu verwendet werden, den License Server in die Annahme zu &quot;tricksen&quot;, dass der DRM-Client seinen Status zurückgenommen hat, was eine Aussetzung des Kontos verursacht.

Weitere Informationen zum Wiedergabeschutz finden Sie unter [ AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).
