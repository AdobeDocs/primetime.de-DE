---
description: Sie können ein Steuerelement der Benutzeroberfläche einrichten, um die Lautstärke für das Video anzupassen.
seo-description: Sie können ein Steuerelement der Benutzeroberfläche einrichten, um die Lautstärke für das Video anzupassen.
seo-title: Volumensteuerung bereitstellen
title: Volumensteuerung bereitstellen
uuid: f1e959e0-1817-4ccb-8adc-3eba09c91887
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---


# Volumensteuerung {#provide-volume-control}

Sie können ein Steuerelement der Benutzeroberfläche einrichten, um die Lautstärke für das Video anzupassen.

1. Vergewissern Sie sich in der Rückruffunktion für das Element der Volumensteuerungs-Schnittstelle, dass der Player für diesen Befehl einen gültigen Status hat.

   >[!TIP]
   >
   >Jeder Status, mit Ausnahme von RELEASED, ist gültig.

1. Rufen Sie `setVolume` auf, um die Lautstärke festzulegen.

   Beispiel:

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   Der Wert für das Volumen stellt das angeforderte Volumen dar, ausgedrückt als Anteil des maximalen Volumens, wobei `0` stumm und `1` das maximale Volumen ist.

