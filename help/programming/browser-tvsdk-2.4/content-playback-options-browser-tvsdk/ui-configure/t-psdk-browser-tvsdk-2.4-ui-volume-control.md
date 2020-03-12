---
description: Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.
seo-description: Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.
seo-title: Volumensteuerung bereitstellen
title: Volumensteuerung bereitstellen
uuid: 5f2f69cc-3969-4ca2-8ab9-5713fdf5cdb8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Volumensteuerung bereitstellen{#provide-volume-control}

Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.

1. Warten Sie, bis die `MediaPlayer` Instanz für diesen Befehl gültig ist.

   Jeder Status außer RELEASED oder FEHLER ist gültig.
1. Legen Sie das Lautstärkeattribut für die `MediaPlayer` Instanz fest, um die Lautstärke festzulegen.

   ```js
   player.volume = ...
   ```

   Der Wert für das Volumen entspricht dem beantragten Volumen, ausgedrückt als Anteil des maximalen Volumens, wobei 0 stumm ist und das maximale Volumen ist.

