---
description: Sie können ein Benutzeroberflächensteuerelement für die Lautstärke einrichten.
title: Bereitstellen der Lautstärkeregelung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Bereitstellen der Lautstärkeregelung{#provide-volume-control}

Sie können ein Benutzeroberflächensteuerelement für die Lautstärke einrichten.

1. Warten Sie auf die `MediaPlayer` -Instanz einen gültigen Status für diesen Befehl aufweisen.

   Jeder Status außer RELEASED oder ERROR ist gültig.
1. Legen Sie das Volumenattribut auf der `MediaPlayer` -Instanz, um die Lautstärke festzulegen.

   ```js
   player.volume = ...
   ```

   Der Wert für das Volumen stellt das angeforderte Volumen dar, ausgedrückt als Anteil des maximalen Volumens, wobei 0 stumm ist und das maximale Volumen ist.
