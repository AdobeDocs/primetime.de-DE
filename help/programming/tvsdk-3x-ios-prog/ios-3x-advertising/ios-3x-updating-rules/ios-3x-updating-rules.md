---
description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.
seo-title: Aktualisieren von Regeln zur kreativen Auswahl von Werbeanzeigen
title: Aktualisieren von Regeln zur kreativen Auswahl von Werbeanzeigen
uuid: b7d316ef-323e-4769-83d9-036422ae1707
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Übersicht {#update-ad-creative-selection-rules-overview}

Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.

Wenn Ihr Videoplayer eine Anforderung an einen Werbeserver sendet, enthält die VAST/VMAP-Antwort in der Regel mehrere Werbeinhalte ( `MediaFile` Elemente), von denen jede eine URL zu einer anderen Container-Codec-Version bereitstellt. In einigen Fällen bieten Anzeigenkreative in der VAST/VMAP-Antwort jeweils eine andere Bitrate für die Anzeige. Wenn Sie Ihre eigenen Prioritäten- und Transformationsregeln für diese Werbeinhalte angeben möchten, können Sie dies in der [!DNL AdobeTVSDKConfig.json] Konfigurationsdatei tun.

>[!IMPORTANT]
>
>* Ändern Sie nicht den Namen der TVSDK-Konfigurationsdatei. Der Name muss bleiben [!DNL AdobeTVSDKConfig.json].
>* Sie können diese Datei an einer beliebigen Stelle platzieren, auf die Ihr Bundle zugreifen kann.
>



Sie können zwei Regeltypen angeben in [!DNL AdobeTVSDKConfig.json]: Regeln für *Priorität* und *Normalisieren* von Regeln.

**[!UICONTROL Disabling Pre-Roll]**

Um Pre-Roll zu deaktivieren, müssen Sie die standardmäßigen Opportunitätsgeneratoren ändern, damit der Pre-Roll-Aufruf nicht erfolgt. TVSDK verwendet standardmäßig die folgenden Opportunitätsgeneratoren:

```
/** 
 * @inheritDoc 
 */ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
    var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
    result.push(new AdSignalingModeOpportunityGenerator()); 
    result.push(new SpliceOutOpportunityGenerator()); 
    return result; 
} 
```

Um die Pre-Roll-Funktion für Live-Streams zu deaktivieren, sollte diese Änderung nur SpliceOutOpportunityGenerator umfassen:

```
/** 
 * @inheritDoc 
 */ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
    var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
    if (preroll_enabled == true) { 
        result.push(new AdSignalingModeOpportunityGenerator()); 
    } 
    result.push(new SpliceOutOpportunityGenerator()); 
    return result; 
}
```
