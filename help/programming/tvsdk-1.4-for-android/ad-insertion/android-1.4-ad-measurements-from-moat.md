---
description: TVSDK nimmt Informationen von FreeWheel und anderen Werbeservern mit VAST-Antworten entgegen. FreeWheel bietet innerhalb der VAST-Antworten Informationen vom Moat-Dienst. Der Moat-Dienst zählt Anzeigenimpressionen mit einer Genauigkeit, die besser zeigt, ob Kreative die Interessen einer Audience erfassen oder vernachlässigen.
seo-description: TVSDK nimmt Informationen von FreeWheel und anderen Werbeservern mit VAST-Antworten entgegen. FreeWheel bietet innerhalb der VAST-Antworten Informationen vom Moat-Dienst. Der Moat-Dienst zählt Anzeigenimpressionen mit einer Genauigkeit, die besser zeigt, ob Kreative die Interessen einer Audience erfassen oder vernachlässigen.
seo-title: Anzeigenmessungen von Moat
title: Anzeigenmessungen von Moat
uuid: 73ef3a14-7ad6-4e67-8ad3-eabbeb898a09
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Anzeigenmessungen von Moat{#ad-measurements-from-moat}

TVSDK nimmt Informationen von FreeWheel und anderen Werbeservern mit VAST-Antworten entgegen. FreeWheel bietet innerhalb der VAST-Antworten Informationen vom Moat-Dienst. Der Moat-Dienst zählt Anzeigenimpressionen mit einer Genauigkeit, die besser zeigt, ob Kreative die Interessen einer Audience erfassen oder vernachlässigen.

Moat ist ein Dienst, der die Anzeige und Anzeige über viele Verwendungen hinweg misst, von Browsern bis hin zu Anwendungen. Moat generiert Marketinganalysedaten in Echtzeit über mehrere Plattformen hinweg.

Die VAST-Antwort-XML verfügt über eine Eigenschaft und ein Element, das Ihr Code lesen kann, die äußerste `Ad id` Eigenschaft und das äußere `Extension` Element. In beiden Fällen kann Ihr Code TVSDK verwenden, um sowohl die `Ad id` Informationen als auch die `Extension` Informationen zu speichern, und dann die Informationen in einer Baumstruktur organisieren. Mit dieser Organisation kann Ihr Code die Daten von jeder beliebigen Ebene abrufen und an die gewünschte Stelle weiterleiten. Der Wert der äußersten `Ad id` Eigenschaft ermöglicht es Ihrem Code, Informationen aus dem zugehörigen Campaign zu koordinieren.

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

Wie im Beispiel unten dargestellt, kann auch FreeWheel die `id` Eigenschaft im `Ad` Element einstellen.

```xml
<Ad id="118566" sequence="1">
```

Lesen Sie die API-Dokumentation für die Klasse `NetworkAdInfo`.
