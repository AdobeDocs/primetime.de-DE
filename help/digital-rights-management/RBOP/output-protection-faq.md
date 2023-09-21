---
description: Häufig gestellte Fragen zur Verwendung des auflösungsbasierten Ausgabeschutzes.
title: Häufig gestellte Fragen zu RBOP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Häufig gestellte Fragen zu RBOP {#rbop-faq}

Häufig gestellte Fragen zur Verwendung des auflösungsbasierten Ausgabeschutzes.

* **F.** *Beim Definieren einer digitalen Ausgabeanforderung für eine Pixelbegrenzung erhalte ich Parsing-/Formatierungsfehler, wenn ich die HDCP-Version auslasse, aber ich habe keine HDCP-Anforderungen. Wie konfiguriere ich in diesem Fall meine digitale Ausgabeanforderung?* **A.** Da die HDCP-Versionskontrolle derzeit nicht vom Client unterstützt wird, empfiehlt Adobe, die HDCP-Version auf `1.0`. Dadurch wird sichergestellt, dass Ihre Konfiguration korrekt formatiert ist und in Zukunft semantisch konsistent ist, wenn die HDCP-Versionskontrolle unterstützt wird. Das folgende Snippet zeigt eine Konfiguration mit diesem HDCP-Wert.

  ```
  { "pixelConstraints":  
    [  
      { "pixelCount": 720, "digital":  
        [  
          {  
            "output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}  
          }  
        ]  
      }  
    ]  
  }
  ```

* **F.** *Sind RBOP-Pixelbeschränkungen diskret oder bereichsbasiert?* **A.** RBOP-Pixelbegrenzungen sind bereichsbasiert. Jede Pixelanzahl definiert die Anforderungen für alle Pixelzahlen, die kleiner oder gleich der angegebenen Anzahl sind, oder bis zur größten Anzahl, die kleiner ist als dieser Wert, wenn mehr als eine Pixelbegrenzung vorhanden ist. Einfach ausgedrückt, gelten die Werte als maximale Schwellenwerte für jede vertikale Pixelanzahl.

  Nehmen wir einmal an, dass ein MBR-Stream mit vertikalen Auflösungen von 240, 480, 600, 720 und 1080 mit den folgenden RBOP-Einstellungen an Ihren Player übergeben wird.

  **RBOP-Richtlinieneinstellungen:**

   * 720P - HDCP erforderlich
   * 480P - Kein OP

  Die folgenden Regeln werden auf jede Variante angewendet.

  **Streams:**

   * 240, 480: Beide sind &lt;= 480; es ist kein OP erforderlich und die Ströme werden mit oder ohne vorhandenes HDCP beladen.
   * 600, 720: Beide sind &lt;= 720; HDCP ist für die Wiedergabe erforderlich
   * 1080: > 720; der Stream wird blockiert (Fehler wird zurückgegeben), da er in den oben stehenden Regeln nicht gefunden wird.

* **F.** Auf einigen meiner Android-Geräte werden die von mir definierten Beschränkungen der Pixelanzahl nicht genau wie definiert angewendet. Was passiert?

  **A.** Einige Android-Geräte melden Frame-Größen, die etwas höher sind als die normale Größe. Passen Sie die Bildgrößen ( `maxPixel` und `pixelCount` -Einstellungen) um 20 Pixel nach oben. Passen Sie beispielsweise Ihre Einstellungen für die Bildgröße nach oben an:

  ```
  { 
      "maxPixel": 800, 
      "pixelConstraints": [ 
          { "pixelCount": 532, 
            "digital": [{"output": "REQUIRED", "hdcp":{"major": 1,"minor": 0}}], 
            "analog": {"output": "REQUIRED"} 
          }, 
  ... 
  ```

  an:

  ```
  { 
      "maxPixel": 820, 
      "pixelConstraints": [ 
          { "pixelCount": 552, 
            "digital": [{"output": "REQUIRED", "hdcp":{"major": 1,"minor": 0}}], 
            "analog": {"output": "REQUIRED"} 
          }, 
  ... 
  ```

  für alle Instanzen von `maxPixel` und `pixelCount`.
