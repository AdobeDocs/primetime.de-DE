---
description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Anzeigenauswahl in VAST-/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Transformationsregeln für die Quell-URL-Weiterleitung von Werbeanzeigen zu definieren.
title: Aktualisieren der Anzeigenauswahlregeln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Übersicht {#updating-ad-creative-selection-rules}

Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Anzeigenauswahl in VAST-/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Transformationsregeln für die Quell-URL-Weiterleitung von Werbeanzeigen zu definieren.

Wenn Ihr Videoplayer eine Anforderung an einen Anzeigenserver sendet, enthält die VAST-/VMAP-Antwort in der Regel mehrere Werbeinformationen ( `MediaFile` -Elemente), die jeweils eine URL zu einer anderen Container-Codec-Version bereitstellen. In einigen Fällen stellen Werbeinterstellungselemente in der VAST-/VMAP-Antwort jeweils eine andere Bitrate für die Anzeige bereit. Wenn Sie für diese Anzeigenkreativen eigene Prioritäten und Umwandlungsregeln festlegen möchten, können Sie dies im [!DNL AdobeTVSDKConfig.json] Konfigurationsdatei.

>[!IMPORTANT]
>
>* Ändern Sie nicht den Namen der TVSDK-Konfigurationsdatei. Der Name muss beibehalten werden. [!DNL AdobeTVSDKConfig.json].
>* Diese Datei sollte auf Ihrem Content Delivery Network (CDN) gehostet werden.
>

Sie können zwei Regeltypen in [!DNL AdobeTVSDKConfig.json]: *Priorität* Regeln und *Normalisieren* Regeln.
