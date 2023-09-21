---
description: Medien-Streams können zusätzliche Metadaten in Form von Tags in der Wiedergabeliste/Manifestdatei enthalten. Diese Datei zeigt die Platzierung der Werbung an. Sie können benutzerdefinierte Tag-Namen angeben und benachrichtigt werden, wenn bestimmte Tags in der Manifestdatei angezeigt werden.
title: Benutzerdefinierte Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Benutzerdefinierte Tags{#custom-tags}

Medien-Streams können zusätzliche Metadaten in Form von Tags in der Wiedergabeliste/Manifestdatei enthalten. Diese Datei zeigt die Platzierung der Werbung an. Sie können benutzerdefinierte Tag-Namen angeben und benachrichtigt werden, wenn bestimmte Tags in der Manifestdatei angezeigt werden.

## HLS-Inhalts-Tags {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Diese Funktion ist für Safari auf Apple-Computern nicht verfügbar, da TVSDK zum Abspielen von HLS-Inhalten das Video-Tag anstelle von Flash oder MSE verwendet.

TVSDK bietet native Unterstützung für bestimmte #EXT-Werbe-Tags. Ihre Anwendung kann benutzerdefinierte Tags verwenden, um den Werbe-Workflow zu verbessern oder Blackout-Szenarien zu unterstützen. Zur Unterstützung erweiterter Workflows können Sie mit TVSDK zusätzliche Tags im Manifest angeben und abonnieren. Sie können benachrichtigt werden, wenn diese Tags in der Manifestdatei angezeigt werden.

>[!TIP]
>
>Sie können benutzerdefinierte Tags sowohl für VOD- als auch Live-/Linearstreams abonnieren.

>[!NOTE]
>
>Wenn HLS mit dem Video-Tag in Safari und nicht mit Flash Fallback wiedergegeben wird, ist diese Funktion in Safari nicht verfügbar.

## Verwenden benutzerdefinierter HLS-Tags {#section_AD032318AEF5418393D2B1DF36B0BABB}

Im Folgenden finden Sie ein Beispiel für ein benutzerdefiniertes VOD-Asset:

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

Ihre Anwendung kann die folgenden Szenarien einrichten:

* Eine Benachrichtigung bei `#EXT-X-ASSET` -Tags oder andere benutzerdefinierte Tag-Namen, die Sie abonniert haben, sind in der Datei vorhanden.
* Fügen Sie Anzeigen ein, wenn eine `#EXT-X-AD` -Tag oder einen anderen benutzerdefinierten Tag-Namen finden Sie im Stream.

Sie können eines der folgenden Tags als benutzerdefinierte Tags abonnieren: `EXT-PROGRAM-DATE-TIME`, `EXT-X-START`, `EXT-X-AD`, `EXT-X-CUE`, `EXT-X-ENDLIST`. Sie werden über eine `TimedMetadata` -Ereignis während des Parsens von Manifestdateien.

Es gibt einige Werbe-Tags, z. B. `EXT-X-CUE`, für die Sie bereits angemeldet sind. Diese Anzeigen-Tags werden auch vom standardmäßigen Opportunity-Generator verwendet. Sie können festlegen, welche Anzeigen-Tags vom standardmäßigen Opportunity-Generator verwendet werden, indem Sie die `adTags` -Eigenschaft.
