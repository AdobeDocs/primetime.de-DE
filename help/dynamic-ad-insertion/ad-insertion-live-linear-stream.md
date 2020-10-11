---
title: Ad Insertion in Live/Linear-Stream verwenden
description: Ad Insertion in Live/Linear-Stream verwenden
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Ad Insertion in Live/Linear-Stream verwenden {#ad-insertion-live-linear-stream}

Primetime-Ad Insertion bietet Herausgebern die Möglichkeit, standardmäßige und komplexe Anzeigeneinfügesituationen zu bearbeiten, die während der Live-/linearen Streams auftreten.

## Unterstützte Cue-Formate {#cue-formats-supported}

Primetime Ad Insertion unterstützt eine breite Palette an Standard- und Nicht-Standard-Cue-Formaten, darunter:

* DPI SCTE-35 (erweiterte Anzeigenmarken mit SCTE-35)

* [Adobe Digital Programm Insertion Signaling Specification](https://www.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeDigitalProgramInsertionSignalingSpecification.pdf)

* Binärdatei SCTE-35

Wenden Sie sich an Ihren Primetime-Support-Mitarbeiter, um weitere Informationen oder andere unterstützte Cue-Formate zu erhalten.

## Unterstützung für teilweise Werbeunterbrechungen {#partial-ad-break-support}

Teilweise Werbeunterbrechungen können in Situationen verwendet werden, in denen ein Viewer nach Beginn einer Werbeunterbrechung in einen Live-/linearen Stream wechselt.  Wenn ein Viewer beispielsweise eine 2:00-lange Werbeunterbrechung mit dem 1:00-Zeichen eingibt, wird durch das Einfügen von Werbeunterbrechungen sichergestellt, dass Anzeigen in der verbleibenden Zeit bereitgestellt werden. Ohne das Einfügen von Werbeunterbrechungen würden diesem Viewer während der Pause keine Anzeigen bereitgestellt. Primetime-Ad Insertion aktiviert standardmäßig das Einfügen von Teilen-Werbeunterbrechungen, wenn die entsprechenden Tags im/den Medienstream/s vorhanden sind.

## Frühzeitige Rückkehr (Vorzeitiger Anzeigenausstieg) {#early-return-early-ad-exit}

Es gibt Fälle, in denen es erforderlich sein kann, frühzeitig von einer Werbeunterbrechung in einem Live-/linearen Stream zurückzukehren, z. B. wenn ein sportliches Ereignis plötzlich zu einer Aktion zurückkehrt. Jedes Entscheidungsformat der Anzeige enthält ein Tag zum &quot;Cue-out&quot;(Anzeigen) oder &quot;Cue-in&quot;(Inhalt). Wenn vor dem Ende einer Werbeunterbrechung ein &quot;Cue-in&quot;-Tag gefunden wird, berücksichtigt Adobe Primetime Ad Insertion das Cue-In. Wenden Sie sich an Ihren Content Packager, um eine frühzeitige Rückkehr zu ermöglichen.
