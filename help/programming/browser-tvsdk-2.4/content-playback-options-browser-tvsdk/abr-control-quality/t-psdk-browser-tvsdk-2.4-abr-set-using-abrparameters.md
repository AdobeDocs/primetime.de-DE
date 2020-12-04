---
description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
seo-description: Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.
seo-title: Adaptive Bitraten mit ABRControlParameters konfigurieren
title: Adaptive Bitraten mit ABRControlParameters konfigurieren
uuid: 99b7a463-327b-48bf-8244-e41467072b44
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Adaptive Bitraten mit ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters} konfigurieren

Sie können ABR-Steuerelementwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit eine neue erstellen.

Die folgenden Bedingungen gelten für `ABRControlParameters`:

* Sie müssen Werte für alle Parameter zur Bauzeit angeben.
* Sie können nach der Bauzeit keine individuellen Werte mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird ein `ArgumentError` ausgelöst.

1. Legen Sie die ABR-Richtlinie fest:

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters`-Konstruktor fest und weisen Sie sie dem Media Player zu.

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```

