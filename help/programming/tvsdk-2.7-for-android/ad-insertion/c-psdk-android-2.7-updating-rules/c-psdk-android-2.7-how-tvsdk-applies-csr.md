---
description: 'null'
keywords: creative selection rules;AdobeTVSDKConfig
seo-description: 'null'
seo-title: Kreative Auswahlregeln anwenden
title: Kreative Auswahlregeln anwenden
uuid: 75109483-ea60-43a8-92e7-4bcba48986bc
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Kreative Auswahlregeln {#apply-creative-selection-rules} anwenden

TVSDK wendet kreative Auswahlregeln wie folgt an:

* TVSDK wendet zuerst alle `default`-Regeln an, gefolgt von den zonenspezifischen Regeln.
* TVSDK ignoriert alle Regeln, die nicht für die aktuelle Zonen-ID definiert sind.
* Sobald TVSDK die Standardregeln anwendet, können die zonenspezifischen Regeln die kreativen Prioritäten anhand der `host` (Domäne)-Übereinstimmungen mit den von den `default`-Regeln ausgewählten kreativen Elementen weiter ändern.

* Wenn in der enthaltenen Beispielregeldatei mit zusätzlichen Zonenregeln TVSDK die `default`-Regeln angewendet wird und die kreative Domäne M3U8 weder [!DNL my.domain.com] noch [!DNL a.bcd.com] enthält und die Anzeigenzone `1234` ist, werden die kreativen Elemente neu angeordnet und das Flash-VPAID-Kreativelement wird zuerst wiedergegeben, wenn verfügbar. Andernfalls wird eine MP4-Anzeige wiedergegeben usw. bis zu JavaScript.

* Wenn ein Werbekreativ ausgewählt ist, dass TVSDK nicht nativ wiedergegeben werden kann ( [!DNL .mp4], [!DNL .flv] usw.), stellt TVSDK eine Anforderung zum Umpacken aus.

Beachten Sie, dass die Anzeigentypen, die von TVSDK verarbeitet werden können, weiterhin über die Einstellung `validMimeTypes` in `AuditudeSettings` definiert werden.

<!-- 

In Android 2.5 API docs, I see a 
<span class="codeph"> setValidMimeTypes</span> but not a 
<span class="codeph"> getValidMimeTypes</span>.

 -->

