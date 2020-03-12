---
description: Browser TVSDK sendet Rechnungsmetriken in einem XML-Format an Adobe.
seo-description: Browser TVSDK sendet Rechnungsmetriken in einem XML-Format an Adobe.
seo-title: Rechnungsmetriken übertragen
title: Rechnungsmetriken übertragen
uuid: ed2638d2-7894-4840-b31a-51e48e0a3f49
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Rechnungsmetriken übertragen{#transmit-billing-metrics}

Browser TVSDK sendet Rechnungsmetriken in einem XML-Format an Adobe.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Wenn Sie zur Überwachung der Statistiken, die Browser TVSDK an Adobe sendet, ein Netzwerk-Capture-Tool verwenden, sollten Sie die folgenden Einheiten sehen:

```
<?xml version="1.0" encoding="UTF-8"?>
<request>
    <sc_xml_ver>1.0</sc_xml_ver>
    <reportSuiteID>primesample2</reportSuiteID>
    <visitorID>947310128cb56f41</visitorID>
    <pageURL>https://. . ..m3u8</pageURL>
    <timestamp>2016-4-7T10:1:4</timestamp>
    <contextData>
        <billingMetrics>
            <publisherID>com.adobe.primetime.reference.PrimetimeReference</publisherID>
            <contentType>vod</contentType>
            <adsEnabled>true</adsEnabled>
            <midrollEnabled>true</midrollEnabled>
            <platform>Mac OSX 10.11.5</platform>
            <tvsdkVersion>2,4,0,1559</tvsdkVersion>
            <contentURL>https://. . ..m3u8</contentURL>
        </billingMetrics>
    </contextData>
</request>
```

Die booleschen Eigenschaften `drmProtected`, `adsEnabled`und `midrollEnabled` werden nur angezeigt, wenn sie wahr sind.