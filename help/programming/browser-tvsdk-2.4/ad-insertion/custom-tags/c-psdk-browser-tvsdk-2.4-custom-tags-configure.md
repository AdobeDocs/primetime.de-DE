---
description: Medienstreams können zusätzliche Metadaten in Form von Tags in der MPD-Datei (Media Presentation Description) enthalten. Diese Datei zeigt die Platzierung der Werbung an. Sie können benutzerdefinierte Tag-Namen angeben und benachrichtigt werden, wenn bestimmte Tags in der Manifestdatei angezeigt werden.
seo-description: Medienstreams können zusätzliche Metadaten in Form von Tags in der MPD-Datei (Media Presentation Description) enthalten. Diese Datei zeigt die Platzierung der Werbung an. You can specify custom tag names and be notified when certain tags appear in the manifest file.
seo-title: Benutzerdefinierte Tags
title: Custom tags
uuid: d1e34288-545b-440f-a262-2fb853f0e3c4
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---


# Übersicht {#custom-tags-overview}

Medienstreams können zusätzliche Metadaten in Form von Tags in der MPD-Datei (Media Presentation Description) enthalten. Diese Datei zeigt die Platzierung der Werbung an. Sie können benutzerdefinierte Tag-Namen angeben und benachrichtigt werden, wenn bestimmte Tags in der Manifestdatei angezeigt werden.

## HLS-Inhalts-Tags {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Diese Funktion ist für Safari auf Apple-Computern nicht verfügbar, da Browser TVSDK anstelle von Flash oder MSE das Video-Tag verwendet, um HLS-Inhalte wiederzugeben.

Browser TVSDK provides out-of-the-box support for specific #EXT advertising tags. Your application can use custom tags to enhance the advertising workflow or to support blackout scenarios. To support advanced workflows, Browser TVSDK allows you to specify and subscribe to additional tags in the manifest. You can be notified when these tags appear in the manifest file.

>[!TIP]
>
>You can subscribe to custom tags both for VOD and live/linear streams.

>[!NOTE]
>
>Wenn HLS unter Verwendung des Video-Tags in Safari wiedergegeben wird und nicht unter Verwendung von Flash-Fallback, ist diese Funktion in Safari nicht verfügbar.

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

Sie können die folgenden Tags als benutzerdefinierte Tags abonnieren: `EXT-PROGRAM-DATE-TIME`, `EXT-X-START`, `EXT-X-AD`, `EXT-X-CUE`, `EXT-X-ENDLIST`. Sie werden bei der Analyse der Manifestdateien mit einem `TimedMetadata` Ereignis benachrichtigt.

Es gibt einige Werbetags, wie `EXT-X-CUE`zum Beispiel, für die Sie bereits abonniert sind. Diese Anzeigen-Tags werden auch vom standardmäßigen Opportunitätsgenerator verwendet. Sie können festlegen, welche Anzeigen-Tags vom standardmäßigen Opportunitätsgenerator verwendet werden, indem Sie die `adTags` Eigenschaft festlegen.

## DASH-Inhalts-Tags {#section_967A952319BE4048B4C6612FFF7ADA6E}

DASH bietet zwei Möglichkeiten zur Signalgebung von Ereignissen:

* In der MPD-Datei.

   Diese Datei ähnelt der M3U8-Datei im HLS-Inhalt, und MPD-Ereignisse sind in der .mpd-Datei vorhanden.
* In der Darstellung einschließen

   Inband-Ereignis werden mit Darstellungen multipliziert, indem die Ereignis-Meldungen als Teil der Segmente hinzugefügt werden. Eine Darstellung ist eine Liste von Video- und Audiosegmenten, die nacheinander wiedergegeben werden. Die Inband-Ereignis-Daten werden in diese Segmente eingebettet.

Diese Ereignis werden als `TimedMetadata` Ereignisse an die Anwendung benachrichtigt, sobald sie von Browser TVSDK analysiert werden. Sobald ein Ereignis benachrichtigt wurde, wird es nicht erneut benachrichtigt.
