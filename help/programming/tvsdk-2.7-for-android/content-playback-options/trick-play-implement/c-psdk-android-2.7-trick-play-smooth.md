---
description: Wenn Ihr System Zugriff auf hardwareunterstützte Dekodierung hat, können Sie mithilfe des iFrame-Formats reibungslosere Trickwiedergaben erzielen als mit der reinen TVSDK-Implementierung.
title: Glättere Trick Play-Vorgänge
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Glättere Trick Play-Vorgänge {#smoother-trick-play-operations}

Wenn Ihr System Zugriff auf hardwareunterstützte Dekodierung hat, können Sie mithilfe des iFrame-Formats reibungslosere Trickwiedergaben erzielen als mit der reinen TVSDK-Implementierung.

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

Die Verwendung des iFrame-Formats führt zu nicht reibungslosen Abspielvorgängen. Bei einem reibungsloseren Trick Play-Vorgang wird ein normales (nicht iFrame-) Profil, Hardware-Dekodierungsunterstützung und eine höhere Bildrate verwendet. Verschiedene hardwareunterstützte Dekodierungsgeräte verfügen über unterschiedliche Funktionen. Für die Doppelgeschwindigkeit sind 60 Frames pro Sekunde (FPS) erforderlich, für die Vierergeschwindigkeit sind 120 FPS erforderlich.

>[!IMPORTANT]
>
>Adobe empfiehlt, die Wiedergabe auf eine doppelte Geschwindigkeit für neuere Android-Geräte zu beschränken und die Funktion nicht für ältere Android-Geräte zu verwenden.

Um eine reibungslosere Trickwiedergabe zu erzielen, legen Sie `ABRControlParameters.maxPlayoutRate` auf das gewünschte Vielfache der normalen Geschwindigkeit (z. B. 2,0 für doppelte Geschwindigkeit). Wenn ein nachfolgender Aufruf an `MediaPlayer.setRate()` weist ein Argument auf, das kleiner oder gleich dem Wert ist, für den Sie `maxPlayoutRate`, verwendet TVSDK ein normales Profil, um eine reibungslosere Trickwiedergabe zu erzielen. Andernfalls wird ein iFrame-Profil für den Trickplay-Vorgang verwendet.
