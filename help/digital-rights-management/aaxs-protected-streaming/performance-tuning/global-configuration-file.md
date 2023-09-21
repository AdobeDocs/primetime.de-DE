---
title: Globale Konfigurationsdatei
description: Globale Konfigurationsdatei
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Globale Konfigurationsdatei{#global-configuration-file}

Die größte Auswirkung auf die Leistung können Sie durch die Verwendung von Einstellungen in der globalen Konfigurationsdatei &quot;flashaccess-global.xml&quot;erzielen. Zu diesen Einstellungen gehören `<Caching>` und `<Logging>` -Elemente.

* `<Caching>` Die `<Caching>` -Element steuert das Zwischenspeichern von Konfigurationsdateien im Speicher. Die `<Caching>` -Element hat die folgende Syntax:

  ```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
  ```

   * `refreshDelaySeconds` steuert, wie oft der Server nach Aktualisierungen der Konfigurationsdateien sucht. Ein niedriger Wert für `refreshDelaySeconds` wirkt sich negativ auf die Leistung aus, während ein höherer Wert die Leistung verbessern kann. Weitere Informationen unter `refreshDelaySeconds`, siehe[Aktualisieren von Konfigurationsdateien](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)&quot;.

   * `numTenants` gibt die Anzahl der Mandanten an. Ein Wert, der niedriger ist als die Anzahl der Mandanten, wirkt sich wahrscheinlich auf die Leistung aus, da Anforderungen an die verbleibenden Mandanten zu Cache-Fehlern führen. Ein Cache-Ausfall für Konfigurationsdaten wirkt sich negativ auf die Leistung aus. Daher empfiehlt Adobe, diesen Wert höher als die Anzahl der für den Server konfigurierten Mandanten festzulegen, es sei denn, es gibt Speicherbeschränkungen.

* `<Logging>` Die `<Logging>` -Element gibt die Protokollierungsstufe und die Häufigkeit des Rollierens von Protokolldateien an. Die `<Logging>` -Element hat die folgende Syntax:

  ```
  <Logging level="..." rollingFrequency=""/>
  ```

   * `level` gibt die zu protokollierenden Nachrichten an. Der Wert &quot;DEBUG&quot;liefert viele Protokollmeldungen und kann sich negativ auf die Leistung auswirken. Adobe empfiehlt für optimale Leistung die Einstellung &quot;WARN&quot;. Dieser Wert birgt jedoch das Risiko, wesentliche Laufzeitinformationen wie Lizenzprüfungen zu verlieren. Verwenden Sie den Wert &quot;INFO&quot;, um wertvolle Protokollinformationen mit minimalen Auswirkungen auf die Leistung beizubehalten.
   * `rollingFrequency` gibt an, wie oft Protokolldateien *rollierend*. Beim Rollierenden Vorgang wird eine neue Protokolldatei zum aktiven Protokoll, während die zuvor aktive Protokolldatei nicht mehr in geschrieben wird und als rollierend betrachtet wird. Das rollierende Intervall kann auf &quot;MINUTELY&quot;, &quot;STÜNDLICH&quot;, &quot;TWICE-DAILY&quot;, &quot;DAILY&quot;, &quot;WEEKLY&quot;, &quot;MONTHLY&quot;oder &quot;NEVER&quot;eingestellt werden.

Siehe *Verwenden des Adobe Access SDK zum Schutz von Inhalten* für zusätzliche Tipps zur Leistungsoptimierung.
