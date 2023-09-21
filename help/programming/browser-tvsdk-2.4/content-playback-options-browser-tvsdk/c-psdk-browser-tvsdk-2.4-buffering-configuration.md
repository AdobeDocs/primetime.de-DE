---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert das Browser TVSDK manchmal den Video-Stream. Sie können konfigurieren, wie der Player gepuffert wird.
title: Pufferung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Pufferung{#buffering}

Um eine reibungslosere Anzeige zu ermöglichen, puffert das Browser TVSDK manchmal den Video-Stream. Sie können konfigurieren, wie der Player gepuffert wird.

Browser TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit von mindestens 2 Sekunden, bevor die Medienwiedergabe beginnt. Nach den App-Aufrufen `play` aber vor Beginn der Wiedergabe puffert das Browser TVSDK die Medien bis zum Zeitpunkt der ersten Wiedergabe, um einen reibungslosen Start zu ermöglichen, wenn die Wiedergabe tatsächlich beginnt.

## Pufferzeiten festlegen {#section_179DA7CA865D48EBA4B03D50B6B7BC50}

Der MediaPlayer bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.

>[!TIP]
>
>Wenn Sie die Puffersteuerungsparameter nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer für den anfänglichen Puffer auf 2 Sekunden und für die laufende Wiedergabepufferzeit auf 30 Sekunden gesetzt.

* Um die Pufferparameter zu verwenden, verwenden Sie die `bufferControlParameters` -Attribut.

  So legen Sie beispielsweise den anfänglichen Puffer auf 2 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

  ```js
  var params = new AdobePSDK.BufferControlParameters(2000, 30000);
  ```

## Pufferung von Zeitrichtlinien {#section_7EF2947931654CCC8DAB9172391FA4EB}

Abhängig von Ihrer Umgebung (einschließlich Gerät, Betriebssystem oder Netzwerkbedingungen) können Sie für Ihren Player verschiedene Pufferungsrichtlinien festlegen, z. B. die Mindestdauer für die anfängliche Pufferung und für die laufende Wiedergabe ändern.

Nach dem Aufruf `play`, beginnt der Medienplayer mit der Pufferung des Videos. Wenn der Medienplayer die durch die anfängliche Pufferzeit angegebene Videomenge gepuffert hat, beginnt die Wiedergabe. Dieser Prozess verbessert die Startzeit, da der Player nicht darauf wartet, dass der gesamte Wiedergabepuffer gefüllt wird, bevor die Wiedergabe gestartet wird. Stattdessen beginnt die Wiedergabe, nachdem die ersten Sekunden gepuffert wurden.

Während das Video gerendert wird, puffert Browser TVSDK weiterhin neue Fragmente, bis der in der Wiedergabepufferzeit angegebene Betrag gepuffert wurde. Wenn die aktuelle Pufferlänge unter die Wiedergabepufferzeit fällt, lädt der Player zusätzliche Fragmente herunter. Sobald die aktuelle Pufferlänge um einige Sekunden über der Wiedergabepufferzeit liegt, beendet Browser TVSDK das Herunterladen von Fragmenten.

>[!TIP]
>
>Wenn der anfängliche Pufferwert hoch ist, kann es Ihrem Benutzer eine lange anfängliche Pufferzeit geben, bevor er startet. Dies kann eine reibungslose Wiedergabe über einen längeren Zeitraum ermöglichen. Wenn jedoch die Netzwerkbedingungen schlecht sind, kann die anfängliche Wiedergabe verzögert sein.
