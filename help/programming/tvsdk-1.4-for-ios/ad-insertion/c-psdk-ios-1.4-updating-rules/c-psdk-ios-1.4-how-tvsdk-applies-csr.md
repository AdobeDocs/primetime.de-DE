---
keywords: kreative Auswahlregeln;AdobeTVSDKConfig
title: Kreative Auswahlregeln anwenden
description: Kreative Auswahlregeln anwenden
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Anwenden kreativer Auswahlregeln{#apply-creative-selection-rules}

TVSDK wendet kreative Auswahlregeln wie folgt an:

* TVSDK wendet zuerst alle `default`-Regeln an, gefolgt von den zonenspezifischen Regeln.
* TVSDK ignoriert alle Regeln, die nicht für die aktuelle Zonen-ID definiert sind.
* Sobald TVSDK die Standardregeln anwendet, können die zonenspezifischen Regeln die kreativen Prioritäten anhand der `host` (Domäne)-Übereinstimmungen mit den von den `default`-Regeln ausgewählten kreativen Elementen weiter ändern.

* Wenn in der enthaltenen Beispielregeldatei mit zusätzlichen Zonenregeln TVSDK die `default`-Regeln angewendet wird und die kreative Domäne M3U8 weder [!DNL my.domain.com] noch [!DNL a.bcd.com] enthält und die Anzeigenzone `1234` ist, werden die kreativen Elemente neu angeordnet und das Flash-VPAID-Kreativelement wird zuerst wiedergegeben, wenn verfügbar. Andernfalls wird eine MP4-Anzeige wiedergegeben usw. bis zu JavaScript.

* Wenn ein Werbekreativ ausgewählt ist, dass TVSDK nicht nativ wiedergegeben werden kann ( [!DNL .mp4], [!DNL .flv] usw.), stellt TVSDK eine Anforderung zum Umpacken aus.

Beachten Sie, dass die Anzeigentypen, die von TVSDK verarbeitet werden können, weiterhin über die Einstellung `validMimeTypes` in `AuditudeSettings` definiert werden.
