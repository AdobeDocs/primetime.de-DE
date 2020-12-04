---
description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
seo-description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
seo-title: Adaptive Bitraten mit ABRControlParameters konfigurieren
title: Adaptive Bitraten mit ABRControlParameters konfigurieren
uuid: 7084e954-196b-492e-846f-f8b36bed13a9
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Adaptive Bitraten mit ABRControlParameters {#configure-adaptive-bit-rates-using-abrcontrolparameters} konfigurieren

Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.

Die folgenden Bedingungen gelten für `ABRControlParameters`:

* Zur Bauzeit müssen Sie Werte für alle Parameter angeben.
* Nach der Konstruktion können Sie keine individuellen Werte mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird ein `ArgumentError` ausgelöst.

1. Legen Sie die anfänglichen, minimalen und maximalen Bitraten fest.
1. Legen Sie die ABR-Richtlinie fest:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Legen Sie die ABR-Parameterwerte im Konstruktor `ABRControlParameters` fest und weisen Sie die Werte dem Medienplayer zu.

   ```
   public ABRControlParameters(int initialBitRate, 
     int minBitRate, 
     int maxBitRate, 
     ABRControlParameters.ABRPolicy abrPolicy, 
     int minTrickPlayBitRate, 
     int maxTrickPlayBitRate, 
     int maxTrickPlayBandwidthUsage, 
     int maxPlayoutRate);
   ```

