---
seo-title: Wiederholungsschutz
title: Wiederholungsschutz
uuid: 5e6488e6-0834-4dcf-bc26-55019f5db320
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Wiederholungsschutz{#replay-protection}

Der Schutz vor Wiederholung verhindert, dass ein Angreifer eine Lizenzanforderungsmeldung wiedergibt und möglicherweise einen DoS-Angriff (Denial-of-Service) gegen den Client auslöst (Ein *Denial-of-Service* -Angriff ist ein Versuch eines Angreifers, den rechtmäßigen Benutzern eines Dienstes die Nutzung dieses Dienstes zu verwehren.) Beispielsweise könnte ein erneuter play-Angriff mit dem Rollback-Zähler dazu verwendet werden, den License Server zu &quot;trick&quot;zu der Annahme zu führen, dass der DRM-Client seinen Status zurückfährt, was eine Aussetzung des Kontos zur Folge hat.

Weitere Informationen zum erneuten Abspielen finden Sie in `AbstractRequestMessage.getMessageId()` der *Adobe Access API-Referenz*.
