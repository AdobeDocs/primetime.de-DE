---
description: Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.
seo-description: Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.
seo-title: Verpacken Sie inkompatible Anzeigen mit dem Adobe Creative Repackages Service neu.
title: Verpacken Sie inkompatible Anzeigen mit dem Adobe Creative Repackages Service neu.
uuid: eea3651f-2598-4efa-ba4d-dbd7afa7cb95
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Verpacken Sie inkompatible Anzeigen mit dem Adobe Creative Repackages Service neu. {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.

Anzeigen, die von verschiedenen Drittanbietern bereitgestellt werden, z. B. von einer Agentur und einem Server, Ihrem Bestandspartner oder einem Werbenetzwerk, werden häufig in inkompatiblen Formaten wie dem progressiven Download von MP4 bereitgestellt.

Wenn TVSDK zum ersten Mal auf eine inkompatible Anzeige stößt, ignoriert der Player die Anzeige und sendet eine Anforderung an den Kreativ-Umverpackungsdienst (CRS), der Teil des Primetime-Anzeigenende ist, um die Anzeige in ein kompatibles Format zu verpacken. CRS versucht, M3U8-Darstellungen der Anzeige mit mehreren Bitraten zu generieren, und speichert diese Darstellungen im Primetime Content Versand Network (CDN). Wenn TVSDK das nächste Mal eine Anzeigenantwort erhält, die auf diese Anzeige verweist, verwendet der Player die HLS-kompatible M3U8-Version vom CDN.

Wenden Sie sich zur Aktivierung dieser optionalen Funktion an Ihren Adobe-Kundenbetreuer.

Weitere Informationen zu CRS finden Sie unter [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf).

## Mehrere CDN-Unterstützung für CRS und Versand{#multiple-cdn-support-for-crs-ad-delivery}

Während das Standard-Szenario für den Creative Repackage Service (CRS) darin besteht, ein Content Data Network (CDN) zu verwenden, können Sie CRS-Elemente auf mehr als einem CDN bereitstellen.

Sie können aus den folgenden Gründen mehrere CDNs verwenden:

* Eine Anforderung zum Vergrößern für große Ereignis.
* Eine Anforderung, die CDN-Quelle des CRS-Assets mit der CDN-Quelle des Hauptinhalts abzugleichen.

Sie können die Standard-URL, die vom CRS bereitgestellt wird, mithilfe der TVSDK URL Transformer-APIs transformieren.

Im Folgenden finden Sie die API-Ergänzungen in TVSDK:

* `URLTransformer` Eine Schnittstelle, die die Methoden beschreibt, die zum Transformieren der CRS- und URLs erforderlich sind, die von TVSDK angefordert werden. Anwendungen können diese Schnittstelle implementieren und Implementierungen für die erforderlichen Methoden bereitstellen.

* `DefaultURLTransformer` Die Standard-URL-Transformer-Instanz, die in TVSDK erstellt wird und die die `URLTransformer` Schnittstelle implementiert. Anwendungen können diese Klasse überschreiben oder einen Post-URL-Konvertierungs-Handler hinzufügen. Dieser Handler ist nützlich, wenn die Anwendung Änderungen an der URL-Anforderung vornehmen möchte, nachdem die Standardtransformation angewendet wurde.

* `NetworkConfiguration.setURLTransformer` Eine Setter-Methode, die für die `NetworkConfiguration` Metadateninstanz bereitgestellt wird, um die `URLTransformer` Implementierung festzulegen.

>[!IMPORTANT]
>
>Ihre App-Implementierungen müssen nach der `URLTransformerInputType` Auflistung suchen und nur URLs vom Typ `URLTransformerInputType.CRSCreative` für CRS transformieren.

Das folgende Codebeispiel zeigt, wie Ihre Anwendung die Standard-Hostkomponente in eine andere Zeichenfolge ändern kann (z. B. `cdn.mycrsdomain.com`):

```java
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
DefaultURLTransformer urlTransformer = new DefaultURLTransformer(); 
urlTransformer.addPostURLTransformHandler(new DefaultURLTransformer.URLTransformHandler() { 
    @Override 
    public String call(String url, URLTransformerInputType type) { 
        if (type == URLTransformerInputType.CRSCreative) { 
            try { 
                return url.replaceAll(new java.net.URI(url).getHost(), "cdn.mycrsdomain.com"); 
            } catch (URISyntaxException e) { 
            } 
        } 
        return url; 
    } 
}); 
   
networkConfiguration.setURLTransformer(urlTransformer); 
   
// metadata is the Metadata instance set on a MediaResource instance. 
metadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(), networkConfiguration);
```
