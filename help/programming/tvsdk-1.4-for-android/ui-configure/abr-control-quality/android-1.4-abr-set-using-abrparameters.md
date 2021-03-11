---
description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
title: Adaptive Bitraten mit ABRControlParameters konfigurieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# Adaptive Bitraten mit ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters} konfigurieren

Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.

Die folgenden Bedingungen gelten für `ABRControlParameters`:

* Sie müssen Werte für alle Parameter zur Bauzeit angeben.
* Sie können nach der Bauzeit keine individuellen Werte mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird ein `ArgumentError` ausgelöst.

1. Entscheiden Sie sich für die anfänglichen, minimalen und maximalen Bitraten.
1. Legen Sie die ABR-Richtlinie fest:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters`-Konstruktor fest und weisen Sie sie dem Media Player zu.

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

