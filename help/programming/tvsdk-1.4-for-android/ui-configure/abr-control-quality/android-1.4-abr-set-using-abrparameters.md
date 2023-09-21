---
description: Sie können ABR-Kontrollwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit einen neuen erstellen.
title: Adaptive Bitraten mithilfe von ABRControlParameters konfigurieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Adaptive Bitraten mithilfe von ABRControlParameters konfigurieren{#configure-adaptive-bit-rates-using-abrcontrolparameters}

Sie können ABR-Kontrollwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit einen neuen erstellen.

Die folgenden Bedingungen gelten für `ABRControlParameters`:

* Sie müssen Werte für alle Parameter zum Zeitpunkt der Erstellung angeben.
* Sie können einzelne Werte nach der Bauzeit nicht mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird ein `ArgumentError` geworfen wird.

1. Entscheiden Sie für die Start-, Mindest- und HöchstBitraten.
1. Bestimmen Sie die ABR-Richtlinie:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters` und weisen Sie sie dem Media Player zu.

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
