---
description: Wenn Ihr System Zugriff auf die hardwareunterstützte Dekodierung hat, können Sie mit dem iFrame-Format eine gleichmäßigere Trick-Wiedergabe als mit der reinen Software TVSDK-Implementierung erzielen.
title: Glättere Trick-Play-Vorgänge
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---


# Glättere Trick Play-Vorgänge {#smoother-trick-play-operations}

Wenn Ihr System Zugriff auf die hardwareunterstützte Dekodierung hat, können Sie mit dem iFrame-Format eine gleichmäßigere Trick-Wiedergabe als mit der reinen Software TVSDK-Implementierung erzielen.

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

Die Verwendung des iFrame-Formats führt zu nicht glatten Trick-Wiedergabevorgängen. Bei einer schlankeren Trick-Wiedergabe wird ein normales (nicht iFrame) Profil, eine Hardware-Dekodierung und eine höhere Bildrate verwendet. Verschiedene hardwareunterstützte Dekodierungsgeräte haben unterschiedliche Funktionen. Die Geschwindigkeit der Dublette beträgt 60 Frames pro Sekunde (FPS) und die Vierteldrehzahl 120 FPS.

>[!IMPORTANT]
>
>Adobe empfiehlt, die Wiedergabe auf Dublette für neuere Android-Geräte zu beschränken und nicht die Funktion für ältere Android-Geräte zu verwenden.

Um eine gleichmäßigere Trick-Wiedergabe zu erzielen, setzen Sie `ABRControlParameters.maxPlayoutRate` auf das gewünschte Vielfache der Normalgeschwindigkeit (z. B. 2,0 für die Dublette). Wenn ein nachfolgender Aufruf von `MediaPlayer.setRate()` ein Argument hat, das kleiner oder gleich dem für `maxPlayoutRate` festgelegten Wert ist, verwendet TVSDK ein normales Profil, um eine reibungslosere Trick-Wiedergabe zu erzielen. Andernfalls wird ein iFrame-Profil für den Trickplay-Vorgang verwendet.