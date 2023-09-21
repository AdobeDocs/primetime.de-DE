---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server wiederzugeben. Die Variabilität der Internet-Verbindung oder Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität der Medien lokal wiedergegeben wird.
title: Format "AC-3 5.1"
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Format &quot;AC-3 5.1&quot;{#ac-format}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server wiederzugeben. Die Variabilität der Internet-Verbindung oder Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität der Medien lokal wiedergegeben wird.

Primetime kann nicht vor solchen Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen. Primetime-Streaming bietet jedoch einen Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Server-Fehlern oder Betriebsausfällen zu schützen, wodurch das Erlebnis für Viewer verbessert wird. TVSDK implementiert einen Failover-Schutz, um Unterbrechungen der Wiedergabe zu minimieren und trotz Übertragungsproblemen eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Medienset, wenn vollständige Ausgabedarstellungen oder Fragmente nicht verfügbar sind.

Mit dem Audio Codec 3 (AC-3, auch Dolby Digital®) 5.1 Format können Inhaltsanbieter die Größe von Multichannel-Audiodateien komprimieren, ohne die Klangqualität zu beeinträchtigen. AC-3 ist ein 5.1-Format, d. h. es bietet fünf Kanäle mit voller Bandbreite für ein umfassenderes Benutzererlebnis.

Weitere Informationen finden Sie unter [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html).

>[!IMPORTANT]
>
>TVSDK Version 1.4 unterstützt nur das AC-3 5.1-Format auf Amazon FireTV.

TVSDK unterstützt die folgenden AC-3 5.1-Funktionen:

* AC-3-Surround-Audio
* Gemischte/nicht gemischte Streams für Surround-Audio-Typ
* Möglichkeit, das Gerät abzufragen, um zu sehen, ob der Audio-Codec für die Umgebung auf dem Gerät verfügbar ist.

  Die Ergebnisse bestimmen, welcher bevorzugte Audio-Codec-Typ ausgewählt ist. Das Manifest mit dem Audio-Codec-Typ, das das Gerät nicht verwenden wird, wird verworfen. Wenn beispielsweise das AC-3-Format ausgewählt wurde, werden Profile mit dem AAC-Format (Advanced Audio Coding) nicht berücksichtigt.
* Durchlaufmodus

  Anstatt die Medien aus dem AC-3 5.1-Format in das PCM-Format (Multichannel Puls-Code Modulation) zu dekodieren, wird das TVSDK im Passthrough-Modus von den Decoder-Medien geändert oder nicht verändert (je nach Gerät). Dieses Medium wird an das Audiogerät (Lautsprecher oder Empfänger) gesendet, damit das Audiogerät den Dolby-Surround-Stream dekodieren und wiedergeben kann.

TVSDK unterstützt die AC-3 5.1-Funktionen nur auf dem Gerät Amazon Fire TV 1. Generation.

Die folgenden AC-3 5.1-Funktionen werden nicht unterstützt:

* Multichannel AAC-Audio
* ABR über verschiedene Codecs hinweg (AAC - AC3)

## Unterstützte Medien auswählen {#section_E1DFA1F472EA4BDE846C71A3343E275A}

Hier ist der typische Workflow, der auftritt, wenn TVSDK ein Manifest mit AC-3- und AAC-Medien findet:

1. TVSDK-Abfragen, die vom Gerät unterstützt werden können.
1. Der Codec mit der höheren Qualität wird ausgewählt.

   Die Reihenfolge der Qualität ist AC-3 > AAC.
1. TVSDK ignoriert Profile mit anderen Audio-Codec-Typen.

>[!TIP]
>
>Die Anwendung kann keine Informationen zu ignorierten Profilen abrufen.

## Ausgabemodus bestimmen {#section_64145D9824594C36AADBF0482C528767}

Wenn bei der Verarbeitung von AC-3-Medien ein Android-Gerät mit dem Lautsprechersystem verbunden ist, hängt die Entscheidung, Inhalte im Surround-Modus oder Stereo-Modus abzuspielen, davon ab, wie das Gerät konfiguriert ist.

|   | Surround-Sound | Stereo-Lautsprecher |
|---|---|---|
| Gerätekonfiguration - Dolby on (oder auto) | Gerätekonfiguration - Dolby on (oder auto) | Stereo-Modus |
| Gerätekonfiguration - Dolby Off | Stereo-Modus | Stereo-Modus |
