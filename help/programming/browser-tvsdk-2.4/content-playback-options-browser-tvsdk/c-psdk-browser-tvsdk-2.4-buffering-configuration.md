---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert Browser TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-description: Um eine reibungslosere Anzeige zu ermöglichen, puffert Browser TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-title: Pufferung
title: Pufferung
uuid: 9937731d-013e-41e9-a4c9-f7a54a5e654d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Pufferung{#buffering}

Um eine reibungslosere Anzeige zu ermöglichen, puffert Browser TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.

Browser TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit von mindestens 2 Sekunden, bevor die Beginn abgespielt werden. Nach dem Aufruf der Anwendung, `play` aber vor dem Start der Wiedergabe puffert Browser TVSDK die Medien bis zum anfänglichen Zeitpunkt, um einen glatten Beginn zu geben, wenn es tatsächlich Beginn abspielen.

## Pufferzeiten einstellen {#section_179DA7CA865D48EBA4B03D50B6B7BC50}

Der MediaPlayer bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.

>[!TIP]
>
>Wenn Sie die Parameter für die Puffersteuerung nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer standardmäßig auf 2 Sekunden für den anfänglichen Puffer und auf 30 Sekunden für die laufende Wiedergabepufferzeit eingestellt.

* Verwenden Sie zum Verwenden der Pufferparameter das MediaPlayer- `bufferControlParameters` Attribut.

   So legen Sie beispielsweise den anfänglichen Puffer auf 2 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

   ```js
   var params = new AdobePSDK.BufferControlParameters(2000, 30000);
   ```

## Zeitrichtlinien zwischenspeichern {#section_7EF2947931654CCC8DAB9172391FA4EB}

Abhängig von Ihrer Umgebung (einschließlich des Geräts, des Betriebssystems oder der Netzwerkbedingungen) können Sie verschiedene Pufferrichtlinien für Ihren Player festlegen, z. B. die Änderung der Mindestdauer für die anfängliche Pufferung und für die kontinuierliche Wiedergabe-Pufferung.

Nach dem Aufruf `play`beginnt der Medienplayer, das Video zu puffern. Wenn der Medienplayer die durch die anfängliche Pufferzeit angegebene Videomenge gepuffert hat, beginnt die Wiedergabe. Dieser Vorgang verbessert die Beginn-Up-Zeit, da der Player nicht darauf wartet, dass der gesamte Wiedergabepuffer gefüllt wird, bevor die Wiedergabe gestartet wird. Stattdessen beginnt die Wiedergabe, nachdem die ersten Sekunden gepuffert wurden.

Während das Video wiedergegeben wird, puffert Browser TVSDK weiterhin neue Fragmente, bis der in der Wiedergabepufferzeit angegebene Betrag gepuffert wurde. Wenn die aktuelle Pufferlänge unter die Wiedergabepufferzeit fällt, lädt der Player zusätzliche Fragmente herunter. Sobald die aktuelle Pufferlänge um einige Sekunden über der Wiedergabepufferzeit liegt, beendet Browser TVSDK das Herunterladen von Fragmenten.

>[!TIP]
>
>Wenn der anfängliche Pufferwert hoch ist, kann dies dem Benutzer eine lange anfängliche Pufferzeit geben, bevor er beginnt. Dies kann eine reibungslose Wiedergabe über einen längeren Zeitraum ermöglichen. Bei schlechten Netzwerkbedingungen kann die anfängliche Wiedergabe jedoch verzögert sein.

