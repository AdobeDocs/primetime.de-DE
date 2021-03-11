---
description: Sie können ein Steuerelement der Benutzeroberfläche einrichten, um die Lautstärke für das Video anzupassen.
title: Volumensteuerung bereitstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 2%

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

