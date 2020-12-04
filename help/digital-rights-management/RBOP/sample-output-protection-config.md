---
description: Dieser Abschnitt enthält eine Beispielkonfiguration, die die Konzepte und die Form der Konfiguration veranschaulicht.
seo-description: Dieser Abschnitt enthält eine Beispielkonfiguration, die die Konzepte und die Form der Konfiguration veranschaulicht.
seo-title: Beispiel-RBOP-Konfiguration
title: Beispiel-RBOP-Konfiguration
uuid: fa5ead93-36c5-4ad1-947b-c4f1f2632d9b
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Beispiel-RBOP-Konfiguration {#sample-rbop-configuration}

Dieser Abschnitt enthält eine Beispielkonfiguration, die die Konzepte und die Form der Konfiguration veranschaulicht.

Die folgende JSON-Beispielkonfiguration definiert eine Pixelausgaberichtlinie, die Folgendes festlegt:

* Verschlüsselung des Videos auf Auflösungen von 1080 oder weniger beschränken
* Besondere Einschränkungen für Auflösungen von 720 und 480 festlegen:

   * Für eine Auflösung von 720: HDCP für digitale Ausgabe erforderlich; erfordern den Schutz des Analog *(CGMS-A) für den analogen Ausgang.*
   * Für eine Auflösung von 480: HDCP für digitale Ausgabe erforderlich; keinen Schutz für analoge

```
{ 
  "pixelConstraints":  
    [ 
      { 
        "pixelCount": 720, 
        "digital": 
          [ 
            {"output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}} 
          ], 
        "analog": {"output": "REQUIRED_CGMSA"} 
      }, 
      { 
        "pixelCount": 480, 
        "digital":  
          [ 
            {"output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}} 
          ], 
        "analog": {"output": "NO_PROTECTION"} 
      } 
    ], 
  "maxPixel": 1080 
}
```

Beachten Sie Folgendes zur obigen Beispielkonfiguration:

* Die Spezifikationen für `pixelCount` befinden sich in der JSON-Struktur innerhalb des Abschnitts `pixelConstraints` auf einer Ebene nach unten.

* Innerhalb jeder Pixelanzahl-Spezifikation wird der Ausgabeschutz für digitale und analoge Ausgabe angegeben.
* In den Spezifikationen für die digitale Ausgabe werden HDCP-Versionen angegeben, obwohl der Client derzeit keine HDCP-Versionierung unterstützt. Weitere Informationen finden Sie in den häufig gestellten Fragen.

