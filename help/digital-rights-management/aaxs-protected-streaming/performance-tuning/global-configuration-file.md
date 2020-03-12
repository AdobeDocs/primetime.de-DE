---
seo-title: Globale Konfigurationsdatei
title: Globale Konfigurationsdatei
uuid: 48c45f56-55c2-4526-b854-5552caf21541
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Globale Konfigurationsdatei{#global-configuration-file}

Die größte Auswirkung auf die Leistung können Sie durch die Verwendung der Einstellungen in der globalen Konfigurationsdatei &quot;flashaccess-global.xml&quot;erzielen. Zu diesen Einstellungen gehören die `<Caching>` Elemente und `<Logging>` -Elemente.

* `<Caching>` Das `<Caching>` Element steuert die Zwischenspeicherung von Konfigurationsdateien im Speicher. Das `<Caching>` -Element hat folgende Syntax:

   ```
   <Caching refreshDelaySeconds="..." numTenants="..."/>
   ```

   * `refreshDelaySeconds` steuert, wie oft der Server nach Aktualisierungen der Konfigurationsdateien sucht. Ein niedriger Wert für `refreshDelaySeconds` negative Auswirkungen auf die Leistung, während ein höherer Wert die Leistung verbessern kann. Weitere Informationen zu `refreshDelaySeconds`finden Sie unter[Aktualisieren von Konfigurationsdateien](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md).

   * `numTenants` gibt die Anzahl der Mieter an. Ein Wert, der niedriger als die Anzahl der Mieter ist, wirkt sich auf die Leistung aus, da Anforderungen an die verbleibenden Mieter zu Cache-Fehlern führen. Ein Cache-Fehlschlag für Konfigurationsdaten hat negative Auswirkungen auf die Leistung. Adobe empfiehlt daher, diesen Wert höher als die Anzahl der für den Server konfigurierten Mieter festzulegen, es sei denn, es bestehen Speicherbeschränkungen.

* `<Logging>` Das `<Logging>` Element gibt die Protokollierungsstufe und die Häufigkeit des Rollierens von Protokolldateien an. Das `<Logging>` -Element hat folgende Syntax:

   ```
   <Logging level="..." rollingFrequency=""/>
   ```

   * `level` gibt die zu protokollierenden Meldungen an. Der Wert &quot;DEBUG&quot;liefert viele Protokollmeldungen und kann sich negativ auf die Leistung auswirken. Adobe empfiehlt die Einstellung &quot;WARN&quot;für eine optimale Leistung. Dieser Wert birgt jedoch das Risiko, wesentliche Laufzeitinformationen wie Lizenzprüfungen zu verlieren. Verwenden Sie den Wert &quot;INFO&quot;, um wertvolle Protokollinformationen mit minimaler Auswirkung auf die Leistung zu erhalten.
   * `rollingFrequency` gibt an, wie oft Protokolldateien *rolliert* werden. Die Rollierung ist der Prozess, bei dem eine neue Protokolldatei zum aktiven Protokoll wird, während die zuvor aktive Protokolldatei nicht mehr in das Protokoll geschrieben wird und als rollierend betrachtet wird. Das rollierende Intervall kann auf &quot;MINUTELY&quot;, &quot;STUNDE&quot;, &quot;TWICE-DAILY&quot;, &quot;DAILY&quot;, &quot;WEEKLY&quot;, &quot;MONATLICH&quot;oder &quot;NEVER&quot;eingestellt werden.

Weitere Tipps zur Leistungsoptimierung finden Sie unter Adobe Access SDK zum Schutz von Inhalten *verwenden* .
