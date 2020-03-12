---
description: 'TVSDK wendet kreative Auswahlregeln wie folgt an '
seo-description: 'TVSDK wendet kreative Auswahlregeln wie folgt an '
seo-title: Anwenden von kreativen Auswahlregeln
title: Anwenden von kreativen Auswahlregeln
uuid: 3949bc24-3060-408b-adae-947be790a8ff
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Anwenden von kreativen Auswahlregeln{#applying-creative-selection-rules}

TVSDK wendet kreative Auswahlregeln wie folgt an:

* TVSDK wendet zuerst alle `default` Regeln an, gefolgt von den zonenspezifischen Regeln.
* TVSDK ignoriert alle Regeln, die nicht für die aktuelle Zonen-ID definiert sind.
* Sobald TVSDK die Standardregeln anwendet, können die zonenspezifischen Regeln die kreativen Prioritäten anhand der `host` (Domäne) Übereinstimmungen mit den kreativen Elementen, die in den `default` Regeln ausgewählt wurden, weiter ändern.

* In der mitgelieferten Beispielregeldatei mit zusätzlichen Zonenregeln werden die kreativen Elemente neu angeordnet, wenn TVSDK die `default` Regeln anwendet, wenn die kreative Domäne M3U8 nicht enthält [!DNL my.domain.com] oder [!DNL a.bcd.com] und die Anzeigenzone `1234`ist. Andernfalls wird eine MP4-Anzeige wiedergegeben usw. bis zu JavaScript.

* Wenn ein Werbekreativ ausgewählt ist, dass TVSDK nicht nativ abspielen kann ( [!DNL .mp4], [!DNL .flv]usw.), stellt TVSDK eine Anforderung zum Neuverpacken aus.

Beachten Sie, dass die Anzeigentypen, die von TVSDK verarbeitet werden können, weiterhin durch die `validMimeTypes` Einstellung in definiert werden `AuditudeSettings`.
