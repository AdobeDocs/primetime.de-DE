---
title: Globale Konfigurationsdatei
description: Globale Konfigurationsdatei
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Globale Konfigurationsdatei{#global-configuration-file}

Die größte Auswirkung auf die Leistung können Sie durch die Verwendung der Einstellungen in der globalen Konfigurationsdatei &quot;flashaccess-global.xml&quot;erzielen. Zu diesen Einstellungen gehören die Elemente `<Caching>` und `<Logging>`.

* `<Caching>` Das  `<Caching>` Element steuert die Zwischenspeicherung von Konfigurationsdateien im Speicher. Das `<Caching>`-Element hat folgende Syntax:

   ```
   <Caching refreshDelaySeconds="..." numTenants="..."/>
   ```

   * `refreshDelaySeconds` steuert, wie oft der Server nach Aktualisierungen der Konfigurationsdateien sucht. Ein niedriger Wert für `refreshDelaySeconds` wirkt sich negativ auf die Leistung aus, während ein höherer Wert die Leistung verbessern kann. Weitere Informationen zu `refreshDelaySeconds` finden Sie unter &quot;[Aktualisieren von Konfigurationsdateien](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)&quot;.

   * `numTenants` gibt die Anzahl der Mieter an. Ein Wert, der niedriger als die Anzahl der Mieter ist, wirkt sich auf die Leistung aus, da Anforderungen an die verbleibenden Mieter zu Cache-Fehlern führen. Ein Cache-Fehlschlag für Konfigurationsdaten hat negative Auswirkungen auf die Leistung. Daher empfiehlt Adobe, diesen Wert höher als die Anzahl der für den Server konfigurierten Mandanten festzulegen, es sei denn, es bestehen Speicherbeschränkungen.

* `<Logging>` Das  `<Logging>` Element gibt die Protokollierungsstufe und die Häufigkeit des Rollierens von Protokolldateien an. Das `<Logging>`-Element hat folgende Syntax:

   ```
   <Logging level="..." rollingFrequency=""/>
   ```

   * `level` gibt die zu protokollierenden Meldungen an. Der Wert &quot;DEBUG&quot;liefert viele Protokollmeldungen und kann sich negativ auf die Leistung auswirken. Adobe empfiehlt die Einstellung &quot;WARN&quot; für eine optimale Leistung. Dieser Wert birgt jedoch das Risiko, wesentliche Laufzeitinformationen wie Lizenzprüfungen zu verlieren. Verwenden Sie den Wert &quot;INFO&quot;, um wertvolle Protokollinformationen mit minimaler Auswirkung auf die Leistung zu erhalten.
   * `rollingFrequency` gibt an, wie oft Protokolldateien  *rolliert* werden. Die Rollierung ist der Prozess, bei dem eine neue Protokolldatei zum aktiven Protokoll wird, während die zuvor aktive Protokolldatei nicht mehr in das Protokoll geschrieben wird und als rollierend betrachtet wird. Das rollierende Intervall kann auf &quot;MINUTELY&quot;, &quot;STUNDE&quot;, &quot;TWICE-DAILY&quot;, &quot;DAILY&quot;, &quot;WEEKLY&quot;, &quot;MONATLICH&quot;oder &quot;NEVER&quot;eingestellt werden.

Weitere Tipps zur Leistungsoptimierung finden Sie unter *Verwenden des Adobe Access SDK for Protection Content*.
