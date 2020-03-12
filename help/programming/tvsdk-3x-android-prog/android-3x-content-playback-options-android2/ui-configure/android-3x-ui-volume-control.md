---
description: Sie können ein Steuerelement der Benutzeroberfläche einrichten, um die Lautstärke für das Video anzupassen.
seo-description: Sie können ein Steuerelement der Benutzeroberfläche einrichten, um die Lautstärke für das Video anzupassen.
seo-title: Volumensteuerung bereitstellen
title: Volumensteuerung bereitstellen
uuid: c87fe656-0329-4c9c-b65b-43be48c77062
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Volumensteuerung bereitstellen {#provide-volume-control}

Sie können ein Steuerelement der Benutzeroberfläche einrichten, um die Lautstärke für das Video anzupassen.

1. Vergewissern Sie sich in der Rückruffunktion für das Element der Volumensteuerungs-Schnittstelle, dass der Player für diesen Befehl einen gültigen Status hat.

   >[!TIP]
   >
   >Jeder Status, mit Ausnahme von RELEASED, ist gültig.

1. Rufen Sie `setVolume` an, um die Lautstärke festzulegen.

   Beispiel:

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   Der Wert für das Volumen entspricht dem beantragten Volumen, ausgedrückt als Anteil des Höchstvolumens, wobei `0` es stumm ist und das Höchstvolumen `1` ist.