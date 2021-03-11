---
description: Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.
title: Volumensteuerung bereitstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# Volumensteuerung{#provide-volume-control}

Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.

1. Warten Sie, bis sich die MediaPlayer-Instanz in einem gültigen Status für diesen Befehl befindet (mit Ausnahme von RELEASED oder ERROR).
1. Rufen Sie `setVolume` auf der `MediaPlayer`-Instanz auf, um die Lautstärke festzulegen.

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   Der Wert für das Volumen entspricht dem beantragten Volumen, ausgedrückt als Anteil des Höchstvolumens, wobei 0 stumm und 100 das Höchstvolumen ist.

