---
title: Funktionsmanager
description: Mit Feature Manager können Sie einzelne Funktionen steuern, ohne das gesamte TVSDK zu durchlaufen, indem Sie nach Code für eine Funktion suchen, die an mehreren Stellen verteilt sein könnte.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Funktionsmanager {#feature-managers}

Mit Feature Manager können Sie einzelne Funktionen steuern, ohne das gesamte TVSDK zu durchlaufen, indem Sie nach Code für eine Funktion suchen, die an mehreren Stellen verteilt sein könnte. Feature Manager verdichten Code zu einer Klasse pro Funktion. Die Funktionsmanager warten auf Trigger von TVSDK-Ereignissen und informieren dann die Klasse, die den Feature Manager zur Verarbeitung des Ergebnisses verwendet. Der Feature Manager stellt die erforderlichen Informationen für die Klasse bereit.

Die Funktionmanager führen die folgenden Aufgaben aus:

* **Trigger TVSDK-Funktionen.**
Dies sind Funktionsaufrufe zum Trigger einer TVSDK-Funktion. Beispiel: `PlaybackManager.play()` wird aufgerufen, wenn die Player-Anwendung die Videowiedergabe starten muss.

* **Überwacht TVSDK-Ereignisse.**
Der Feature Manager muss TVSDK-Ereignisse überwachen, um Informationen vom TVSDK zu erhalten. Beispiel: `AdsManager` überwacht TVSDK-Anzeigen-Ereignisse, die benachrichtigt werden, wenn Werbeunterbrechungen beginnen.

* **Sendet Ereignisse an den Handler.**
Nachdem die Feature Manager die Ereignisse vom TVSDK empfangen und verarbeiten, benachrichtigen sie die Client-Seite, um das Ereignis zu verarbeiten. Beispiel: nach `AdsManager` ein Ereignis zum Start der Werbeunterbrechung erhält, wird das Player-Fragment angewiesen, diese Änderung in der Benutzeroberfläche widerzuspiegeln (Deaktivieren der Scrubbing-Leiste, Anzeigen der Anzeigenüberlagerung usw.).

Die Primetime-Referenzimplementierung umfasst die folgenden Feature Manager:

| Funktionsmanager | Standarddatei | Funktion |  |
|---|---|---|---|
| Videowiedergabe | PlaybackManager | HLS-Wiedergabe und -Steuerung, DVR-Wiedergabe und -Steuerung, Puffersteuerung und Multi-Bitrate-Handhabung. | Erforderlich |
| DRM-Inhaltsschutz | DrmManager | Inhaltsschutz. | Erforderlich |
| Anzeigeneinfügung | AdsManager | Anzeigeneinfügung, einschließlich Adobe Primetime-Anzeigenentscheidung, direkter Werbeunterbrechung und benutzerspezifischer Werbeunterbrechung. | Optional |
| Geschlossene Untertitel | CCManager | Untertitel für verdeckte Untertitel und VTT. | Optional |
| Spätbindende Audiowiedergabe | AAManager | Spätes Binden von Audio. | Optional |
| QoS | QosManager | Servicequalitätsstatistiken. | Optional |
| Berechtigung | EntitlementManager | Berechtigungsintegration für Primetime-Authentifizierung. | Optional |

Die Referenzimplementierung enthält grundlegende Standardklassen, die oben aufgeführt sind, und entsprechende Klassen mit dem Suffix &quot;On&quot;. Die Standardklassen bieten das standardmäßige TVSDK-Verhalten, während die Klassen mit dem On-Suffix den gesamten Code enthalten, der zum Trigger der TVSDK-Funktion und zum Überwachen der TVSDK-Ereignisse für diese Funktion erforderlich ist.

* Bei optionalen Funktionen funktioniert der Standardcode so, als wäre die Funktion deaktiviert.
* Klassen mit dem Suffix &quot;Ein&quot;funktionieren so, als ob die Funktion aktiviert ist.
