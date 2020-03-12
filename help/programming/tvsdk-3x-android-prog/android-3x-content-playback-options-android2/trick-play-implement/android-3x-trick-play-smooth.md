---
description: Wenn Ihr System Zugriff auf die hardwareunterstützte Dekodierung hat, können Sie mit dem iFrame-Format eine gleichmäßigere Trick-Wiedergabe als mit der reinen Software TVSDK-Implementierung erzielen.
seo-description: Wenn Ihr System Zugriff auf die hardwareunterstützte Dekodierung hat, können Sie mit dem iFrame-Format eine gleichmäßigere Trick-Wiedergabe als mit der reinen Software TVSDK-Implementierung erzielen.
seo-title: Glättere Trick-Play-Vorgänge
title: Glättere Trick-Play-Vorgänge
uuid: 959d6c67-b64f-4666-8de7-54d247459fd1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Glättere Trick-Play-Vorgänge {#smoother-trick-play-operations}

Wenn Ihr System Zugriff auf die hardwareunterstützte Dekodierung hat, können Sie mit dem iFrame-Format eine gleichmäßigere Trick-Wiedergabe als mit der reinen Software TVSDK-Implementierung erzielen.

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

Die Verwendung des iFrame-Formats führt zu nicht glatten Trick-Wiedergabevorgängen. Bei einer schlankeren Trick-Wiedergabe wird ein normales (nicht iFrame) Profil, eine Hardware-Dekodierung und eine höhere Bildrate verwendet. Verschiedene hardwareunterstützte Dekodierungsgeräte haben unterschiedliche Funktionen. Die Geschwindigkeit der Dublette beträgt 60 Frames pro Sekunde (FPS) und die Vierteldrehzahl 120 FPS.

>[!IMPORTANT]
>
>Adobe empfiehlt, dass Sie die Wiedergabe auf die Dublette für neuere Android-Geräte beschränken und nicht die Funktion für ältere Android-Geräte verwenden.

Um eine gleichmäßigere Trick-Wiedergabe zu erzielen, stellen Sie `ABRControlParameters.maxPlayoutRate` die gewünschte Vielfache der Normalgeschwindigkeit ein (z. B. 2,0 für die Dublette). Wenn ein nachfolgender Aufruf an ein Argument `MediaPlayer.setRate()` `maxPlayoutRate`hat, das kleiner oder gleich dem von Ihnen festgelegten Wert ist, verwendet TVSDK ein normales Profil, um eine reibungslosere Trick-Wiedergabe zu erzielen. Andernfalls wird ein iFrame-Profil für den Trickplay-Vorgang verwendet.