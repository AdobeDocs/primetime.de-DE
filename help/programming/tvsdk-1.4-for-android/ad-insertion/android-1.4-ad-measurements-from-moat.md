---
description: TVSDK übernimmt Informationen von FreeWheel und anderen Anzeigen-Servern, die VAST-Antworten bereitstellen. FreeWheel bietet innerhalb von VAST-Antworten Informationen vom Moat-Dienst an. Der Moat-Dienst zählt und impressionen mit einer Genauigkeit, die besser zeigt, ob Kreative die Interessen einer Zielgruppe erfassen oder vernachlässigen.
title: Anzeigenmessungen von Moat
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Anzeigenmessungen von Moat{#ad-measurements-from-moat}

TVSDK übernimmt Informationen von FreeWheel und anderen Anzeigen-Servern, die VAST-Antworten bereitstellen. FreeWheel bietet innerhalb von VAST-Antworten Informationen vom Moat-Dienst an. Der Moat-Dienst zählt und impressionen mit einer Genauigkeit, die besser zeigt, ob Kreative die Interessen einer Zielgruppe erfassen oder vernachlässigen.

Moat ist ein Dienst, der die Messung und Anzeige von Inhalten über viele Anwendungen hinweg misst, von Browsern bis hin zu Anwendungen. Moat generiert Marketing-Analysedaten in Echtzeit über mehrere Plattformen hinweg.

Die VAST-Antwort-XML verfügt über eine Eigenschaft und ein Element, das Ihr Code lesen kann, die äußerste `Ad id` und der äußersten Randlage `Extension` -Element. In beiden Fällen kann Ihr Code TVSDK verwenden, um beide `Ad id` und `Extension` Informationen und ordnen Sie die Informationen dann in einer Baumstruktur an. Mit dieser Organisation kann Ihr Code die Daten von einer beliebigen Ebene abrufen und an einen beliebigen Ort weitergeben. Der Wert der äußersten Randlage `Ad id` -Eigenschaft ermöglicht es Ihrem Code, Informationen aus der zugehörigen Kampagne zu koordinieren.

Beispielsweise kann FreeWheel Daten in einem Erweiterungselement zurückgeben. Nachfolgend finden Sie ein Beispielelement.

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

Das Freewheel kann auch `id` -Eigenschaft in der `Ad` -Element, wie im Beispiel unten dargestellt.

```xml
<Ad id="118566" sequence="1">
```

Siehe API-Dokumentation für die Klasse . `NetworkAdInfo`.
