---
title: Funktionmanager
description: Funktionsmanager bieten Ihnen die Möglichkeit, einzelne Funktionen zu steuern, ohne das gesamte TVSDK zu durchlaufen, indem Sie nach Code für eine Funktion suchen, die an mehreren Stellen verstreut werden kann.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---


# Funktionsmanager {#feature-managers}

Funktionsmanager bieten Ihnen die Möglichkeit, einzelne Funktionen zu steuern, ohne das gesamte TVSDK zu durchlaufen, indem Sie nach Code für eine Funktion suchen, die an mehreren Stellen verstreut werden kann. Funktionsmanager verkleinern den Code zu einer Klasse pro Funktion. Die Funktionenmanager warten auf Trigger von TVSDK-Ereignissen und informieren dann die Klasse, die den Feature Manager verwendet, um das Ergebnis zu verarbeiten. Der Feature Manager stellt die erforderlichen Informationen für die Klasse bereit.

Die Funktionsmanager führen die folgenden Aufgaben durch:

* **Trigger TVSDK-Funktionen.**
Dies sind Funktionsaufrufe zum Trigger einer TVSDK-Funktion. Beispiel: 
`PlaybackManager.play()` wird aufgerufen, wenn die Player-Anwendung die Videowiedergabe Beginn hat.

* **Listet TVSDK-Ereignis auf.**
Der Funktionenmanager muss TVSDK-Ereignis abhören, um Informationen vom TVSDK zu erhalten. Beispiel: 
`AdsManager` überwacht die TVSDK Ads-Ereignis, die benachrichtigt werden, wenn die Anzeige den Beginn unterbricht.

* **Sendet Ereignis an den Handler.**
Nachdem die Funktionenmanager die Ereignis vom TVSDK empfangen und verarbeiten, benachrichtigen sie den Kunden, das Ereignis zu bearbeiten. Beispiel: 
`AdsManager` ein Beginn für Werbeunterbrechungen erhält, weist es das Player-Fragment an, diese Änderung in der Benutzeroberfläche widerzuspiegeln (Deaktivieren der Scrubbing-Leiste, Anzeigen der Anzeigenüberlagerung usw.).

Die Primetime-Referenzimplementierung umfasst die folgenden Funktionsmanager:

| Feature Manager | Standarddatei | Funktion |  |
|---|---|---|---|
| Videowiedergabe | PlaybackManager | HLS-Wiedergabe und -Steuerung, DVR-Wiedergabe und -Steuerung, Puffersteuerung und Verarbeitung mit mehreren Bitraten. | Erforderlich |
| DRM-Inhaltsschutz | DRMManager | Inhaltsschutz. | Erforderlich |
| Anzeigeneinfügung | AdsManager | Anzeigeneinfügung, einschließlich Adobe Primetime-Anzeigenentscheidung für direkte Werbeunterbrechung und benutzerspezifische Werbeunterbrechung. | Optional |
| Untertitel | CCManager | Untertitel und VTT-Untertitel. | optional |
| Spätbindendes Audio | AAManager | Spätes Binden von Audio. | optional |
| QoS | QosManager | Servicestatistik. | optional |
| Berechtigung | EntitlementManager | Berechtigungsintegration für die Primetime-Authentifizierung. | optional |

Die Referenz-Implementierung enthält die oben aufgeführten grundlegenden Standardklassen und die entsprechenden Klassen mit dem Suffix On. Die Standardklassen bieten das standardmäßige TVSDK-Verhalten, während die Klassen mit dem On-Suffix den gesamten Code enthalten, der zum Trigger der TVSDK-Funktion und zum Abhören der TVSDK-Ereignis für diese Funktion erforderlich ist.

* Bei optionalen Funktionen funktioniert der Standardcode so, als wäre die Funktion deaktiviert.
* Klassen mit dem Suffix &quot;Ein&quot;funktionieren, als ob die Funktion aktiviert ist.