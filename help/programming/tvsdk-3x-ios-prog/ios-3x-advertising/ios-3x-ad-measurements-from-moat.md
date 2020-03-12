---
description: TVSDK nimmt Informationen von FreeWheel und anderen Adservern entgegen, die VAST-Antworten bereitstellen. FreeWheel bietet innerhalb der VAST-Antworten Informationen vom Moat-Dienst. Der Moat-Dienst zählt Anzeigenimpressionen mit einer Genauigkeit, die besser zeigt, dass Kreative die Interessen einer Audience erfassen oder vernachlässigen.
seo-description: TVSDK nimmt Informationen von FreeWheel und anderen Adservern entgegen, die VAST-Antworten bereitstellen. FreeWheel bietet innerhalb der VAST-Antworten Informationen vom Moat-Dienst. Der Moat-Dienst zählt Anzeigenimpressionen mit einer Genauigkeit, die besser zeigt, dass Kreative die Interessen einer Audience erfassen oder vernachlässigen.
seo-title: Anzeigenmessungen von Moat
title: Anzeigenmessungen von Moat
uuid: 520d33b0-2218-4f74-9689-b9dc520f29cc
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Anzeigenmessungen von Moat {#ad-measurements-from-moat}

TVSDK nimmt Informationen von FreeWheel und anderen Adservern entgegen, die VAST-Antworten bereitstellen. FreeWheel bietet innerhalb der VAST-Antworten Informationen vom Moat-Dienst. Der Moat-Dienst zählt Anzeigenimpressionen mit einer Genauigkeit, die besser zeigt, dass Kreative die Interessen einer Audience erfassen oder vernachlässigen.

Moat ist ein Dienst, der die Anzeige und Anzeige über viele Verwendungen hinweg misst, von Browsern bis hin zu Anwendungen. Moat generiert Marketinganalysedaten in Echtzeit über mehrere Plattformen hinweg.

Die VAST-Antwort-XML verfügt über eine Eigenschaft und ein Element, das Ihr Code lesen kann, die äußerste Anzeige-ID-Eigenschaft und das äußerste Erweiterungselement. So oder so kann Ihr Code TVSDK verwenden, um sowohl die Anzeigen-ID-Informationen als auch die Erweiterungen zu speichern und die Informationen in einer Baumstruktur zu organisieren. Mit dieser Organisation kann Ihr Code die Daten von jeder beliebigen Ebene abrufen und an die gewünschte Stelle weiterleiten. Der Wert der äußersten Anzeige-ID-Eigenschaft ermöglicht es Ihrem Code, Informationen aus dem zugehörigen Campaign zu koordinieren.

Beispielsweise kann FreeWheel Daten in einem Extensions-Element zurückgeben. Nachfolgend finden Sie ein Beispielelement.

```xml
<Extensions> 
   <Extension type="FreeWheel"> 
    <Parameter name="moat"> 
     <MeasurementInfo renditionID="6398737" type="MediaFile"> 
      <MoatID> 
       <![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]]]> 
       <![CDATA[> 
        </MoatID> 
      </MeasurementInfo> 
      <MeasurementInfo renditionID="6398739" type="MediaFile"> 
        <MoatID> 
        <![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]]]> 
        <![CDATA[> 
        </MoatID> 
      </MeasurementInfo> 
    </Parameter> 
  </Extension> 
</Extensions>
```

Wie im Beispiel unten dargestellt, kann FreeWheel auch die ID-Eigenschaft im Anzeigenelement festlegen.

```
<Ad id="118566" sequence="1">
```

Lesen Sie die API-Dokumentation für die Klasse `PTNetworkAdInfo` in `PTAdAsset`.