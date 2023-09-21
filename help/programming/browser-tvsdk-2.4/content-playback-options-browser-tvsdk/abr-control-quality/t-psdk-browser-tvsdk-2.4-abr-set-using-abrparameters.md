---
description: Sie können ABR-Kontrollwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit einen neuen erstellen.
title: Adaptive Bitraten mithilfe von ABRControlParameters konfigurieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Adaptive Bitraten mithilfe von ABRControlParameters konfigurieren{#configure-adaptive-bit-rates-using-abrcontrolparameters}

Sie können ABR-Kontrollwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit einen neuen erstellen.

Die folgenden Bedingungen gelten für `ABRControlParameters`:

* Sie müssen Werte für alle Parameter zum Zeitpunkt der Erstellung angeben.
* Sie können einzelne Werte nach der Bauzeit nicht mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird ein `ArgumentError` geworfen wird.

1. Bestimmen Sie die ABR-Richtlinie:

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters` und weisen Sie sie dem Media Player zu.

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```
