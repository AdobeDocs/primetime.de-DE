---
description: Einige Drittanbieter-Anzeigen (oder Kreative) können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingebunden werden, da ihr Videoformat mit HLS inkompatibel ist. Primetime-Anzeigeneinfügung und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.
title: Komprimieren inkompatibler Anzeigen mit dem Adobe Creative Repackaging Service neu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Komprimieren inkompatibler Anzeigen mit dem Adobe Creative Repackaging Service neu {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Einige Drittanbieter-Anzeigen (oder Kreative) können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingebunden werden, da ihr Videoformat mit HLS inkompatibel ist. Primetime-Anzeigeneinfügung und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.

Anzeigen, die von verschiedenen Drittanbietern bereitgestellt werden, z. B. von einer Agentur und einem Server, Ihrem Inventarpartner oder einem Werbenetzwerk, werden häufig in inkompatiblen Formaten wie progressiv herunterladbarem MP4 bereitgestellt.

Wenn TVSDK erstmals auf eine inkompatible Anzeige trifft, ignoriert der Player die Anzeige und sendet eine Anfrage an den CRS (Creative Repackaging Service), der Teil des Primetime-Anzeigeneinfüge-Backend ist, um die Anzeige in ein kompatibles Format zu verpacken. CRS versucht, M3U8-Ausgabeformate mit mehreren Bit zu generieren und speichert diese Ausgabeformate im Primetime Content Delivery Network (CDN). Wenn TVSDK das nächste Mal eine Anzeigenantwort erhält, die auf diese Anzeige verweist, verwendet der Player die HLS-kompatible M3U8-Version aus dem CDN.

Wenden Sie sich zur Aktivierung dieser optionalen Funktion an Ihren Adobe-Support-Mitarbeiter.

Weitere Informationen zu CRS finden Sie unter [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf).

## Mehrere CDN-Unterstützung für CRS-Anzeigenbereitstellung {#multiple-cdn-support-for-crs-ad-delivery}

Während das Standardszenario Creative Repackaging Service (CRS) darin besteht, ein Content Data Network (CDN) zu verwenden, können Sie CRS-Assets für mehr als ein CDN bereitstellen.

Sie können aus den folgenden Gründen mehrere CDNs verwenden:

* Eine Anforderung zum Skalieren für große Anzeigeereignisse.
* Eine Anforderung, die CDN-Quelle des CRS-Assets mit der CDN-Quelle des Hauptinhalts abzugleichen.

Sie können die Standard-URL, die von CRS bereitgestellt wird, mithilfe der TVSDK URL Transformer-APIs transformieren.

Hier finden Sie die API-Ergänzungen in TVSDK:

* `URLTransformer` Eine Schnittstelle, die die Methoden beschreibt, die zum Transformieren der von TVSDK angeforderten CRS-Anzeigen-URLs erforderlich sind. Anwendungen können diese Schnittstelle implementieren und Implementierungen für die erforderlichen Methoden bereitstellen.

* `DefaultURLTransformer` Die Standard-URL-Transformatorinstanz, die in TVSDK erstellt wird und die die `URLTransformer` -Schnittstelle. Anwendungen können diese Klasse überschreiben oder einen Post-URL-Transformations-Handler hinzufügen. Dieser Handler ist nützlich, wenn die Anwendung Änderungen an der URL-Anforderung vornehmen möchte, nachdem die Standardumwandlung vorgenommen wurde.

* `NetworkConfiguration.urlTransformer` Eine Setter-Methode, die für die `NetworkConfiguration` Metadateninstanz zum Festlegen der `URLTransformer` Implementierung.

>[!IMPORTANT]
>
>Ihre App-Implementierungen müssen nach der `URLTransformerInputType` Auflistung und nur Umwandlung von URLs des Typs `URLTransformerInputType.CRSCreative` für CRS.

Das folgende Codebeispiel zeigt, wie Ihre Anwendung die standardmäßige Hostkomponente in eine andere Zeichenfolge ändern kann (z. B. `cdn.mycrsdomain.com`):

```
var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   
var urlTransformer:DefaultURLTransformer = new DefaultURLTransformer(); 
urlTransformer.addPostURLTransformHandler(function (url:String, type:String) { 
    if (type == URLTransformerInputType.CRSCreative) { 
        return url.replace(URLUtil.getServerName(url), "cdn.mycrsdomain.com"); 
    } 
    return url; 
}); 
  
networkConfiguration.urlTransformer = urlTransformer; 
   
// metadata is the Metadata instance set on a MediaResource instance. 
metadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                     networkConfiguration);
```
