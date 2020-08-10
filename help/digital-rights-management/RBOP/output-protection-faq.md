---
description: Häufig gestellte Fragen zur Verwendung des auflösungsbasierten Ausgabeschutzes.
seo-description: Häufig gestellte Fragen zur Verwendung des auflösungsbasierten Ausgabeschutzes.
seo-title: Häufig gestellte Fragen
title: Häufig gestellte Fragen
uuid: 7dcd337c-369a-474c-8768-409c48b5cee5
translation-type: tm+mt
source-git-commit: fa9e89dd63c8b4c9d6eee78258957cfd30c29088
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# Häufig gestellte Fragen {#rbop-faq}

Häufig gestellte Fragen zur Verwendung des auflösungsbasierten Ausgabeschutzes.

* **Q.** *Beim Definieren einer digitalen Ausgabeanforderung für eine Pixelbeschränkung erhalte ich Fehler bei der Analyse/Formatierung, wenn ich die HDCP-Version auslasse, aber ich habe keine HDCP-Anforderungen. Wie konfiguriere ich in diesem Fall meine digitale Ausgabenanforderung?* **A.** Da die Überprüfung der HDCP-Version im Client derzeit nicht unterstützt wird, empfiehlt Adobe, die HDCP-Version auf `1.0`festzulegen. Dadurch wird sichergestellt, dass Ihre Konfiguration korrekt formatiert ist und in Zukunft semantisch konsistent ist, wenn die HDCP-Versionsüberprüfung unterstützt wird. Das folgende Codefragment zeigt eine Konfiguration mit diesem HDCP-Wert.

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

* **Q.** *Sind RBOP-Pixelbeschränkungen diskret oder bereichsbasiert?* **A.** RBOP-Pixelbeschränkungen werden variabel dargestellt. Each pixel count defines the requirements for all pixel counts less than or equal to the given count or up to the largest count smaller than that value if more than one pixel constraint exists. Simply put, the values apply as maximum thresholds for each vertical pixel count.

   Nehmen wir einmal an, dass ein MBR-Stream mit vertikalen Auflösungen von 240, 480, 600, 720 und 1080 mit den folgenden RBOP-Einstellungen an Ihren Player übergeben wird.

   **RBOP-Richtlinieneinstellungen:**

   * 720P - HDCP erforderlich
   * 480P - Kein OP

   Für jede Variante gelten die folgenden Regeln.

   **Streams:**

   * 240, 480: Beide sind &lt;= 480; kein OP erforderlich ist und die Streams mit oder ohne HDCP geladen werden.
   * 600, 720: Both are &lt;= 720; HDCP is required for playback
   * 1080: > 720; der Stream wird blockiert (Fehler zurückgegeben), da er in den oben stehenden Regeln nicht gefunden wird.


* **Q.** Auf einigen meiner Android-Geräte werden die von mir definierten Einschränkungen für die Pixelanzahl nicht genau wie definiert angewendet. What is happening?

   **A.** Some Android devices are reporting frame sizes slightly higher than the normal size. To remedy this situation, adjust your frame sizes ( `maxPixel` and `pixelCount` settings) upward by 20 pixels. Passen Sie beispielsweise die Einstellungen für die Rahmengröße nach oben an:

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

   bis:

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

