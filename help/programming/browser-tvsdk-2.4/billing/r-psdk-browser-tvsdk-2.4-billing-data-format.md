---
description: Browser TVSDK sendet Abrechnungsmetriken im XML-Format an Adobe.
title: Rechnungsmetriken übertragen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Rechnungsmetriken übertragen{#transmit-billing-metrics}

Browser TVSDK sendet Abrechnungsmetriken im XML-Format an Adobe.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Wenn Sie ein Tool zur Netzwerkerfassung verwenden, um die Statistiken zu überwachen, die Browser TVSDK an Adobe übermittelt, sollten Einheiten wie die folgenden angezeigt werden:

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

Die booleschen Eigenschaften `drmProtected`, `adsEnabled`, und `midrollEnabled` nur angezeigt werden, wenn sie wahr sind.
