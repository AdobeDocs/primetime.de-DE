---
description: Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details seines Betriebs berücksichtigen und bestimmte Best Practices befolgen.
title: Überlegungen und Best Practices
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Überlegungen und Best Practices{#considerations-and-best-practices}

Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details seines Betriebs berücksichtigen und bestimmte Best Practices befolgen.

## Überlegungen {#section_tvsdk_considerations}

Beachten Sie bei Verwendung von TVSDK die folgenden Informationen:

* Adobe Primetime funktioniert nicht mit Emulatoren oder Simulatoren.

  Sie müssen echte Geräte zum Testen verwenden.
* Die Wiedergabe wird nur für HLS-Inhalte (HTTP Live Streaming) unterstützt.
* Hauptvideoinhalte können durch Multiplexing gesteuert werden, wobei Video- und Audio-Streams sich in derselben Ausgabedarstellung befinden oder nicht durch Multiplexing, wobei Video- und Audio-Streams in separaten Ausgabedarstellungen enthalten sind.
* Die TVSDK-API ist im ActionScript implementiert.
* Für die Videowiedergabe ist die Adobe Video Engine (AVE) erforderlich. Dies wirkt sich darauf aus, wie und wann auf Medienressourcen zugegriffen werden kann:

   * Verdeckte Untertitel werden in dem von der AVE bereitgestellten Umfang unterstützt.
   * Abhängig von der Genauigkeit des Kodierers unterscheidet sich die tatsächliche kodierte Mediendauer möglicherweise von der Dauer, die im Stream-Ressourcen-Manifest aufgezeichnet wird.

     Es gibt keine zuverlässige Methode, um zwischen der idealen virtuellen Timeline und der tatsächlichen Wiedergabescheitleiste neu zu synchronisieren. Das Fortschritts-Tracking der Stream-Wiedergabe für die Anzeigenverwaltung und Video Analytics muss die tatsächliche Wiedergabedauer verwenden, sodass bei der Berichterstellung und dem Verhalten der Benutzeroberfläche die Medien- und Werbeinhalte möglicherweise nicht genau verfolgt werden.
   * Dem eingehenden Benutzeragenten-Namen für alle HTTP-Anforderungen von TVSDK auf dieser Plattform wird das folgende Zeichenfolgenmuster zugewiesen:

     ```
     "Adobe Flash Player"
     ```

## Best Practices {#section_tvsdk_best_practices}

Hier finden Sie die empfohlenen Vorgehensweisen für TVSDK:

* Verwenden Sie HLS Version 3.0 oder höher für Programminhalte.
* Für TVSDK 1.4 für DHLS ist das verzögerte Laden von Anzeigen standardmäßig aktiviert.

  Für Inhalte ohne Pre-Roll oder Mid-Roll können Sie `AdvertisingMetadata.delayAdLoading` um das Laden von Inhalten noch zu beschleunigen.
