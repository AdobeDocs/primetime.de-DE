---
description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
title: API-Änderungen beim Löschen und Ersetzen von Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# API-Änderungen beim Löschen und Ersetzen von Anzeigen {#ad-deletion-and-replacement-api-changes}

TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.

Die Funktion zum Löschen und Ersetzen erweitert die Funktion für benutzerdefinierte Anzeigenmarkierungen. Benutzerdefinierte Anzeigenmarkierungen markieren Abschnitte des Hauptinhalts als anzeigenbezogene Inhaltszeiträume. Neben der Kennzeichnung dieser Zeiträume können Sie auch Zeitbereiche löschen und ersetzen.

<!--<a id="section_7A90BFE99F1A4D908D6DDB0B49FA1199"></a>-->

Die folgenden Änderungen an TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.

**Neue APIs**

* `PTTimeRangeCollection` ist eine öffentliche Klasse, die einen vordefinierten Satz von Bereichen und einen Typ definiert:

   * `property PTTimeRangeCollectionType type` gibt den Typ des Zeitraums an.
   * `property NSArray* ranges` wird zum Festlegen der Zeiträume verwendet.

     Der erwartete Typ von Objekten im Array ist `PTReplacementTimeRange` oder `CMTimeRange`.

     >[!TIP]
     >
     >Alle Objekte des Arrays müssen denselben Typ aufweisen.

   * `PTTimeRangeCollectionType` ist ein Enum, das das Verhalten für die in der Variablen `PTTimeRangeCollection`:

      * `PTTimeRangeCollectionTypeMarkRanges`: Der Typ der Bereiche ist *Mark*. Die Bereiche werden verwendet, um die Bereiche im Inhalt als Anzeigen zu kennzeichnen.

      * `PTTimeRangeCollectionTypeDeleteRanges`: Der Typ der Bereiche ist Löschen. Die definierten Bereiche werden vor dem Einfügen der Anzeige aus dem Hauptinhalt entfernt.
      * `PTTimeRangeCollectionTypeReplaceRanges`: Der Typ der Bereiche ist Ersetzen. Die definierten Bereiche werden von der Hauptseite durch Anzeigen ersetzt (der Anzeigemodus ist auf `PTAdSignalingModeCustomTimeRanges`).

* `PTReplacementTimeRange` - Neue öffentliche Klasse, die einen einzelnen Bereich der `PTTimeRangeCollection`:

   * `property CMTimeRange range` - Definiert den Beginn und die Dauer des Bereichs.
   * `property long replacementDuration` - Wenn der Typ der `TimeRangeCollection` is `PTTimeRangeCollectionTypeReplaceRanges`, die `replacementDuration` wird verwendet, um eine Platzierungsmöglichkeit (Anzeigeneinfügung) mit einer Dauer von `replacementDuration`. Wenn die Variable `replacementDuration` nicht festgelegt ist, bestimmt der Anzeigenserver die Dauer und Anzahl der Anzeigen für diese Platzierungsmöglichkeit.

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges` - Es wurde ein neuer Typ von `PTAdSignalingMode`. Dieser Modus wird zusammen mit dem `PTTimeRangeCollection` mit Typ `PTTimeRangeCollectionReplace` für Anzeigeneinfügungen basierend auf den Ersatzbereichen.

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection` - Zum Festlegen der Zeitbereiche, die im Wiedergabeinhalt in den Bereichen zum Markieren/Löschen/Ersetzen verwendet werden.

* Warnprotokolle:

   * `UNDEFINED_TIME_RANGES`

      * Typ - Warnung
      * Beschreibung - Der Anzeigesignalmodus ist als benutzerdefinierte Bereiche definiert, die benutzerdefinierten Bereiche sind jedoch nicht definiert.

   * `INVALID_TIME_RANGES`

      * Typ - Warnung
      * Beschreibung - Ein oder mehrere Zeitbereiche sind ungültig und werden ignoriert oder geändert.

**Eingestellte APIs**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges` - Diese Eigenschaft wurde zuvor verwendet, um C3-Bereiche für die Kennzeichnung zu definieren. Sie wird jetzt nicht mehr unterstützt, da diese Bereiche über eingestellt werden. `PTTimeRangeCollection`.
