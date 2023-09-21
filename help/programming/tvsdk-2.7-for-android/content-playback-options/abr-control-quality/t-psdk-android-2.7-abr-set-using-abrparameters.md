---
description: Sie können ABR-Kontrollwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit einen neuen erstellen.
title: Adaptive Bitraten mithilfe von ABRControlParameters konfigurieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Adaptive Bitraten mithilfe von ABRControlParameters konfigurieren {#configure-adaptive-bit-rates-using-abrcontrolparameters}

Sie können ABR-Kontrollwerte nur mit ABRControlParameters festlegen, aber Sie können jederzeit einen neuen erstellen.

Die folgenden Bedingungen gelten für `ABRControlParameters`:

* Zum Zeitpunkt der Erstellung müssen Sie Werte für alle Parameter angeben.
* Nach der Erstellung können Sie die einzelnen Werte nicht mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird ein `ArgumentError` geworfen wird.

1. Bestimmen Sie Ihre anfänglichen, minimalen und maximalen Bitraten.
1. Bestimmen Sie die ABR-Richtlinie:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters` -Konstruktor erstellen und die Werte dem Medienplayer zuweisen.

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
