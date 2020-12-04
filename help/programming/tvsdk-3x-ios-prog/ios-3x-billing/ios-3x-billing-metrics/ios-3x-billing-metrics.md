---
description: Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.
seo-description: Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.
seo-title: Rechnungsverwendungsmetriken
title: Rechnungsverwendungsmetriken
uuid: e792cc72-b1ae-42ce-8b71-f9f9f1de0614
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Rechnungsmetriken {#billing-metrics}

Um Kunden, die nur für ihre Nutzung zahlen möchten, anstatt für einen festen Satz unabhängig von der tatsächlichen Nutzung zu bezahlen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel sie den Kunden in Rechnung stellen.

Jedes Mal, wenn der Player ein Stream-Beginn-Ereignis generiert, senden TVSDK-Beginn HTTP-Nachrichten regelmäßig an das Rechnungssystem der Adobe. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann für standardmäßige VOD-, Pro-VOD- (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterschiedlich sein. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, Ihr Vertrag mit der Adobe legt die tatsächlichen Werte fest.

Die Meldungen enthalten die folgenden Informationen:

* Inhaltstyp (live, linear oder VOD)
* Inhalts-URL
* Ob Anzeigen aktiviert sind
* Ob Mid-Roll-Anzeigen aktiviert sind (nur VOD)
* Ob der Stream durch DRM geschützt ist
* TVSDK-Version und -Plattform

Adobe konfiguriert diese Anordnung vorab. Wenn Sie die Anordnung jedoch ändern möchten, wenden Sie sich an Ihren Kundenbetreuer für Adobe-Aktivierung.

Um die Statistiken zu überwachen, die TVSDK an die Adobe sendet, rufen Sie die URL von Ihrem Kundenbetreuer für Adobe-Aktivierung ab und verwenden Sie ein Netzwerk-Erfassungswerkzeug, z. B. Charles, um die Daten anzuzeigen.

## Rechnungsmetriken {#configure-billing-metrics} konfigurieren

Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Kundenbetreuer für die Aktivierung der Adobe unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die PTBillingMetricsConfiguration-Klasse, um diese Parameter festzulegen, bevor Sie den Medienplayer initialisieren.

Die meisten Kunden sollten die Standardkonfiguration verwenden.

>[!IMPORTANT]
>
>Die von Ihnen festgelegte Konfiguration bleibt während der gesamten Laufzeit des Medienplayers gültig. Nachdem Sie den Medienplayer initialisiert haben, können Sie die Konfiguration nicht mehr ändern.

So konfigurieren Sie Rechnungsmetriken:

Geben Sie das folgende Codebeispiel ein.

```
PTBillingMetricsConfiguration *billingConfig = [[[PTBillingMetricsConfiguration alloc] init] autorelease]; 
billingConfig.enabled = YES; 
billingConfig.stdVODBillableDurationMinutes = 60.0; 
billingConfig.proVODBillableDurationMinutes = 30.0; 
billingConfig.liveBillableDurationMinutes = 15.0; 
                
// metadata is the PTMetadata instance set on PTMediaPlayerItem 
[metadata setMetadata:billingConfig forKey:PTBillingMetricsConfigurationMetadataKey];
```

## Rechnungsmetriken senden {#transmit-billing-metrics}

TVSDK sendet Rechnungsmetriken an die Adobe im XML-Format.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Wenn Sie ein Netzwerkerfassungstool verwenden, um die Statistiken zu überwachen, die TVSDK an die Adobe sendet, sollten Sie Einheiten wie die folgenden sehen:

```
<request> 
     <sc_xml_ver>1.0</sc_xml_ver> 
     <reportSuiteID>ptebilling</reportSuiteID> 
     <visitorID>5536C629-5EF7-4F02-8E5D-9FA136CB3CED</visitorID> 
     <pageName>com.adobe.primetime.psdksample</pageName> 
     <timestamp>2016-11-22T18:06:30+0000</timestamp> 
     <userAgent>Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13B143</userAgent> 
     <contextData> 
         <billingMetrics> 
                 <contentDuration>1799111</contentDuration> 
                 <contentURL>https%3A%2F%2Fdevimages.apple.com.edgekey.net%2Fstreaming%2Fexamples%2Fbipbop_16x9%2Fbipbop_16x9_variant.m3u8</contentURL> 
                 <contentType>vod</contentType> 
                 <midrollEnabled>true</midrollEnabled> 
                 <tvsdkVersion>1.0.211</tvsdkVersion> 
                 <platform>Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13B143</platform> 
                 <publisherID>com.adobe.primetime.psdksample</publisherID> 
                 <adsEnabled>true</adsEnabled> 
                 <type>start</type> 
         </billingMetrics> 
     </contextData> 
</request>
```

Die booleschen Eigenschaften `drmProtected`, `adsEnabled` und `midrollEnabled` werden nur angezeigt, wenn sie &quot;true&quot;sind.