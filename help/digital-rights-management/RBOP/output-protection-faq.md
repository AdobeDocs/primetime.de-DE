---
description: Häufig gestellte Fragen zur Verwendung des auflösungsbasierten Ausgabeschutzes.
seo-description: Häufig gestellte Fragen zur Verwendung des auflösungsbasierten Ausgabeschutzes.
seo-title: Häufig gestellte Fragen
title: Häufig gestellte Fragen
uuid: 7dcd337c-369a-474c-8768-409c48b5cee5
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

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

* **Q.** *Sind RBOP-Pixelbeschränkungen diskret oder bereichsbasiert?* **A.** RBOP-Pixelbeschränkungen werden variabel dargestellt. Jeder Pixelzähler definiert die Anforderungen für alle Pixelzahlen, die kleiner oder gleich der angegebenen Anzahl sind, oder bis zur größten Anzahl, die kleiner als dieser Wert ist, wenn mehr als eine Pixelbeschränkung vorhanden ist. Einfach ausgedrückt, gelten die Werte als maximale Schwellenwerte für jede vertikale Pixelanzahl.

   Nehmen wir einmal an, dass ein MBR-Stream mit vertikalen Auflösungen von 240, 480, 600, 720 und 1080 mit den folgenden RBOP-Einstellungen an Ihren Player übergeben wird.

   **RBOP-Richtlinieneinstellungen:**

   * 720P - HDCP erforderlich
   * 480P - Kein OP
   Für jede Variante gelten die folgenden Regeln.

   **Streams:**

   * 240, 480: Beide sind &lt;= 480; kein OP erforderlich ist und die Streams mit oder ohne HDCP geladen werden.
   * 600, 720: Beide sind &lt;= 720; HDCP ist für die Wiedergabe erforderlich
   * 1080: > 720; der Stream ist auf der Blacklist (Fehler zurückgegeben), da er in den oben stehenden Regeln nicht gefunden wird.


* **Q.** Auf einigen meiner Android-Geräte werden die von mir definierten Einschränkungen für die Pixelanzahl nicht genau wie definiert angewendet. Was passiert?

   **A.** Einige Android-Geräte haben eine etwas höhere Rahmengröße als der Berichte. Passen Sie zur Behebung dieses Problems die Bildgrößen ( `maxPixel` und `pixelCount` -einstellungen) um 20 Pixel nach oben an. Passen Sie beispielsweise die Einstellungen für die Rahmengröße nach oben an:

   ```
   { 
       "maxPixel":  
   
<b>800</b>,&quot;pixelConstraints&quot;: [{ &quot;pixelCount&quot;:\
<b>532</b>, &quot;digital&quot;: [{&quot;output&quot;: &quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot;: 1, &quot;minderjährig&quot;: 0}}],&quot;analog&quot;: {&quot;output&quot;: &quot;ERFORDERLICH&quot;}},...

```
to: 
```
{&quot;maxPixel&quot;:\
<b>820</b>,&quot;pixelConstraints&quot;: [{ &quot;pixelCount&quot;:\
<b>552</b>, &quot;digital&quot;: [{&quot;output&quot;: &quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot;: 1, &quot;minderjährig&quot;: 0}}],&quot;analog&quot;: {&quot;output&quot;: &quot;ERFORDERLICH&quot;}},...

```
throughout, for all instances of `maxPixel` and `pixelCount`.

