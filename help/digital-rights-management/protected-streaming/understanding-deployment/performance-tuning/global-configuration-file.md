---
description: In diesem Thema werden leistungsbezogene Aspekte beschrieben. Alle Einstellungen in der globalen Konfigurationsdatei "flashaccess-global.xml"wirken sich auf die Leistung aus.
seo-description: In diesem Thema werden leistungsbezogene Aspekte beschrieben. Alle Einstellungen in der globalen Konfigurationsdatei "flashaccess-global.xml"wirken sich auf die Leistung aus.
seo-title: Globale Konfigurationsdatei
title: Globale Konfigurationsdatei
uuid: 254925b5-d441-4a35-ad6f-f99db5de7591
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Leistungsoptimierung {#performance-tuning}

In diesem Thema werden leistungsbezogene Aspekte beschrieben. Alle Einstellungen in der globalen Konfigurationsdatei &quot;flashaccess-global.xml&quot;wirken sich auf die Leistung aus.

## Globale Konfigurationsdatei {#global-configuration-file}

Die Konfigurationsdatei enthält die folgenden Einstellungselemente:

* `<Caching>` Das `<Caching>` Element steuert die Zwischenspeicherung von Konfigurationsdateien im Speicher. Das `<Caching>` -Element unterstützt die folgende Syntax:

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` Steuert, wie oft der Server nach Aktualisierungen der Konfigurationsdateien sucht. Ein niedriger Wert für `refreshDelaySeconds` negative Auswirkungen auf die Leistung, während ein höherer Wert die Leistung verbessern kann.

   Weitere Informationen finden Sie unter *Konfigurationsdateien* aktualisieren `refreshDelaySeconds`.

* `numTenants` gibt die Anzahl der Mieter an. Ein Wert, der niedriger als die Anzahl der Mieter ist, wirkt sich auf die Leistung aus, da Anforderungen an die verbleibenden Mieter zu Cache-Fehlern führen. Ein Cache-Ausfall für Konfigurationsdaten beeinträchtigt die Leistung. Es wird daher empfohlen, diesen Wert höher als die Anzahl der Mieter festzulegen, die für den Server konfiguriert sind, es sei denn, es gibt Speicherbeschränkungen, die Sie berücksichtigen müssen.

* `<Logging>` Das `<Logging>` Element gibt die Protokollierungsstufe und die Häufigkeit an, mit der Protokolldateien rolliert werden. Das `<Logging>` -Element unterstützt die folgende Syntax:

   ```
   <Logging level="..." rollingFrequency="..."/>
   ```

* `<level>`  Gibt Meldungen an `level` ein Protokoll an. Der Wert von `DEBUG` liefert viele Protokollmeldungen, die sich negativ auf die Leistung auswirken können. Es wird empfohlen, eine Einstellung für `WARN` eine optimale Leistung anzuwenden. Dieser Wert kann jedoch dazu führen, dass wichtige Laufzeitinformationen wie Lizenzprüfungen verloren gehen. Wenn Sie Protokollinformationen mit minimaler Auswirkung auf die Leistung speichern möchten, müssen Sie den Wert `INFO`&quot;anwenden&quot;.

* `<rollingFrequency>`  Gibt `rollingFrequency` an, wie oft Protokolldateien *rolliert* werden. *`Rolling`* ist ein Prozess, der jede neue Protokolldatei als aktives Protokoll bezeichnet. Daher kann die zuvor aktive Protokolldatei nicht mehr geändert werden und wird in Betracht gezogen *`rolled`*. Sie können das Rollierungsintervall auf `MINUTELY`, `HOURLY`, `TWICE-DAILY`, `DAILY`, `WEEKLY`, `MONTHLY`oder `NEVER`einstellen.

Tipps zur Leistungsoptimierung finden Sie unter *Verwenden des Adobe Primetime DRM-SDK zum Schutz von Inhalten* .