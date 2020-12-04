---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-title: Zeitrichtlinien zwischenspeichern
title: Zeitrichtlinien zwischenspeichern
uuid: 8d3ce9be-cca4-485e-ba66-d2f2aa6822dd
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Zeitrichtlinien für die Pufferung {#buffering-time-policies}

Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.

TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit von mindestens 5 Sekunden, bevor die Beginn abgespielt werden. Nachdem die Anwendung &quot;`play`&quot;aufruft, aber bevor die Wiedergabe beginnt, puffert TVSDK die Medien bis zur Anfangsphase, um einen glatten Beginn zu erhalten, wenn die Wiedergabe tatsächlich Beginn ist.

Sie können die Pufferzeiten ändern, indem Sie neue Pufferrichtlinien definieren.

<!--<a id="section_F6EEE15600814A70A57CCBACE20D68BD"></a>-->

Abhängig von Ihrer Umgebung (einschließlich des Geräts, des Betriebssystems oder der Netzwerkbedingungen) können Sie verschiedene Pufferrichtlinien für Ihren Player festlegen, z. B. die Änderung der Mindestdauer für die anfängliche Pufferung und für die kontinuierliche Wiedergabe-Pufferung.

Nach dem Aufruf von `play` beginnt der Medienplayer mit der Pufferung des Videos. Wenn der Medienplayer die durch die anfängliche Pufferzeit angegebene Videomenge gepuffert hat, beginnt die Wiedergabe. Dieser Vorgang verbessert die Beginn-Up-Zeit, da der Player nicht darauf wartet, dass der gesamte Wiedergabepuffer gefüllt wird, bevor die Wiedergabe gestartet wird. Stattdessen beginnt die Wiedergabe, nachdem die ersten Sekunden gepuffert wurden.

Während das Video wiedergegeben wird, puffert TVSDK weiterhin neue Fragmente, bis der in der Wiedergabepufferzeit angegebene Betrag gepuffert wurde. Wenn die aktuelle Pufferlänge unter die Wiedergabepufferzeit fällt, lädt der Player zusätzliche Fragmente herunter. Sobald die aktuelle Pufferlänge um einige Sekunden über der Wiedergabepufferzeit liegt, beendet TVSDK das Herunterladen von Fragmenten.

>[!TIP]
>
>Wenn der anfängliche Pufferwert hoch ist, kann dies dem Benutzer eine lange anfängliche Pufferzeit geben, bevor er beginnt. Dies kann eine reibungslose Wiedergabe über einen längeren Zeitraum ermöglichen. Bei schlechten Netzwerkbedingungen kann die anfängliche Wiedergabe jedoch verzögert sein.

