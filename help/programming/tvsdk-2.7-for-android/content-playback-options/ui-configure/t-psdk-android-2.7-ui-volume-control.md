---
description: Sie können ein Benutzeroberflächensteuerelement einrichten, um die Lautstärke für das Video anzupassen.
title: Bereitstellen der Lautstärkeregelung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Bereitstellen der Lautstärkeregelung {#provide-volume-control}

Sie können ein Benutzeroberflächensteuerelement einrichten, um die Lautstärke für das Video anzupassen.

1. Stellen Sie in der Callback-Routine für das Schnittstellenelement &quot;Lautstärkeregelung&quot;sicher, dass der Player für diesen Befehl einen gültigen Status aufweist.

   >[!TIP]
   >
   >Jeder Status, mit Ausnahme von RELEASED, ist gültig.

1. Aufruf `setVolume` , um die Lautstärke festzulegen.

   Beispiel:

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   Der Wert für das Volumen entspricht dem geforderten Volumen, ausgedrückt als Anteil des Höchstvolumens, wobei `0` ist still und `1` ist das maximale Volumen.
