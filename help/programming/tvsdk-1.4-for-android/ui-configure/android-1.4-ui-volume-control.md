---
description: Sie können ein Benutzeroberflächensteuerelement für die Lautstärke einrichten.
title: Bereitstellen der Lautstärkeregelung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Bereitstellen der Lautstärkeregelung{#provide-volume-control}

Sie können ein Benutzeroberflächensteuerelement für die Lautstärke einrichten.

1. Warten Sie, bis die MediaPlayer-Instanz für diesen Befehl einen gültigen Status aufweist, bei dem es sich um einen beliebigen Befehl mit Ausnahme von RELEASED oder ERROR handelt.
1. Aufruf `setVolume` auf `MediaPlayer` -Instanz, um die Lautstärke festzulegen.

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   Der Wert für das Volumen stellt das angeforderte Volumen dar, ausgedrückt als Anteil des maximalen Volumens, wobei 0 stumm und 100 das maximale Volumen ist.
