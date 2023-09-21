---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player gepuffert wird.
title: Pufferung von Zeitrichtlinien
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Pufferung von Zeitrichtlinien {#buffering-time-policies}

Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player gepuffert wird.

TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit, die mindestens 5 Sekunden beträgt, bevor die Medienwiedergabe beginnt. Nach den App-Aufrufen `play` aber vor Beginn der Wiedergabe puffert TVSDK die Medien bis zur Anfangsphase, um einen reibungslosen Start bei der tatsächlichen Wiedergabe zu gewährleisten.

Sie können die Pufferzeiten ändern, indem Sie neue Pufferrichtlinien definieren.

<!--<a id="section_F6EEE15600814A70A57CCBACE20D68BD"></a>-->

Abhängig von Ihrer Umgebung (einschließlich Gerät, Betriebssystem oder Netzwerkbedingungen) können Sie für Ihren Player verschiedene Pufferungsrichtlinien festlegen, z. B. die Mindestdauer für die anfängliche Pufferung und für die laufende Wiedergabe ändern.

Nach dem Aufruf `play`, beginnt der Medienplayer mit der Pufferung des Videos. Wenn der Medienplayer die durch die anfängliche Pufferzeit angegebene Videomenge gepuffert hat, beginnt die Wiedergabe. Dieser Prozess verbessert die Startzeit, da der Player nicht darauf wartet, dass der gesamte Wiedergabepuffer gefüllt wird, bevor die Wiedergabe gestartet wird. Stattdessen beginnt die Wiedergabe, nachdem die ersten Sekunden gepuffert wurden.

Während das Video gerendert wird, puffert TVSDK weiterhin neue Fragmente, bis der in der Wiedergabepufferzeit angegebene Betrag gepuffert wurde. Wenn die aktuelle Pufferlänge unter die Wiedergabepufferzeit fällt, lädt der Player zusätzliche Fragmente herunter. Sobald die aktuelle Pufferlänge um einige Sekunden über der Wiedergabepufferzeit liegt, stoppt TVSDK das Herunterladen von Fragmenten.

>[!TIP]
>
>Wenn der anfängliche Pufferwert hoch ist, kann es Ihrem Benutzer eine lange anfängliche Pufferzeit geben, bevor er startet. Dies kann eine reibungslose Wiedergabe über einen längeren Zeitraum ermöglichen. Wenn jedoch die Netzwerkbedingungen schlecht sind, kann die anfängliche Wiedergabe verzögert sein.
