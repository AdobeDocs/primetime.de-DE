---
description: In diesem Thema werden leistungsbezogene Aspekte beschrieben. Alle Einstellungen in der globalen Konfigurationsdatei flashaccess-global.xml wirken sich auf die Leistung aus.
title: Globale Konfigurationsdatei
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Leistungsoptimierung {#performance-tuning}

In diesem Thema werden leistungsbezogene Aspekte beschrieben. Alle Einstellungen in der globalen Konfigurationsdatei flashaccess-global.xml wirken sich auf die Leistung aus.

## Globale Konfigurationsdatei {#global-configuration-file}

Die Konfigurationsdatei enthält die folgenden Einstellungselemente:

* `<Caching>` Die `<Caching>` -Element steuert das Zwischenspeichern von Konfigurationsdateien im Speicher. Die `<Caching>` -Element unterstützt die folgende Syntax:

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` Steuert, wie oft der Server nach Aktualisierungen der Konfigurationsdateien sucht. Ein niedriger Wert für `refreshDelaySeconds` negative Auswirkungen auf die Leistung, während ein höherer Wert die Leistung verbessern kann.

  Siehe *Aktualisieren von Konfigurationsdateien* für weitere Informationen über `refreshDelaySeconds`.

* `numTenants` gibt die Anzahl der Mandanten an. Ein Wert, der kleiner als die Anzahl der Mandanten ist, wirkt sich auf die Leistung aus, da Anforderungen an die verbleibenden Mandanten zu Cache-Fehlern führen. Ein Cache-Ausfall für Konfigurationsdaten wirkt sich negativ auf die Leistung aus. Es wird daher empfohlen, diesen Wert höher als die Anzahl der für den Server konfigurierten Mandanten festzulegen, es sei denn, es gibt Speicherbeschränkungen, die Sie berücksichtigen müssen.

* `<Logging>` Die `<Logging>` -Element gibt die Protokollierungsstufe und die Häufigkeit an, mit der Protokolldateien rolliert werden. Die `<Logging>` -Element unterstützt die folgende Syntax:

  ```
  <Logging level="..." rollingFrequency="..."/>
  ```

* `<level>`  `level` gibt Meldungen in einem Protokoll an. Ein Wert von `DEBUG` liefert viele Protokollmeldungen, was sich negativ auf die Leistung auswirken kann. Es wird empfohlen, die Einstellung `WARN` für eine optimale Leistung. Dieser Wert kann jedoch dazu führen, dass wesentliche Laufzeitinformationen wie Lizenzprüfungen verloren gehen. Wenn Sie Protokollinformationen mit minimalen Auswirkungen auf die Leistung speichern möchten, müssen Sie den Wert `INFO`.

* `<rollingFrequency>`  `rollingFrequency` gibt an, wie oft Protokolldateien *rollierend*. *`Rolling`* ist ein Prozess, der jede neue Protokolldatei als aktives Protokoll bezeichnet. Daher kann die zuvor aktive Protokolldatei nicht mehr geändert werden und wird als *`rolled`*. Sie können das Rollierungsintervall auf `MINUTELY`, `HOURLY`, `TWICE-DAILY`, `DAILY`, `WEEKLY`, `MONTHLY`oder `NEVER`.

Siehe *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten* Tipps zur Leistungsoptimierung.
