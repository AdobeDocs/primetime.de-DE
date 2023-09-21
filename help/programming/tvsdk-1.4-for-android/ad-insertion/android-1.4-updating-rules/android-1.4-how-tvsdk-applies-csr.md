---
description: TVSDK wendet kreative Auswahlregeln auf folgende Arten an
title: Anwenden von kreativen Auswahlregeln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Anwenden von kreativen Auswahlregeln{#applying-creative-selection-rules}

TVSDK wendet kreative Auswahlregeln wie folgt an:

* TVSDK gilt für alle `default` Regeln zuerst, gefolgt von den zonenspezifischen Regeln.
* TVSDK ignoriert alle Regeln, die nicht für die aktuelle Zonen-ID definiert sind.
* Sobald TVSDK die Standardregeln anwendet, können die zonenspezifischen Regeln die kreativen Prioritäten basierend auf der `host` (Domäne) stimmt mit dem vom `default` Regeln.

* In der enthaltenen Beispielregeldatei mit zusätzlichen Zonenregeln, sobald TVSDK die Variable `default` Regeln, wenn die kreative Domäne M3U8 nicht enthält. [!DNL my.domain.com] oder [!DNL a.bcd.com] und die Anzeigenzone `1234`, werden die Kreativen neu angeordnet und das Flash VPAID-Kreativ zuerst abgespielt, sofern verfügbar. Andernfalls wird eine MP4-Anzeige abgespielt, usw. bis zu JavaScript.

* Wenn ein Werbekreativ ausgewählt wurde, kann TVSDK nicht nativ wiedergegeben werden ( [!DNL .mp4], [!DNL .flv]usw.), gibt TVSDK eine Neuverpackungsanfrage aus.

Beachten Sie, dass die Anzeigentypen, die von TVSDK verarbeitet werden können, weiterhin über die `validMimeTypes` Einstellung in `AuditudeSettings`.
