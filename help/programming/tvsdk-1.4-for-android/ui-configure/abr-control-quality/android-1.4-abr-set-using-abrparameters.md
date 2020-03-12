---
description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
seo-description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
seo-title: Adaptive Bitraten mit ABRControlParameters konfigurieren
title: Adaptive Bitraten mit ABRControlParameters konfigurieren
uuid: c877c5cc-ad72-46dc-afc4-d41ee097a9a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Adaptive Bitraten mit ABRControlParameters konfigurieren{#configure-adaptive-bit-rates-using-abrcontrolparameters}

Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.

Die folgenden Bedingungen gelten für `ABRControlParameters`die

* Sie müssen Werte für alle Parameter zur Bauzeit angeben.
* Sie können nach der Bauzeit keine individuellen Werte mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird eine `ArgumentError` ausgelöst.

1. Entscheiden Sie sich für die anfänglichen, minimalen und maximalen Bitraten.
1. Legen Sie die ABR-Richtlinie fest:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters` Konstruktor fest und weisen Sie sie dem Media Player zu.

   ```java
   public ABRControlParameters(int initialBitRate, 
     int minBitRate, 
     int maxBitRate, 
     ABRControlParameters.ABRPolicy abrPolicy, 
     int minTrickPlayBitRate, 
     int maxTrickPlayBitRate, 
     int maxTrickPlayBandwidthUsage, 
     int maxPlayoutRate);
   ```

