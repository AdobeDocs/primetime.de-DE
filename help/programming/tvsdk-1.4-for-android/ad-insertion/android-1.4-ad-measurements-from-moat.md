---
description: TVSDK nimmt Informationen von FreeWheel und anderen Werbeservern mit VAST-Antworten entgegen. FreeWheel bietet innerhalb der VAST-Antworten Informationen vom Moat-Dienst. Der Moat-Dienst zählt Anzeigenimpressionen mit einer Genauigkeit, die besser zeigt, ob Kreative die Interessen einer Audience erfassen oder vernachlässigen.
title: Anzeigenmessungen von Moat
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# Anzeigenmessungen von Moat{#ad-measurements-from-moat}

TVSDK nimmt Informationen von FreeWheel und anderen Werbeservern mit VAST-Antworten entgegen. FreeWheel bietet innerhalb der VAST-Antworten Informationen vom Moat-Dienst. Der Moat-Dienst zählt Anzeigenimpressionen mit einer Genauigkeit, die besser zeigt, ob Kreative die Interessen einer Audience erfassen oder vernachlässigen.

Moat ist ein Dienst, der die Anzeige und Anzeige über viele Verwendungen hinweg misst, von Browsern bis hin zu Anwendungen. Moat generiert Marketinganalysedaten in Echtzeit über mehrere Plattformen hinweg.

Die VAST-Antwort-XML verfügt über eine Eigenschaft und ein Element, das Ihr Code lesen kann, die äußerste `Ad id`-Eigenschaft und das äußerste `Extension`-Element. In beiden Fällen kann Ihr Code TVSDK verwenden, um sowohl die `Ad id`-Informationen als auch die `Extension`-Informationen zu speichern und die Informationen dann in einer Baumstruktur zu organisieren. Mit dieser Organisation kann Ihr Code die Daten von jeder beliebigen Ebene abrufen und an die gewünschte Stelle weiterleiten. Der Wert der äußersten `Ad id`-Eigenschaft ermöglicht es Ihrem Code, Informationen aus der zugehörigen Kampagne zu koordinieren.

Beispielsweise kann FreeWheel Daten in einem Extensions-Element zurückgeben. Nachfolgend finden Sie ein Beispielelement.

```xml
<?xml version="1.0"?> 
<Extensions> 
  <Extension type="FreeWheel"> 
    <Parameter name="moat"> 
      <MeasurementInfo renditionID="6398737" type="MediaFile"> 
        <MoatID><![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]></MoatID> 
      </MeasurementInfo> 
      <MeasurementInfo renditionID="6398739" type="MediaFile"> 
        <MoatID><![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]></MoatID> 
      </MeasurementInfo> 
    </Parameter> 
  </Extension> 
</Extensions> 
```

Die Eigenschaft `id` kann auch im Element `Ad` festgelegt werden, wie im folgenden Beispiel gezeigt.

```xml
<Ad id="118566" sequence="1">
```

Lesen Sie die API-Dokumentation für die Klasse `NetworkAdInfo`.
