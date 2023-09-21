---
description: TVSDK behandelt Zeitbereichsfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume zusammengeführt oder neu angeordnet werden.
title: Umgang mit Anzeigenlöschungen und Ersatzfehlern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Umgang mit Anzeigenlöschungen und Ersatzfehlern  {#ad-deletion-and-replacement-error-handling}

TVSDK behandelt Zeitbereichsfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume zusammengeführt oder neu angeordnet werden.

TVSDK verwaltet `timeRanges` Fehler durch standardmäßige Zusammenführungs- und Neuanordnungsprozesse. Zunächst sortiert der Player kundendefinierte Zeiträume nach dem *begin* Zeit. Basierend auf dieser Sortierreihenfolge führt TVSDK benachbarte Bereiche zusammen und fügt diese Bereiche zusammen, wenn es Untergruppen und Schnittmengen gibt.

TVSDK behandelt Zeitbereichsfehler mit den folgenden Optionen:

* **Nicht in Reihenfolge** TVSDK ordnet die Zeiträume neu an.

* **Untergruppe** TVSDK führt die Zeitbereich-Teilmengen zusammen.

* **Schnittmenge** TVSDK führt die sich überschneidenden Zeiträume zusammen.

* **Bereichskonflikt ersetzen** TVSDK wählt die Ersetzungsdauer von der ersten `timeRange` in der in Konflikt stehenden Gruppe angezeigt.

TVSDK behandelt Signalmoduskonflikte mit Anzeigenmetadaten wie folgt:

* Wenn der Anzeigenanzeigemodus mit den Zeitbereichs-Metadaten in Konflikt steht, haben die Zeitbereichsmetadaten immer Priorität.

  Wenn beispielsweise der Anzeigenanzeigemodus als Server-Mapping- oder Manifestangaben festgelegt ist und die Anzeigenmetadaten auch MÄRKTE-Zeitspannen aufweisen, wird das resultierende Verhalten dadurch verursacht, dass die Bereiche markiert sind und keine Anzeigen eingefügt werden.
* Wenn der Signalmodus für Ersetzungsbereiche als Serverzuordnung oder Manifestzeichen festgelegt ist, werden die Bereiche wie in den ERSETZUNGSBEREICHEN angegeben ersetzt und es wird keine Anzeige über Serverzuordnungen oder Manifestanzeigen eingefügt.

  Weitere Informationen finden Sie unter *Verhalten der Signalmethode/Metadatenkombination* Tabelle in [Auswirkung auf das Einfügen und Löschen von Anzeigen im Anzeigesignalmodus](../../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/delete-replace-content-vod/android-3x-signaling-mode-android.md).

Beachten Sie Folgendes:

* Wenn der Server keine Gültigkeit zurückgibt `AdBreaks`, generiert und verarbeitet TVSDK eine `NOPTimelineOperation` für die leere AdBreak verwenden und keine Anzeige wiedergegeben wird.

* Obwohl das Löschen/Ersetzen von C3-Anzeigen nur für VOD unterstützt werden soll, werden, sofern in den Anzeigenmetadaten angegeben, auch Zeitbereiche für Live-Streams verarbeitet.
