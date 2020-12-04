---
description: TVSDK behandelt Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume zusammengeführt oder neu angeordnet werden.
seo-description: TVSDK behandelt Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume zusammengeführt oder neu angeordnet werden.
seo-title: Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen
title: Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen
uuid: 9a951bc4-b372-4655-8510-3f474171415d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# Übersicht {#ad-deletion-and-replacement-error-handling-overview}

TVSDK behandelt Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume zusammengeführt oder neu angeordnet werden.

TVSDK verwaltet `timeRanges`-Fehler durch standardmäßige Zusammenführungs- und Neuanordnungsprozesse. Zunächst sortiert der Player benutzerdefinierte Zeitbereiche nach der Zeit *begin*. Auf der Grundlage dieser Sortierreihenfolge führt TVSDK angrenzende Bereiche zusammen, wenn es Untergruppen und Schnittpunkte zwischen den Bereichen gibt.

TVSDK behandelt Zeitraumfehler mit folgenden Optionen:

* **Out of** orderTVSDK ordnet die Zeiträume neu an.

* **** SubsetTVSDK führt die Teilmengen des Zeitraums zusammen.

* **** IntersectTVSDK führt die sich überschneidenden Zeiträume zusammen.

* **Ersetzungsbereiche** konfliktfreiTVSDK wählt die Ersetzungsdauer aus der frühesten in  `timeRange` der widersprüchlichen Gruppe angezeigten Gruppe aus.

TVSDK behandelt Signalmoduskonflikte mit Anzeigenmetadaten wie folgt:

* Wenn der Anzeigensignalisierungsmodus mit den Zeitraummetadaten in Konflikt steht, haben die Zeitraummetadaten immer Priorität.

   Wenn beispielsweise der Anzeigensignalisierungsmodus als Serverzuordnung oder als Manifestzeichen festgelegt ist und die Anzeigenmetadaten auch Zeitspannen für den Markierungsmodus aufweisen, wird das Ergebnis angezeigt, dass die Bereiche markiert sind und keine Anzeigen eingefügt werden.
* Bei REPLACE-Bereichen werden die Bereiche, wenn der Signalisierungsmodus als Serverzuordnung oder als Manifestzeichen festgelegt ist, wie in den REPLACE-Bereichen angegeben ersetzt und es wird keine Anzeige über die Serverzuordnung oder die Manifestzuordnung eingefügt.

   Weitere Informationen finden Sie in der Tabelle *Verhalten bei der Kombination von Signalen/Metadaten* in [Auswirkungen auf das Einfügen und Löschen von Anzeigen im Signalisierungsmodus...](../../../../tvsdk-2.7-for-android/ad-insertion/delete-replace-content-vod/c-psdk-android-2.7-signaling-mode-metadata-combos-android.md#c_psdk_signaling-mode-metadata-combos-android).

Beachten Sie Folgendes:

* Wenn der Server kein gültiges `AdBreaks` zurückgibt, generiert und verarbeitet TVSDK ein `NOPTimelineOperation` für das leere AdBreak und es wird keine Anzeige wiedergegeben.

* Obwohl das Löschen/Ersetzen von C3-Anzeigen nur für VOD unterstützt werden soll, werden, sofern in den Anzeigenmetadaten angegeben, auch Zeitbereiche für Live-Streams verarbeitet.

