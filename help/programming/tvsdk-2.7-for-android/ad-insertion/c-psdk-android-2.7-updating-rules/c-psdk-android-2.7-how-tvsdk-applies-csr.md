---
keywords: kreative Auswahlregeln;AdobeTVSDKConfig
title: Anwenden von kreativen Auswahlregeln
description: Anwenden von kreativen Auswahlregeln
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Anwenden von kreativen Auswahlregeln {#apply-creative-selection-rules}

TVSDK wendet kreative Auswahlregeln wie folgt an:

* TVSDK gilt für alle `default` Regeln zuerst, gefolgt von den zonenspezifischen Regeln.
* TVSDK ignoriert alle Regeln, die nicht für die aktuelle Zonen-ID definiert sind.
* Sobald TVSDK die Standardregeln anwendet, können die zonenspezifischen Regeln die kreativen Prioritäten basierend auf der `host` (Domäne) stimmt mit dem vom `default` Regeln.

* In der enthaltenen Beispielregeldatei mit zusätzlichen Zonenregeln, sobald TVSDK die Variable `default` Regeln, wenn die kreative Domäne M3U8 nicht enthält. [!DNL my.domain.com] oder [!DNL a.bcd.com] und die Anzeigenzone `1234`, werden die Kreativen neu angeordnet und das Flash VPAID-Kreativ zuerst abgespielt, sofern verfügbar. Andernfalls wird eine MP4-Anzeige abgespielt, usw. bis zu JavaScript.

* Wenn ein Werbekreativ ausgewählt wurde, kann TVSDK nicht nativ wiedergegeben werden ( [!DNL .mp4], [!DNL .flv]usw.), gibt TVSDK eine Neuverpackungsanfrage aus.

Beachten Sie, dass die Anzeigentypen, die von TVSDK verarbeitet werden können, weiterhin über die `validMimeTypes` Einstellung in `AuditudeSettings`.

<!-- 

In Android 2.5 API docs, I see a 
<span class="codeph"> setValidMimeTypes</span> but not a 
<span class="codeph"> getValidMimeTypes</span>.

 -->
