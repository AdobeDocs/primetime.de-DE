---
description: In diesem Abschnitt wird eine Beispielkonfiguration vorgestellt, die die Konzepte und die Form der Konfiguration veranschaulicht.
title: Beispiel-RBOP-Konfiguration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Beispiel-RBOP-Konfiguration {#sample-rbop-configuration}

In diesem Abschnitt wird eine Beispielkonfiguration vorgestellt, die die Konzepte und die Form der Konfiguration veranschaulicht.

Die folgende JSON-Beispielkonfiguration definiert eine Pixelausgaberichtlinie, die Folgendes angibt:

* Beschränken Sie die Entschlüsselung des Videos auf Auflösungen von 1080 oder darunter
* Legen Sie spezifische Einschränkungen für die Auflösungen 720 und 480 fest:

   * Für 720 Auflösung: HDCP für digitale Ausgabe erforderlich; erforderlich *Kopiergenerierungssystem - Analog* (CGMS-A) Schutz für analoge Ausgabe.
   * Für eine Auflösung von 480: HDCP für digitale Ausgabe erforderlich; kein Schutz für analoge

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

* Die `pixelCount` -Spezifikationen sind in der JSON-Struktur innerhalb der `pixelConstraints` Abschnitt.

* In jeder Spezifikation für die Pixelanzahl ist der Ausgabeschutz für digitale und analoge Ausgabe angegeben.
* In den digitalen Ausgabespezifikationen werden HDCP-Versionen angegeben, obwohl der Client derzeit keine HDCP-Versionierung unterstützt. Weitere Informationen finden Sie in den häufig gestellten Fragen .
