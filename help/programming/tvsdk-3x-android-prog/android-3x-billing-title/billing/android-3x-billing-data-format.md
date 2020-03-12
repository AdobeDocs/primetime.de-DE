---
description: TVSDK sendet Rechnungsmetriken in einem XML-Format an Adobe.
seo-description: TVSDK sendet Rechnungsmetriken in einem XML-Format an Adobe.
seo-title: Rechnungsmetriken übertragen
title: Rechnungsmetriken übertragen
uuid: c925800c-0fb7-4781-94e8-7e7ad94bb965
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Rechnungsmetriken übertragen {#transmit-billing-metrics}

TVSDK sendet Rechnungsmetriken in einem XML-Format an Adobe.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Wenn Sie ein Netzwerk-Erfassungswerkzeug verwenden, um die Statistiken zu überwachen, die TVSDK an Adobe sendet, sollten Sie Einheiten wie die folgenden sehen:

```xml
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