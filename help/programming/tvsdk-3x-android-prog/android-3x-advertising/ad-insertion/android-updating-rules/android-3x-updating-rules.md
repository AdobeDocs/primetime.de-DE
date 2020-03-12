---
description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.
seo-title: Aktualisieren von Regeln zur kreativen Auswahl von Werbeanzeigen
title: Aktualisieren von Regeln zur kreativen Auswahl von Werbeanzeigen
uuid: 77d8e186-01b5-4d62-8686-28f431d18876
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Übersicht {#update-ad-creative-selection-rules-overview}

Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.

Wenn Ihr Videoplayer eine Anforderung an einen Werbeserver sendet, enthält die VAST/VMAP-Antwort in der Regel mehrere Werbeinhalte ( `MediaFile` Elemente), von denen jede eine URL zu einer anderen Container-Codec-Version bereitstellt. In einigen Fällen bieten Anzeigenkreative in der VAST/VMAP-Antwort jeweils eine andere Bitrate für die Anzeige. Wenn Sie Ihre eigenen Prioritäten- und Transformationsregeln für diese Werbeinhalte angeben möchten, können Sie dies in der [!DNL AdobeTVSDKConfig.json] Konfigurationsdatei tun.

>[!IMPORTANT]
>
>* Ändern Sie nicht den Namen der TVSDK-Konfigurationsdatei. Der Name muss bleiben [!DNL AdobeTVSDKConfig.json].
>* Diese Datei muss im [!DNL assets/] Projektordner abgelegt werden.
>* Das Ändern der Audiospuren bei der Wiedergabe der Anzeige ändert die Audiospur nicht. Ein Player sollte Benutzern nicht erlauben, die Audiospur zu ändern, wenn eine Anzeige wiedergegeben wird.
>



Sie können zwei Regeltypen angeben in [!DNL AdobeTVSDKConfig.json]: Regeln für *Priorität* und *Normalisieren* von Regeln.

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

Die Anzeigenregeln werden mithilfe einer JSON-Datei angegeben. Das Format der JSON-Datei bleibt in beiden Versionen des TVSDK gleich. In TVSDK v3.0 muss die JSON-Datei der Anzeigenregeln jedoch an einem Speicherort gehostet werden, auf den über eine HTTP-URL zugegriffen werden kann. Die Anwendung kann eine Instanz von AuditudeSettings verwenden:

```
//TVSDK v3.0 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
