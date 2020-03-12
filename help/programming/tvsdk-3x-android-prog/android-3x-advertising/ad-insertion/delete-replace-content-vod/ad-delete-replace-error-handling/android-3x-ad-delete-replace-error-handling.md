---
description: TVSDK behandelt Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume zusammengeführt oder neu angeordnet werden.
seo-description: TVSDK behandelt Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume zusammengeführt oder neu angeordnet werden.
seo-title: Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen
title: Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen
uuid: 615f42b7-733a-49c4-bd7a-f14ad0d23fa0
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen {#ad-deletion-and-replacement-error-handling}

TVSDK behandelt Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume zusammengeführt oder neu angeordnet werden.

TVSDK verwaltet `timeRanges` Fehler durch standardmäßige Zusammenführungs- und Neuanordnungsprozesse. Zunächst sortiert der Player kundenspezifische Zeiträume nach der *Anfangszeit* . Auf der Grundlage dieser Sortierreihenfolge führt TVSDK angrenzende Bereiche zusammen, wenn es Untergruppen und Schnittpunkte zwischen den Bereichen gibt.

TVSDK behandelt Zeitraumfehler mit folgenden Optionen:

* **TVSDK ordnet die Zeiträume nicht in der richtigen Reihenfolge** an.

* **Untergruppe** TVSDK führt die Teilmengen des Zeitraums zusammen.

* **Intersect** TVSDK führt die sich überschneidenden Zeiträume zusammen.

* **Bereich ersetzen Konflikt** TVSDK wählt die Dauer des Ersetzungsvorgangs aus der frühesten Zeit, die in der konfliktbehafteten Gruppe angezeigt `timeRange` wird.

TVSDK behandelt Signalmoduskonflikte mit Anzeigenmetadaten wie folgt:

* Wenn der Anzeigensignalisierungsmodus mit den Zeitraummetadaten in Konflikt steht, haben die Zeitraummetadaten immer Priorität.

   Wenn beispielsweise der Anzeigensignalisierungsmodus als Serverzuordnung oder als Manifestzeichen festgelegt ist und die Anzeigenmetadaten auch Zeitspannen für den Markierungsmodus aufweisen, wird das Ergebnis angezeigt, dass die Bereiche markiert sind und keine Anzeigen eingefügt werden.
* Bei REPLACE-Bereichen werden die Bereiche, wenn der Signalisierungsmodus als Serverzuordnung oder als Manifestzeichen festgelegt ist, wie in den REPLACE-Bereichen angegeben ersetzt und es wird keine Anzeige über die Serverzuordnung oder die Manifestzuordnung eingefügt.

   Weitere Informationen finden Sie in der Tabelle &quot; *Signalisierungsmodus/Metadaten-Kombinationsverhalten* &quot;in [Effekt auf das Einfügen und Löschen von Anzeigen im Anzeigensignalisierungsmodus](../../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/delete-replace-content-vod/android-3x-signaling-mode-android.md).

Beachten Sie Folgendes:

* Wenn der Server nicht gültig zurückgibt `AdBreaks`, generiert und verarbeitet TVSDK eine `NOPTimelineOperation` für den leeren AdBreak und es wird keine Anzeige wiedergegeben.

* Obwohl das Löschen/Ersetzen von C3-Werbeanzeigen nur für VOD unterstützt werden soll, werden, sofern in den Anzeigenmetadaten angegeben, auch Zeitbereiche für Live-Streams verarbeitet.
