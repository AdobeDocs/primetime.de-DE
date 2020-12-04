---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität des Mediums lokal wiedergegeben wird.
seo-description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität des Mediums lokal wiedergegeben wird.
seo-title: Format AC-3 5.1
title: Format AC-3 5.1
uuid: d5e77bb5-ed51-4f9f-b34f-e9082f5ee4de
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---


# Format AC-3 5.1{#ac-format}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität des Mediums lokal wiedergegeben wird.

Primetime kann nicht vor solchen Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen. Das Primetime-Streaming bietet jedoch einen Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Serverausfällen oder Betriebsausfällen zu schützen, was eine bessere Benutzererfahrung ermöglicht. TVSDK implementiert Failover-Schutz, um Unterbrechungen bei der Wiedergabe zu minimieren und trotz Übertragungsproblemen eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Mediensatz, wenn vollständige Darstellungen oder Fragmente nicht verfügbar sind.

Mit dem Audiocodec 3 (AC-3, auch Dolby Digital® genannt) 5.1 Format können Content Provider die Größe von Mehrkanal-Audiodateien komprimieren, ohne die Klangqualität zu beeinträchtigen. AC-3 ist ein 5.1-Format, d. h. es bietet fünf Kanal mit voller Bandbreite für eine verbesserte Benutzerfreundlichkeit.

Weitere Informationen finden Sie unter [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html).

>[!IMPORTANT]
>
>TVSDK Version 1.4 unterstützt das Format AC-3 5.1 nur auf Amazon FireTV.

TVSDK unterstützt die folgenden AC-3 5.1-Funktionen:

* AC-3-Surround-Audio
* Gemischte/nicht gemischte Streams für den Surround-Audiotyp
* Möglichkeit zur Abfrage des Geräts, um zu sehen, ob der Surround-Audio-Codec auf dem Gerät verfügbar ist.

   Die Ergebnisse bestimmen, welcher bevorzugte Audio-Codec-Typ ausgewählt wird. Das Manifest mit dem Audiocodec-Typ, das das Gerät nicht verwenden wird, wird verworfen. Wenn beispielsweise das AC-3-Format ausgewählt wurde, werden Profile mit dem AAC-Format (Advanced Audio Coding) nicht berücksichtigt.
* Übergangsmodus

   Im Passthrough-Modus wird das TVSDK nicht mehr vom AC-3 5.1-Format in ein PCM-Format (Multichannel Puls-Code Modulation) dekodiert, sondern verändert oder unmodifiziert (je nach Gerät) Dolby-Medien aus dem Decoder. Dieses Medium wird an das Audiogerät (Lautsprecher oder Empfänger) gesendet, damit das Audiogerät den Dolby-Surround-Stream dekodieren und wiedergeben kann.

TVSDK unterstützt die AC-3 5.1 Funktionen nur auf dem Gerät Amazon Fire TV 1. Generation.

Die folgenden AC-3 5.1-Funktionen werden nicht unterstützt:

* Multichannel AAC-Audio
* ABR für verschiedene Codecs (AAC - AC3)

## Auswählen unterstützter Medien {#section_E1DFA1F472EA4BDE846C71A3343E275A}

Hier ist der typische Arbeitsablauf, der auftritt, wenn TVSDK ein Manifest mit AC-3- und AAC-Medien findet:

1. TVSDK-Abfragen, die vom Gerät unterstützt werden können.
1. Der Codec mit der höheren Qualität wird ausgewählt.

   Die Reihenfolge der Qualität ist AC-3 > AAC.
1. TVSDK ignoriert Profile mit anderen Audio-Codec-Typen.

>[!TIP]
>
>Die Anwendung kann keine Informationen zu ignorierten Profilen abrufen.

## Festlegen des Ausgabemodus {#section_64145D9824594C36AADBF0482C528767}

Wenn bei der Verarbeitung von AC-3-Medien ein Android-Gerät an das Lautsprechersystem angeschlossen ist, hängt die Entscheidung, Inhalte im Surround-Modus oder Stereo-Modus abzuspielen, davon ab, wie das Gerät konfiguriert ist.

|  | Surround-Sound | Stereosprecher |
|---|---|---|
| Gerätekonfiguration - Dolby on (oder auto) | Gerätekonfiguration - Dolby on (oder auto) | Stereomodus |
| Gerätekonfiguration - Dolby off | Stereomodus | Stereomodus |

