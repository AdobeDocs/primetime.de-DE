---
description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Anzeigenauswahl in VAST-/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Transformationsregeln für die Quell-URL-Weiterleitung von Werbeanzeigen zu definieren.
keywords: kreative Auswahlregeln; AdobeTVSDKConfig; Anzeigenkreativprioritäten; Umwandlungsregeln
title: Aktualisieren der kreativen Anzeigenauswahlregeln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Übersicht {#update-ad-creative-selection-rules-overview}

Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Anzeigenauswahl in VAST-/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Transformationsregeln für die Quell-URL-Weiterleitung von Werbeanzeigen zu definieren.

Wenn Ihr Videoplayer eine Anforderung an einen Anzeigenserver sendet, enthält die VAST-/VMAP-Antwort in der Regel mehrere Werbeinformationen ( `MediaFile` -Elemente), die jeweils eine URL zu einer anderen Container-Codec-Version bereitstellen. In einigen Fällen stellen Werbeinterstellungselemente in der VAST-/VMAP-Antwort jeweils eine andere Bitrate für die Anzeige bereit. Wenn Sie für diese Anzeigenkreativen eigene Prioritäten und Umwandlungsregeln festlegen möchten, können Sie dies im [!DNL AdobeTVSDKConfig.json] Konfigurationsdatei.

>[!IMPORTANT]
>
>* Ändern Sie nicht den Namen der TVSDK-Konfigurationsdatei. Der Name muss beibehalten werden. [!DNL AdobeTVSDKConfig.json].
>* Diese Datei muss im [!DNL assets/] Ordner Ihres Projekts.
>* Das Ändern von Audiospuren bei der Anzeigenwiedergabe ändert den Audio-Track nicht. Ein Player sollte Benutzern nicht erlauben, den Audio-Track zu ändern, wenn eine Anzeige wiedergegeben wird.
>

Sie können zwei Regeltypen in [!DNL AdobeTVSDKConfig.json]: *Priorität* Regeln und *Normalisieren* Regeln.

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

Die Anzeigenregeln werden mithilfe einer JSON-Datei angegeben. Das Format der JSON-Datei bleibt in beiden Versionen des TVSDK unverändert. In TVSDK v3.0 muss die JSON-Datei mit den Anzeigenregeln jedoch an einem Speicherort gehostet werden, auf den über eine HTTP-URL zugegriffen werden kann. Die Anwendung kann eine Instanz von AuditudeSettings verwenden:

```
//TVSDK v3.0 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
