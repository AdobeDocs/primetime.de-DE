---
title: Anzeigenmessung von Moat
description: Anzeigenmessung von Moat
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Anzeigenmessung von Moat {#ad-measurement-from-moat}

TVSDK übernimmt Informationen von FreeWheel und anderen Adservern, die VAST-Antworten bereitstellen. FreeWheel bietet innerhalb von VAST-Antworten Informationen vom Moat-Dienst an. Der Moat-Dienst zählt und beeindruckt mit einer Genauigkeit, die besser zeigt, dass Kreative die Interessen einer Zielgruppe erfassen oder vernachlässigen.

Moat ist ein Dienst, der die Messung und Anzeige von Inhalten über viele Anwendungen hinweg misst, von Browsern bis hin zu Anwendungen. Moat generiert Marketing-Analysedaten in Echtzeit über mehrere Plattformen hinweg.

Die VAST-Antwort-XML verfügt über eine Eigenschaft und ein Element, das Ihr Code lesen kann, die äußerste Anzeige-ID-Eigenschaft und das äußere Erweiterungselement. In beiden Fällen kann Ihr Code TVSDK verwenden, um sowohl die Anzeigen-ID-Informationen als auch die Erweiterungsinformationen zu speichern und die Informationen in einer Baumstruktur zu organisieren. Mit dieser Organisation kann Ihr Code die Daten von einer beliebigen Ebene abrufen und an einen beliebigen Ort weitergeben. Der Wert der Eigenschaft &quot;äußerste Anzeigen-ID&quot;ermöglicht es Ihrem Code, Informationen aus der zugehörigen Kampagne zu koordinieren.

Beispielsweise kann FreeWheel Daten in einem Erweiterungselement zurückgeben. Nachfolgend finden Sie ein Beispielelement.

```
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

Freewheel kann auch die ID-Eigenschaft im Anzeigenelement festlegen, wie im Beispiel unten dargestellt.

```
<Ad id="118566" sequence="1">
```

Weitere Informationen finden Sie in der API-Dokumentation für die Klasse AdobePSDK.NetworkAdInfo .
