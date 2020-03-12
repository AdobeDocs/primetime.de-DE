---
description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
seo-description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
seo-title: Adaptive Bitraten mit ABRControlParameters konfigurieren
title: Adaptive Bitraten mit ABRControlParameters konfigurieren
uuid: 283ccd3d-535b-43ca-8ca5-82d12df31798
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Adaptive Bitraten mit ABRControlParameters konfigurieren {#configure-adaptive-bit-rates-using-abrcontrolparameters}

Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.

Die folgenden Bedingungen gelten für `ABRControlParameters`die

* Zur Bauzeit müssen Sie Werte für alle Parameter angeben.
* Nach der Konstruktion können Sie keine individuellen Werte mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird eine `ArgumentError` ausgelöst.

1. Legen Sie die anfänglichen, minimalen und maximalen Bitraten fest.
1. Legen Sie die ABR-Richtlinie fest:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters` Konstruktor fest und weisen Sie die Werte dem Media Player zu.

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
