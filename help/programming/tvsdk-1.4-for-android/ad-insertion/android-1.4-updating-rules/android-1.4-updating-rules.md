---
description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Anzeigenauswahl in VAST-/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Transformationsregeln für die Quell-URL-Weiterleitung von Werbeanzeigen zu definieren.
keywords: kreative Auswahlregeln; AdobeTVSDKConfig; Anzeigenkreativprioritäten; Umwandlungsregeln
title: Aktualisieren der Anzeigenauswahlregeln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Übersicht {#updating-ad-creative-selection-rules-overview}

Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Anzeigenauswahl in VAST-/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Transformationsregeln für die Quell-URL-Weiterleitung von Werbeanzeigen zu definieren.

Wenn Ihr Videoplayer eine Anforderung an einen Anzeigenserver sendet, enthält die VAST-/VMAP-Antwort in der Regel mehrere Werbeinformationen ( `MediaFile` -Elemente), die jeweils eine URL zu einer anderen Container-Codec-Version bereitstellen. In einigen Fällen stellen Werbeinterstellungselemente in der VAST-/VMAP-Antwort jeweils eine andere Bitrate für die Anzeige bereit. Wenn Sie für diese Anzeigenkreativen eigene Prioritäten und Umwandlungsregeln festlegen möchten, können Sie dies im [!DNL AdobeTVSDKConfig.json] Konfigurationsdatei.

>[!IMPORTANT]
>
>* Ändern Sie nicht den Namen der TVSDK-Konfigurationsdatei. Der Name muss beibehalten werden. [!DNL AdobeTVSDKConfig.json].
>* Diese Datei muss im [!DNL assets/] Ordner Ihres Projekts.
>

Sie können zwei Regeltypen in [!DNL AdobeTVSDKConfig.json]: *Priorität* Regeln und *Normalisieren* Regeln.

## Deaktivieren der Pre-Roll-Funktion {#disabling-preroll}

Um die Pre-roll-Funktion zu deaktivieren, müssen Sie die standardmäßigen Opportunity-Generatoren ändern, damit kein Pre-Roll-Aufruf erfolgt. TVSDK verwendet standardmäßig die folgenden Opportunity-Generatoren:

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

Um die Pre-Roll-Funktion für Live-Streams zu deaktivieren, sollte dies geändert werden, um nur den SplliceOutOpportunityGenerator aufzunehmen:

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
