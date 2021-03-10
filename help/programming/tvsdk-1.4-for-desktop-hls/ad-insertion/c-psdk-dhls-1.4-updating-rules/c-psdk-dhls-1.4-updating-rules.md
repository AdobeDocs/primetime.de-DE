---
description: Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.
title: Aktualisieren von Regeln für die kreative Auswahl von Werbeanzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Übersicht {#updating-ad-creative-selection-rules}

Sie können die TVSDK-Konfigurationsdatei (AdobeTVSDKConfig.json) verwenden, um die Prioritäten für die Auswahl von Werbeanzeigen in VAST/VMAP-Antworten zu aktualisieren. Sie können diese Konfigurationsdatei auch verwenden, um die Quell-URL-Konvertierungsregeln für Anzeigenkreative zu definieren.

Wenn Ihr Videoplayer eine Anforderung an einen Werbeserver sendet, enthält die VAST/VMAP-Antwort in der Regel mehrere Werbeinhalte ( `MediaFile`), von denen jede eine URL zu einer anderen Container-Codec-Version bereitstellt. In einigen Fällen bieten Anzeigenkreative in der VAST/VMAP-Antwort jeweils eine andere Bitrate für die Anzeige. Wenn Sie Ihre eigenen Prioritäten- und Transformationsregeln für diese Anzeigenkreative angeben möchten, können Sie dies in der Konfigurationsdatei [!DNL AdobeTVSDKConfig.json] tun.

>[!IMPORTANT]
>
>* Ändern Sie nicht den Namen der TVSDK-Konfigurationsdatei. Der Name muss [!DNL AdobeTVSDKConfig.json] bleiben.
>* Diese Datei sollte auf Ihrem Content Versand-Netzwerk (CDN) gehostet werden.

>



Sie können zwei Regeltypen in [!DNL AdobeTVSDKConfig.json] angeben: *Priorität* und *Normalisieren*-Regeln.
