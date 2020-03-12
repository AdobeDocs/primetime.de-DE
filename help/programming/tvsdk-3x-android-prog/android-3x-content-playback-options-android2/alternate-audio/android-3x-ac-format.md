---
description: Mit dem Audiocodec 3 (AC-3, auch Dolby Digital® genannt) 5.1 Format können Content Provider die Größe von Mehrkanal-Audiodateien komprimieren, ohne die Klangqualität zu beeinträchtigen. AC-3 ist ein 5.1-Format, d. h. es bietet fünf Kanal mit voller Bandbreite für eine verbesserte Benutzerfreundlichkeit.
seo-description: Mit dem Audiocodec 3 (AC-3, auch Dolby Digital® genannt) 5.1 Format können Content Provider die Größe von Mehrkanal-Audiodateien komprimieren, ohne die Klangqualität zu beeinträchtigen. AC-3 ist ein 5.1-Format, d. h. es bietet fünf Kanal mit voller Bandbreite für eine verbesserte Benutzerfreundlichkeit.
seo-title: Format AC-3 5.1
title: Format AC-3 5.1
uuid: 9d1adf33-4c9b-4d31-8212-ac301f3e44c5
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Format AC-3 5.1 {#ac-format}

Mit dem Audiocodec 3 (AC-3, auch Dolby Digital® genannt) 5.1 Format können Content Provider die Größe von Mehrkanal-Audiodateien komprimieren, ohne die Klangqualität zu beeinträchtigen. AC-3 ist ein 5.1-Format, d. h. es bietet fünf Kanal mit voller Bandbreite für eine verbesserte Benutzerfreundlichkeit.

Weitere Informationen finden Sie unter [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html).

TVSDK unterstützt die folgenden AC-3 5.1-Funktionen:

* AC-3-Surround-Audio
* Gemischte/nicht gemischte Streams für den Surround-Audiotyp
* Möglichkeit zur Abfrage des Geräts, um zu sehen, ob der Surround-Audio-Codec auf dem Gerät verfügbar ist.

   Die Ergebnisse bestimmen, welcher bevorzugte Audio-Codec-Typ ausgewählt wird. Das Manifest mit dem Audiocodec-Typ, das das Gerät nicht verwenden wird, wird verworfen. Wenn beispielsweise das AC-3-Format ausgewählt wurde, werden Profile mit dem AAC-Format (Advanced Audio Coding) nicht berücksichtigt.
* Übergangsmodus

   Im Passthrough-Modus wird das TVSDK nicht mehr vom AC-3 5.1-Format in ein PCM-Format (Multichannel Puls-Code Modulation) dekodiert, sondern verändert oder unmodifiziert (je nach Gerät) Dolby-Medien aus dem Decoder. Dieses Medium wird an das Audiogerät (Lautsprecher oder Empfänger) gesendet, damit das Audiogerät den Dolby-Surround-Stream dekodieren und wiedergeben kann.

>[!IMPORTANT]
>
>TVSDK unterstützt die AC-3 5.1 Funktionen nur auf dem Gerät Amazon Fire TV 1. Generation.

Die folgenden AC-3 5.1-Funktionen werden nicht unterstützt:

* Multichannel AAC-Audio
* ABR für verschiedene Codecs (AAC - AC3)

## Unterstützte Medien auswählen {#section_0D7E717BE18B418D817EE017EF2375D1}

Hier ist der typische Arbeitsablauf, der auftritt, wenn TVSDK ein Manifest mit AC-3- und AAC-Medien findet:

1. TVSDK-Abfragen, die vom Gerät unterstützt werden können.
1. Der Codec mit der höheren Qualität wird ausgewählt.

   Die Qualität wird in der folgenden Reihenfolge ausgewählt:

   1. AC-3
   1. AAC

1. TVSDK ignoriert Profile mit anderen Audio-Codec-Typen.

>[!TIP]
>
>Die Anwendung kann keine Informationen zu ignorierten Profilen abrufen.

## Festlegen des Ausgabemodus {#section_D2AFBF33D3904AC2A7C653A60C3A0CD3}

Wenn bei der Verarbeitung von AC-3-Medien ein Android-Gerät an das Lautsprechersystem angeschlossen ist, hängt die Entscheidung, Inhalte im Surround-Modus oder Stereo-Modus abzuspielen, davon ab, wie das Gerät konfiguriert ist.

|  | **Surround-Sound** | **Stereosprecher** |
|---|---|---|
| Gerätekonfiguration - Dolby on (oder auto) | Gerätekonfiguration - Dolby on (oder auto) | Stereomodus |
| Gerätekonfiguration - Dolby off | Stereomodus | Stereomodus |