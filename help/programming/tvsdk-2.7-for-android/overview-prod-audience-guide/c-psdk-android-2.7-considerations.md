---
description: Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details zu seiner Funktionsweise berücksichtigen und bestimmte Best Practices befolgen.
title: Überlegungen und Best Practices
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# Überlegungen und Best Practices{#considerations-and-best-practices}

Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details zu seiner Funktionsweise berücksichtigen und bestimmte Best Practices befolgen.

## Überlegungen {#section_tvsdk_considerations}

Beachten Sie bei Verwendung von TVSDK die folgenden Informationen:

* Die TVSDK-API ist in Java implementiert.
* Adobe Primetime funktioniert derzeit nicht auf Android-Emulatoren.

   Sie müssen echte Geräte zum Testen verwenden.
* Die Wiedergabe wird nur für HLS-Inhalte (HTTP Live Streaming) unterstützt.
* Hauptvideoinhalte können mehrfach (Video- und Audio-Streams in derselben Darstellung) oder nicht multipliziert (Video- und Audio-Streams in separaten Darstellungen) eingesetzt werden.
* Zurzeit müssen Sie die meisten TVSDK-API-Vorgänge im UI-Thread ausführen, dem Android-Haupt-Thread.

   Vorgänge, die ordnungsgemäß im Hauptthread ausgeführt werden, können einen Fehler auslösen und bei Ausführung in einem Hintergrundthread beendet werden.
* Für die Videowiedergabe ist die Adobe Video Engine (AVE) erforderlich. Dies wirkt sich darauf aus, wie und wann auf Medienressourcen zugegriffen werden kann:

   * Untertitel werden in dem von der AVE bereitgestellten Umfang unterstützt.
   * Abhängig von der Genauigkeit des Encoder kann die tatsächliche Dauer der kodierten Medien von der Dauer abweichen, die im Stream-Ressourcenmanifest aufgezeichnet wird.

      Es gibt keine zuverlässige Methode, um zwischen der idealen virtuellen Zeitleiste und der tatsächlichen Wiedergabedauer neu zu synchronisieren. Die Fortschrittsverfolgung der Stream-Wiedergabe für die Anzeigenverwaltung und Video Analytics muss die tatsächliche Wiedergabedauer verwenden, sodass das Verhalten von Berichte und Benutzeroberfläche die Medien- und Anzeigeninhalte möglicherweise nicht genau verfolgen kann.
   * Dem eingehenden Benutzeragenten-Namen für alle Medienanforderungen des TVSDK auf dieser Plattform wird das folgende Zeichenfolgenmuster zugewiesen:

   ```
   "Adobe Primetime/" + 
   <varname>
   originalUserAgent
   </varname> 
   ```

   Bei allen Anzeigentelefonaten wird der Standardbenutzer-Agent von Android oder der benutzerdefinierte Benutzeragent verwendet, wenn Sie ihn beim Einrichten der Metadaten für das Einfügen von Anzeigen festlegen.

## Bewährte Verfahren {#section_tvsdk_best_practices}

Hier finden Sie empfohlene Vorgehensweisen für TVSDK:

* Verwenden Sie HLS Version 3.0 oder höher für Programm-Inhalte.
* Führen Sie die meisten TVSDK-Vorgänge auf dem Haupt-(UI-)Thread und nicht auf Hintergrundthreads aus.
* Für TVSDK 2.5 für Android ist die verzögerte Anzeigenauflösung standardmäßig aktiviert.

   Bei Inhalten ohne Pre-Roll oder Mid-Roll können Sie `AdvertisingMetadata.setPreroll(false)` verwenden, um das Laden von Inhalten zu beschleunigen.
