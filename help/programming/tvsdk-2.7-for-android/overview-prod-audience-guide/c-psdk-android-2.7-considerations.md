---
description: Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details seines Betriebs berücksichtigen und bestimmte Best Practices befolgen.
title: Überlegungen und Best Practices
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Überlegungen und Best Practices{#considerations-and-best-practices}

Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details seines Betriebs berücksichtigen und bestimmte Best Practices befolgen.

## Überlegungen {#section_tvsdk_considerations}

Beachten Sie bei Verwendung von TVSDK die folgenden Informationen:

* Die TVSDK-API ist in Java implementiert.
* Adobe Primetime funktioniert derzeit nicht mit Android-Emulatoren.

  Sie müssen echte Geräte zum Testen verwenden.
* Die Wiedergabe wird nur für HLS-Inhalte (HTTP Live Streaming) unterstützt.
* Hauptvideoinhalte können durch Multiplexing (Video- und Audio-Streams in derselben Ausgabedarstellung) oder durch Nicht-Multiplexing (Video- und Audio-Streams in separaten Ausgabedarstellungen) wiedergegeben werden.
* Derzeit müssen Sie die meisten TVSDK-API-Vorgänge im UI-Thread ausführen, der der Android-Haupt-Thread ist.

  Vorgänge, die ordnungsgemäß im Haupt-Thread ausgeführt werden, können einen Fehler auslösen und beenden, wenn sie in einem Hintergrund-Thread ausgeführt werden.
* Für die Videowiedergabe ist die Adobe Video Engine (AVE) erforderlich. Dies wirkt sich darauf aus, wie und wann auf Medienressourcen zugegriffen werden kann:

   * Verdeckte Untertitel werden in dem von der AVE bereitgestellten Umfang unterstützt.
   * Abhängig von der Genauigkeit des Kodierers unterscheidet sich die tatsächliche kodierte Mediendauer möglicherweise von der Dauer, die im Stream-Ressourcen-Manifest aufgezeichnet wird.

     Es gibt keine zuverlässige Methode, um zwischen der idealen virtuellen Timeline und der tatsächlichen Wiedergabescheitleiste neu zu synchronisieren. Das Fortschritts-Tracking der Stream-Wiedergabe für die Anzeigenverwaltung und Video Analytics muss die tatsächliche Wiedergabedauer verwenden, sodass bei der Berichterstellung und dem Verhalten der Benutzeroberfläche die Medien- und Werbeinhalte möglicherweise nicht genau verfolgt werden.
   * Dem eingehenden Benutzeragenten-Namen für alle Medienanfragen des TVSDK auf dieser Plattform wird das folgende Zeichenfolgenmuster zugewiesen:

  ```
  "Adobe Primetime/" + 
  <varname>
  originalUserAgent
  </varname> 
  ```

  Alle anzeigenbezogenen Aufrufe verwenden den standardmäßigen Android-Benutzeragenten oder den benutzerdefinierten Benutzeragenten, wenn Sie ihn beim Einrichten von Anzeigeneinfüge-Metadaten festlegen.

## Best Practices {#section_tvsdk_best_practices}

Hier finden Sie empfohlene Vorgehensweisen für TVSDK:

* Verwenden Sie HLS Version 3.0 oder höher für Programminhalte.
* Führen Sie die meisten TVSDK-Vorgänge im Haupt-Thread (UI) aus, nicht in Hintergrund-Threads.
* Für TVSDK 2.5 für Android ist die verzögerte Anzeigenauflösung standardmäßig aktiviert.

  Für Inhalte ohne Pre-Roll oder Mid-Roll können Sie `AdvertisingMetadata.setPreroll(false)` um das Laden von Inhalten zu beschleunigen.
