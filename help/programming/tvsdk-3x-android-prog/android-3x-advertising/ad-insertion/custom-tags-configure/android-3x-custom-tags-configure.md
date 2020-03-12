---
description: Media-Streams können zusätzliche Metadaten in Form von Tags in der Wiedergabeliste/Manifestdatei enthalten. Diese Datei zeigt die Platzierung der Werbung an. Sie können benutzerdefinierte Tag-Namen angeben und benachrichtigt werden, wenn bestimmte Tags in der Manifestdatei angezeigt werden.
seo-description: Media-Streams können zusätzliche Metadaten in Form von Tags in der Wiedergabeliste/Manifestdatei enthalten. Diese Datei zeigt die Platzierung der Werbung an. Sie können benutzerdefinierte Tag-Namen angeben und benachrichtigt werden, wenn bestimmte Tags in der Manifestdatei angezeigt werden.
seo-title: Benutzerdefinierte Tags
title: Benutzerdefinierte Tags
uuid: 2892712f-bb01-4112-baee-6dcafd4fb923
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Übersicht {#custom-tags-overview}

Media-Streams können zusätzliche Metadaten in Form von Tags in der Wiedergabeliste/Manifestdatei enthalten. Diese Datei zeigt die Platzierung der Werbung an. Sie können benutzerdefinierte Tag-Namen angeben und benachrichtigt werden, wenn bestimmte Tags in der Manifestdatei angezeigt werden.

## HLS-Inhalts-Tags {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Diese Funktion ist für Safari auf Apple-Computern nicht verfügbar, da TVSDK anstelle von Flash oder MSE das Video-Tag verwendet, um HLS-Inhalte wiederzugeben.

TVSDK bietet vordefinierte Unterstützung für bestimmte `#EXT` Werbetags. Ihre Anwendung kann benutzerdefinierte Tags verwenden, um den Arbeitsablauf für Anzeigen zu verbessern oder Blackout-Szenarien zu unterstützen. Zur Unterstützung erweiterter Workflows können Sie mit TVSDK zusätzliche Tags im Manifest angeben und abonnieren. Sie können benachrichtigt werden, wenn diese Tags in der Manifestdatei angezeigt werden.

>[!TIP]
>
>Sie können benutzerdefinierte Tags sowohl für VOD- als auch für Live-/lineare Streams abonnieren.

>[!LIMITATION] {othertype=&quot;Limitation&quot;}
>
>Wenn HLS unter Verwendung des Video-Tags in Safari wiedergegeben wird und nicht mit Flash Fallback, ist diese Funktion in Safari nicht verfügbar.

## Verwenden benutzerdefinierter HLS-Tags {#section_AD032318AEF5418393D2B1DF36B0BABB}

Hier ein Beispiel für ein benutzerdefiniertes VOD-Asset:

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

* Eine Benachrichtigung, wenn `#EXT-X-ASSET` Tags oder andere benutzerdefinierte Tag-Namen, für die Sie ein Abonnement abgeschlossen haben, in der Datei vorhanden sind.
* Fügen Sie Anzeigen ein, wenn ein `#EXT-X-AD` Tag oder ein anderer benutzerdefinierter Tag-Name im Stream gefunden wird.

Sie können die folgenden Tags als benutzerdefinierte Tags abonnieren:

* `EXT-PROGRAM-DATE-TIME`
* `EXT-X-START`
* `EXT-X-AD`
* `EXT-X-CUE`
* `EXT-X-ENDLIST`

Sie werden während der Analyse der Manifestdateien mit einem `TimedMetadata` Ereignis benachrichtigt.

Es gibt einige Werbetags, wie `EXT-X-CUE`zum Beispiel, für die Sie bereits abonniert sind. Diese Anzeigen-Tags werden auch vom standardmäßigen Opportunitätsgenerator verwendet. Sie können festlegen, welche Anzeigen-Tags vom standardmäßigen Opportunitätsgenerator verwendet werden, indem Sie die `adTags` Eigenschaft festlegen.