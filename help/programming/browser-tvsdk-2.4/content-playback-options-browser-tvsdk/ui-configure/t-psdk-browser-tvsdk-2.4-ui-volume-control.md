---
description: Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.
title: Volumensteuerung bereitstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---


# Volumensteuerung{#provide-volume-control}

Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.

1. Warten Sie, bis sich die `MediaPlayer`-Instanz in einem gültigen Status für diesen Befehl befindet.

   Jeder Status außer RELEASED oder FEHLER ist gültig.
1. Legen Sie das Volumenattribut auf der `MediaPlayer`-Instanz fest, um die Lautstärke festzulegen.

   ```js
   player.volume = ...
   ```

   Der Wert für das Volumen entspricht dem beantragten Volumen, ausgedrückt als Anteil des maximalen Volumens, wobei 0 stumm ist und das maximale Volumen ist.

