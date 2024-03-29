---
description: Die folgenden Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.
title: Änderungen an der API zum Löschen und Ersetzen von Anzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Änderungen an der Anzeigen-Löschungs- und Ersatz-API{#ad-deletion-and-replacement-api-changes}

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

