---
description: Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.
seo-description: Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.
seo-title: Volumensteuerung bereitstellen
title: Volumensteuerung bereitstellen
uuid: 63e96424-54d0-4c16-bd94-2366722f752a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Volumensteuerung bereitstellen{#provide-volume-control}

Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.

1. Warten Sie, bis sich die MediaPlayer-Instanz in einem gültigen Status für diesen Befehl befindet (mit Ausnahme von RELEASED oder ERROR).
1. Rufen Sie `setVolume` die `MediaPlayer` Instanz auf, um die Lautstärke festzulegen.

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   Der Wert für das Volumen entspricht dem beantragten Volumen, ausgedrückt als Anteil des Höchstvolumens, wobei 0 stumm und 100 das Höchstvolumen ist.

