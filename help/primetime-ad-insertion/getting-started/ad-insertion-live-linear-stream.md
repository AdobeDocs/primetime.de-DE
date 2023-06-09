---
title: Ad Insertion in Live/Linearstream verwenden
description: Verwenden von Ad Insertion im Live-/Linear-Stream
exl-id: d56ed723-ec72-4bbd-befc-6858c7c9d800
source-git-commit: 1bc2f6c230c262babf2958c32fee31afcad04c2f
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Ad Insertion in Live/Linearstream verwenden {#ad-insertion-live-linear-stream}

Mit Primetime-Ad Insertion können Herausgeber standardmäßige und komplexe Anzeigeneinfüge-Situationen handhaben, die in Live-/linearen Streams auftreten.

## Unterstützte Cue-Formate {#cue-formats-supported}

Primetime Ad Insertion unterstützt eine breite Palette standardmäßiger und nicht standardmäßiger Cue-Formate, darunter:

* DPI SCTE-35 (erweiterte SCTE-35-Anzeigenmarkierungen)

* [Adobe Digital Program Insertion Signaling Specification](assets/PrimetimeDigitalProgramInsertionSignalingSpecification.pdf)

* Binärer SCTE-35 (sowohl HLS als auch DASH)

* Text-SCTE-35 (sowohl HLS als auch DASH)

Wenden Sie sich an Ihren Primetime-Support-Mitarbeiter, um weitere Informationen oder andere unterstützte Cue-Formate zu erhalten.

## Unterstützung für teilweise Werbeunterbrechungen {#partial-ad-break-support}

Teilweise Werbeunterbrechungen können in Situationen verwendet werden, in denen ein Viewer nach dem Start einer Werbeunterbrechung in einen Live-/Linearstream gelangt.  Wenn ein Viewer beispielsweise eine 2:00-lange Werbeunterbrechung bei 1:00 Uhr eingibt, wird durch das Einfügen einer partiellen Werbeunterbrechung sichergestellt, dass Anzeigen in der verbleibenden Zeit bereitgestellt werden. Ohne partielles Einfügen einer Werbeunterbrechung werden diesem Viewer während der Pause keine Anzeigen bereitgestellt. Primetime-Ad Insertion ermöglicht standardmäßig das Einfügen einer partiellen Werbeunterbrechung, wenn die entsprechenden Tags in den Medien-Streams vorhanden sind.

## Frühzeitige Rückkehr (Beenden der frühzeitigen Anzeige) {#early-return-early-ad-exit}

Es gibt Fälle, in denen es erforderlich sein kann, frühzeitig von einer Werbeunterbrechung in einem Live-/linearen Stream zurückzukehren, z. B. wenn ein Sportereignis plötzlich zur Aktion zurückkehrt. Jedes Entscheidungsformat einer Anzeige enthält ein Tag zum &quot;Cue-out&quot;(Anzeigen) oder &quot;Cue-in&quot;(Inhalt)  Wenn vor dem Ende einer Werbeunterbrechung ein &quot;Cue-in&quot;-Tag auftritt, berücksichtigt Adobe Primetime Ad Insertion den Cue-in.  Wenden Sie sich an Ihren Content Packager, um eine frühe Rückkehr zu ermöglichen.
