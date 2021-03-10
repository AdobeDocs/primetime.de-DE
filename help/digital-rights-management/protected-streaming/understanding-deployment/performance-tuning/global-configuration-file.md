---
description: In diesem Thema werden leistungsbezogene Aspekte beschrieben. Alle Einstellungen in der globalen Konfigurationsdatei "flashaccess-global.xml"wirken sich auf die Leistung aus.
title: Globale Konfigurationsdatei
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Leistungsoptimierung {#performance-tuning}

In diesem Thema werden leistungsbezogene Aspekte beschrieben. Alle Einstellungen in der globalen Konfigurationsdatei &quot;flashaccess-global.xml&quot;wirken sich auf die Leistung aus.

## Globale Konfigurationsdatei {#global-configuration-file}

Die Konfigurationsdatei enthält die folgenden Einstellungselemente:

* `<Caching>` Das  `<Caching>` Element steuert die Zwischenspeicherung von Konfigurationsdateien im Speicher. Das `<Caching>`-Element unterstützt die folgende Syntax:

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` Steuert, wie oft der Server nach Aktualisierungen der Konfigurationsdateien sucht. Ein niedriger Wert für `refreshDelaySeconds` wirkt sich negativ auf die Leistung aus, während ein höherer Wert die Leistung verbessern kann.

   Weitere Informationen zu `refreshDelaySeconds` finden Sie unter *Konfigurationsdateien aktualisieren*.

* `numTenants` gibt die Anzahl der Mieter an. Ein Wert, der niedriger als die Anzahl der Mieter ist, wirkt sich auf die Leistung aus, da Anforderungen an die verbleibenden Mieter zu Cache-Fehlern führen. Ein Cache-Ausfall für Konfigurationsdaten beeinträchtigt die Leistung. Es wird daher empfohlen, diesen Wert höher als die Anzahl der Mieter festzulegen, die für den Server konfiguriert sind, es sei denn, es gibt Speicherbeschränkungen, die Sie berücksichtigen müssen.

* `<Logging>` Das  `<Logging>` Element gibt die Protokollierungsstufe und die Häufigkeit an, mit der Protokolldateien rolliert werden. Das `<Logging>`-Element unterstützt die folgende Syntax:

   ```
   <Logging level="..." rollingFrequency="..."/>
   ```

* `<level>`  `level` gibt Meldungen in ein Protokoll ein. Der Wert `DEBUG` liefert viele Protokollmeldungen, was sich negativ auf die Leistung auswirken kann. Es wird empfohlen, für eine optimale Leistung die Einstellung `WARN` anzuwenden. Dieser Wert kann jedoch dazu führen, dass wichtige Laufzeitinformationen wie Lizenzprüfungen verloren gehen. Wenn Sie Protokollinformationen mit minimaler Auswirkung auf die Leistung speichern möchten, müssen Sie den Wert `INFO` anwenden.

* `<rollingFrequency>`  `rollingFrequency` gibt an, wie oft Protokolldateien  *rolliert* werden. *`Rolling`* ist ein Prozess, der jede neue Protokolldatei als aktives Protokoll bezeichnet. Daher kann die zuvor aktive Protokolldatei nicht mehr geändert werden und gilt als *`rolled`*. Sie können das rollierende Intervall auf `MINUTELY`, `HOURLY`, `TWICE-DAILY`, `DAILY`, `WEEKLY`, `MONTHLY` oder `NEVER` festlegen.

Tipps zur Leistungsoptimierung finden Sie unter *Verwenden des Adobe Primetime DRM SDK for Protection Content*.