---
seo-title: Funktionmanager
title: Funktionmanager
uuid: 3d78544e-4819-4122-bfd3-01522a067aa9
description: Funktionsmanager bieten Ihnen die Möglichkeit, einzelne Funktionen zu steuern, ohne das gesamte TVSDK zu durchlaufen, indem Sie nach Code für eine Funktion suchen, die an mehreren Stellen verstreut werden kann.
seo-description: Funktionsmanager bieten Ihnen die Möglichkeit, einzelne Funktionen zu steuern, ohne das gesamte TVSDK zu durchlaufen, indem Sie nach Code für eine Funktion suchen, die an mehreren Stellen verstreut werden kann.
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Funktionmanager {#feature-managers}

Funktionsmanager bieten Ihnen die Möglichkeit, einzelne Funktionen zu steuern, ohne das gesamte TVSDK zu durchlaufen, indem Sie nach Code für eine Funktion suchen, die an mehreren Stellen verstreut werden kann. Funktionsmanager verkleinern den Code zu einer Klasse pro Funktion. Die Funktionenmanager warten auf Auslöser von TVSDK-Ereignissen und informieren dann die Klasse, die den Feature Manager verwendet, um das Ergebnis zu verarbeiten. Der Feature Manager stellt die erforderlichen Informationen für die Klasse bereit.

Die Funktionsmanager führen die folgenden Aufgaben durch:

* **Löst TVSDK-Funktionen aus.**
Dies sind Funktionsaufrufe, um eine TVSDK-Funktion auszulösen. Beispielsweise `PlaybackManager.play()` wird aufgerufen, wenn die Player-Anwendung die Videowiedergabe Beginn hat.

* **Listet TVSDK-Ereignis auf.**
Der Funktionenmanager muss TVSDK-Ereignis abhören, um Informationen vom TVSDK zu erhalten. Listet beispielsweise `AdsManager` TVSDK Ads-Ereignis auf, um benachrichtigt zu werden, wenn die Anzeige den Beginn unterbricht.

* **Sendet Ereignis an den Handler.**
Nachdem die Funktionenmanager die Ereignis vom TVSDK empfangen und verarbeiten, benachrichtigen sie den Kunden, das Ereignis zu bearbeiten. Wenn beispielsweise ein Beginn für Werbeunterbrechungen `AdsManager` empfangen wurde, weist es das Player-Fragment an, diese Änderung in der Benutzeroberfläche widerzuspiegeln (deaktivieren Sie die Suchleiste, zeigen Sie die Anzeigenüberlagerung an usw.).

Die Primetime-Referenzimplementierung umfasst die folgenden Funktionsmanager:

| Feature Manager | Standarddatei | Funktion |  |
|---|---|---|---|
| Videowiedergabe | PlaybackManager | HLS-Wiedergabe und -Steuerung, DVR-Wiedergabe und -Steuerung, Puffersteuerung und Verarbeitung mit mehreren Bitraten. | Erforderlich |
| DRM-Inhaltsschutz | DRMManager | Inhaltsschutz. | Erforderlich |
| Anzeigeneinfügung | AdsManager | Anzeigeneinfügung, einschließlich Adobe Primetime-Anzeigenentscheidung, direkte Werbeunterbrechung und benutzerspezifische Werbeunterbrechung. | Optional |
| Untertitel | CCManager | Untertitel und VTT-Untertitel. | Optional |
| Spätbindendes Audio | AAManager | Spätes Binden von Audio. | Optional |
| QoS | QosManager | Servicestatistik. | Optional |
| Berechtigung | EntitlementManager | Berechtigungsintegration für die Primetime-Authentifizierung. | Optional |

Die Referenz-Implementierung enthält die oben aufgeführten grundlegenden Standardklassen und die entsprechenden Klassen mit dem Suffix On. Die Standardklassen bieten das standardmäßige TVSDK-Verhalten, während die Klassen mit dem On-Suffix den gesamten Code enthalten, der zum Auslösen der TVSDK-Funktion erforderlich ist, und TVSDK-Ereignis für diese Funktion abhören.

* Bei optionalen Funktionen funktioniert der Standardcode so, als wäre die Funktion deaktiviert.
* Klassen mit dem Suffix &quot;Ein&quot;funktionieren, als ob die Funktion aktiviert ist.