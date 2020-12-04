---
description: Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.
seo-description: Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.
seo-title: Verpacken Sie inkompatible Anzeigen mit dem Adobe Creative Repackage Service neu.
title: Verpacken Sie inkompatible Anzeigen mit dem Adobe Creative Repackage Service neu.
uuid: 56a2405d-b395-4fea-820d-343590be7c19
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---


# Verpacken Sie inkompatible Anzeigen mit dem Adobe Creative Repackage Service {#repackage-incompatible-ads-using-adobe-creative-repackaging-service} neu.

Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.

Anzeigen, die von verschiedenen Drittanbietern bereitgestellt werden, z. B. von einer Agentur und einem Server, Ihrem Bestandspartner oder einem Werbenetzwerk, werden häufig in inkompatiblen Formaten wie dem progressiven Download von MP4 bereitgestellt.

Wenn TVSDK zum ersten Mal auf eine inkompatible Anzeige stößt, ignoriert der Player die Anzeige und sendet eine Anforderung an den Kreativ-Umverpackungsdienst (CRS), der Teil des Primetime-Anzeigenende ist, um die Anzeige in ein kompatibles Format zu verpacken. CRS versucht, M3U8-Darstellungen der Anzeige mit mehreren Bitraten zu generieren, und speichert diese Darstellungen im Primetime Content Versand Network (CDN). Wenn TVSDK das nächste Mal eine Anzeigenantwort erhält, die auf diese Anzeige verweist, verwendet der Player die HLS-kompatible M3U8-Version vom CDN.

Wenden Sie sich an Ihren Kundenbetreuer, um diese optionale Funktion zu aktivieren.

Weitere Informationen zu CRS finden Sie unter [Creative Packaging Service (CRS)](../../../dynamic-ad-insertion/creative-repackaging-service/crs-overview.md).

## Mehrere CDN-Unterstützung für CRS und Versand {#section_900FDDA5454143718F1EB4C9732C8E1C}

Während das Standard-Szenario für den Creative Repackage Service (CRS) darin besteht, ein Content Data Network (CDN) zu verwenden, können Sie CRS-Elemente auf mehr als einem CDN bereitstellen.

Sie können aus den folgenden Gründen mehrere CDNs verwenden:

* Eine Anforderung zum Vergrößern für große Ereignis.
* Eine Anforderung, die CDN-Quelle des CRS-Assets mit der CDN-Quelle des Hauptinhalts abzugleichen.

Sie können die Standard-URL, die vom CRS bereitgestellt wird, mithilfe der TVSDK URL Transformer-APIs transformieren.

Im Folgenden finden Sie die API-Ergänzungen in TVSDK:

* `PTURLTransformer` Ein Protokoll, das die Methoden beschreibt, die zum Transformieren der CRS- und URLs erforderlich sind, die von TVSDK angefordert werden. Anwendungen können dieses Protokoll implementieren und Implementierungen für die erforderlichen Methoden bereitstellen.

* `PTDefaultURLTransformer` Die Standard-URL-Transformer-Instanz, die in TVSDK erstellt wird und das  `PTURLTransformer` Protokoll implementiert. Anwendungen können diese Klasse überschreiben oder einen Post-URL-Konvertierungs-Handler hinzufügen. Dieser Handler ist nützlich, wenn die Anwendung Änderungen an der URL-Anforderung vornehmen möchte, nachdem die Standardtransformation angewendet wurde.

* `PTNetworkConfiguration setURLTransformer:defaultTransformer` Eine Setter-Methode, die für die  `PTNetworkConfiguration` Metadateninstanz bereitgestellt wird, um die  `PTURLTransformer` Implementierung festzulegen.

>[!IMPORTANT]
>
>Ihre App-Implementierungen müssen nach der `PTURLTransformerInputType`-Auflistung suchen und nur URLs vom Typ `PTURLTransformerInputTypeCRSCreative` für CRS transformieren.

Das folgende Codebeispiel zeigt, wie Ihre Anwendung die Standard-Hostkomponente in eine andere Zeichenfolge ändern kann (z. B. `cdn.mycrsdomain.com`):

```
// The sample code below uses Non-ARC code 
PTNetworkConfiguration *networkConfiguration = [[[PTNetworkConfiguration alloc] init] autorelease]; 
   
PTDefaultURLTransformer *defaultTransformer = [[[PTDefaultURLTransformer alloc] init] autorelease]; 
    [defaultTransformer addPostURLTransformHandler:^NSString *(NSString *url, PTURLTransformerInputType type) { 
        if (type == PTURLTransformerInputTypeCRSCreative) { 
            return [url stringByReplacingOccurrencesOfString:[NSURL URLWithString:url].host  
              withString:@"cdn.mycrsdomain.com"]; 
        } 
            return url; 
    }]; 
  
[networkConfiguration setURLTransformer:defaultTransformer]; 
   
// metadata is the PTMetadata instance set on a PTMediaPlayerItem instance. 
[metadata setMetadata:[self getNetworkConfiguration] forKey:PTNetworkConfigurationMetadataKey];
```
