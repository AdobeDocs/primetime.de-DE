---
description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
seo-description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
seo-title: Löschen und Ersetzen von Anzeigen in VOD-Streams
title: Löschen und Ersetzen von Anzeigen in VOD-Streams
uuid: 8f51c413-a8c9-46c1-aec6-0d536feaaeb7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---


# Änderungen an der API zum Löschen und Ersetzen von Anzeigen {#ad-deletion-and-replacement-api-changes}

TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.

Die Funktion zum Löschen und Ersetzen erweitert die Funktion für benutzerdefinierte Anzeigenmarken. Benutzerspezifische Anzeigenmarkierungen markieren Abschnitte des Hauptinhalts als inhaltliche Zeiträume für Anzeigen. Neben der Kennzeichnung dieser Zeiträume können Sie auch Zeitbereiche löschen und ersetzen.

Die folgenden Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.

**Neue APIs**

* `PTTimeRangeCollection` ist eine öffentliche Klasse, die einen vordefinierten Satz von Bereichen und einen Typ definiert:

   * `property PTTimeRangeCollectionType type` gibt den Typ des Zeitraums an.
   * `property NSArray* ranges` wird verwendet, um die Zeiträume festzulegen.

      Der erwartete Objekttyp im Array ist `PTReplacementTimeRange` oder `CMTimeRange`.

      >[!TIP]
      >
      >Alle Objekte des Arrays müssen denselben Typ aufweisen.

   * `PTTimeRangeCollectionType` ist ein Enum, das das Verhalten für die Bereiche definiert, die in der  `PTTimeRangeCollection`:

      * `PTTimeRangeCollectionTypeMarkRanges`: Der Typ der Bereiche ist  *Mark*. Die Bereiche werden verwendet, um die Bereiche im Inhalt als Anzeigen zu kennzeichnen.

      * `PTTimeRangeCollectionTypeDeleteRanges`: Der Typ der Bereiche ist Löschen. Die definierten Bereiche werden vor dem Einfügen der Anzeige aus dem Hauptinhalt entfernt.
      * `PTTimeRangeCollectionTypeReplaceRanges`: Der Typ der Bereiche ist &quot;Ersetzen&quot;. Die definierten Bereiche werden vom Hauptteil durch Anzeigen ersetzt (der Anzeigensignalisierungsmodus ist auf `PTAdSignalingModeCustomTimeRanges` eingestellt).

* `PTReplacementTimeRange` - Neue öffentliche Klasse, die einen einzigen Bereich definiert  `PTTimeRangeCollection`:

   * `property CMTimeRange range` - Definiert den Beginn und die Dauer des Bereichs.
   * `property long replacementDuration` - Wenn der Typ des  `TimeRangeCollection` Artikels  `PTTimeRangeCollectionTypeReplaceRanges`ist,  `replacementDuration` wird er verwendet, um eine Platzierungsmöglichkeit (Anzeigeneinfügung) mit einer Dauer von  `replacementDuration`1000 zu erstellen. Ist `replacementDuration` nicht eingestellt, bestimmt der Anzeigen-Server die Dauer und die Anzahl der Anzeigen für diese Platzierungsmöglichkeit.

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges` - Es wurde ein neuer Typ von hinzugefügt  `PTAdSignalingMode`. Dieser Modus wird in Verbindung mit dem `PTTimeRangeCollection` mit dem Typ `PTTimeRangeCollectionReplace` für Anzeigeneinfügung verwendet, basierend auf den Ersatzbereichen.

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection` - Zum Festlegen der Zeiträume, die im Bereich &quot;mark/delete/replace&quot;im Wiedergabeinhalt verwendet werden.

* Warnprotokolle:

   * `UNDEFINED_TIME_RANGES`

      * Typ - Warnung
      * Beschreibung - Der Anzeigensignalisierungsmodus ist als benutzerdefinierter Bereich definiert, die benutzerdefinierten Bereiche sind jedoch nicht definiert.
   * `INVALID_TIME_RANGES`

      * Typ - Warnung
      * Beschreibung - Ein oder mehrere Zeitbereiche sind ungültig und werden ignoriert oder geändert.


**Veraltete APIs**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges` - Diese Eigenschaft wurde zuvor zur Definition von C3-Bereichen für die Kennzeichnung verwendet. Es ist jetzt veraltet, da diese Bereiche über `PTTimeRangeCollection` festgelegt werden.