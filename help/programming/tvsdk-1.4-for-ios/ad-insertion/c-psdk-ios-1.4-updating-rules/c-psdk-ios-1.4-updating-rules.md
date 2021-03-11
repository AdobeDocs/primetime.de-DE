---
description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.
keywords: kreative Auswahlregeln;AdobeTVSDKConfig;Ad-kreative Prioritäten;Transformationsregeln
title: Aktualisieren von Regeln zur kreativen Auswahl von Werbeanzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Übersicht {#update-ad-creative-selection-rules-overview}

Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.

Wenn Ihr Videoplayer eine Anforderung an einen Werbeserver sendet, enthält die VAST/VMAP-Antwort in der Regel mehrere Werbeinhalte ( `MediaFile`), von denen jede eine URL zu einer anderen Container-Codec-Version bereitstellt. In einigen Fällen bieten Anzeigenkreative in der VAST/VMAP-Antwort jeweils eine andere Bitrate für die Anzeige. Wenn Sie Ihre eigenen Prioritäten- und Transformationsregeln für diese Anzeigenkreative angeben möchten, können Sie dies in der Konfigurationsdatei [!DNL AdobeTVSDKConfig.json] tun.

>[!IMPORTANT]
>
>* Ändern Sie nicht den Namen der TVSDK-Konfigurationsdatei. Der Name muss [!DNL AdobeTVSDKConfig.json] bleiben.
>* Sie können diese Datei an einer beliebigen Stelle platzieren, auf die Ihr Bundle zugreifen kann.

>



Sie können zwei Regeltypen in [!DNL AdobeTVSDKConfig.json] angeben: *Priorität* und *Normalisieren*-Regeln.

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

