---
description: Um Kunden aufzunehmen, die nur für das bezahlen möchten, was sie verwenden, anstatt für einen festen Satz, unabhängig von der tatsächlichen Verwendung, erfasst Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel Kunden abrechnen müssen.
title: Rechnungsverwendungsmetriken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Abrechnungsmetriken {#billing-metrics}

Um Kunden aufzunehmen, die nur für das bezahlen möchten, was sie verwenden, anstatt für einen festen Satz, unabhängig von der tatsächlichen Verwendung, erfasst Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel Kunden abrechnen müssen.

Jedes Mal, wenn der Player ein Stream-Startereignis generiert, beginnt TVSDK mit dem regelmäßigen Versand von HTTP-Nachrichten an das Adobe-Abrechnungssystem. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann sich für standardmäßige VOD, Pro VOD (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterscheiden. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, Ihr Vertrag mit Adobe bestimmt jedoch die tatsächlichen Werte.

Die Nachrichten enthalten die folgenden Informationen:

* Inhaltstyp (live, linear oder VOD)
* Inhalts-URL
* Ob Anzeigen aktiviert sind
* Ob Mid-Roll-Anzeigen aktiviert sind (nur VOD)
* Ob der Stream durch DRM geschützt wird
* TVSDK-Version und -Plattform

Adobe konfiguriert diese Anordnung vorab. Wenn Sie die Anordnung jedoch ändern möchten, wenden Sie sich an Ihren Adobe-Aktivierungsbeauftragten.

Um die Statistiken zu überwachen, die TVSDK an Adobe sendet, rufen Sie die URL von Ihrem Adobe-Aktivierungsbeauftragten ab und verwenden Sie ein Tool zur Netzwerkerfassung, z. B. Charles, um die Daten anzuzeigen.

## Rechnungsmetriken konfigurieren {#configure-billing-metrics}

Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Adobe-Aktivierungsbeauftragten verschiedene Konfigurationsparameter erhalten haben, verwenden Sie die Klasse PTBillingMetricsConfiguration , um diese Parameter einzurichten, bevor Sie den Medienplayer initialisieren.

Die meisten Kunden sollten die Standardkonfiguration verwenden.

>[!IMPORTANT]
>
>Die von Ihnen festgelegte Konfiguration bleibt für die Lebensdauer des Medienplayers in Kraft. Nachdem Sie den Medienplayer initialisiert haben, können Sie die Konfiguration nicht mehr ändern.

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

## Rechnungsmetriken übertragen {#transmit-billing-metrics}

TVSDK sendet Abrechnungsmetriken im XML-Format an Adobe.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Wenn Sie ein Tool zur Netzwerkerfassung verwenden, um die Statistiken zu überwachen, die das TVSDK an Adobe übermittelt, sollten Einheiten wie die folgenden angezeigt werden:

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

Die booleschen Eigenschaften `drmProtected`, `adsEnabled`, und `midrollEnabled` nur angezeigt werden, wenn sie wahr sind.
