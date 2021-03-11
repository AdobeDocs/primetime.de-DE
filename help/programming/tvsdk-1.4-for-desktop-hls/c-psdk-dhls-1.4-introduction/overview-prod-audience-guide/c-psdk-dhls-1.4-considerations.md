---
description: Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details zu seiner Funktionsweise berücksichtigen und bestimmte Best Practices befolgen.
title: Überlegungen und Best Practices
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Überlegungen und Best Practices{#considerations-and-best-practices}

Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details zu seiner Funktionsweise berücksichtigen und bestimmte Best Practices befolgen.

## Überlegungen {#section_tvsdk_considerations}

Beachten Sie bei Verwendung von TVSDK die folgenden Informationen:

* Adobe Primetime funktioniert nicht auf Emulatoren oder Simulatoren.

   Sie müssen echte Geräte zum Testen verwenden.
* Die Wiedergabe wird nur für HLS-Inhalte (HTTP Live Streaming) unterstützt.
* Hauptvideoinhalte können im Multiplex-Modus wiedergegeben werden, wobei Video- und Audiostreams in derselben Darstellung oder nicht im Multiplexverfahren vorliegen, wobei Video- und Audio-Streams in separaten Darstellungen wiedergegeben werden.
* Die TVSDK-API ist in ActionScript implementiert.
* Für die Videowiedergabe ist die Adobe Video Engine (AVE) erforderlich. Dies wirkt sich darauf aus, wie und wann auf Medienressourcen zugegriffen werden kann:

   * Untertitel werden in dem von der AVE bereitgestellten Umfang unterstützt.
   * Abhängig von der Genauigkeit des Encoder kann die tatsächliche Dauer der kodierten Medien von der Dauer abweichen, die im Stream-Ressourcenmanifest aufgezeichnet wird.

      Es gibt keine zuverlässige Methode, um zwischen der idealen virtuellen Zeitleiste und der tatsächlichen Wiedergabedauer neu zu synchronisieren. Die Fortschrittsverfolgung der Stream-Wiedergabe für die Anzeigenverwaltung und Video Analytics muss die tatsächliche Wiedergabedauer verwenden, sodass das Verhalten von Berichte und Benutzeroberfläche die Medien- und Anzeigeninhalte möglicherweise nicht genau verfolgen kann.
   * Dem Namen des eingehenden Benutzeragenten für alle HTTP-Anforderungen von TVSDK auf dieser Plattform wird das folgende Zeichenfolgenmuster zugewiesen:

      ```
      "Adobe Flash Player"
      ```

## Bewährte Verfahren {#section_tvsdk_best_practices}

Hier finden Sie die empfohlenen Vorgehensweisen für TVSDK:

* Verwenden Sie HLS Version 3.0 oder höher für Programm-Inhalte.
* Für TVSDK 1.4 für DHLS ist das verzögerte Laden von Anzeigen standardmäßig aktiviert.

   Bei Inhalten ohne Pre-Roll oder Mid-Roll können Sie `AdvertisingMetadata.delayAdLoading` verwenden, um das Laden von Inhalten noch schneller zu beschleunigen.

