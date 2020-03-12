---
description: Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers liest (globale Konfiguration oder Mandantenkonfiguration), werden die Konfigurationsinformationen im Arbeitsspeicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanforderung von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden.
seo-description: Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers liest (globale Konfiguration oder Mandantenkonfiguration), werden die Konfigurationsinformationen im Arbeitsspeicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanforderung von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden.
seo-title: Konfigurationsdateien aktualisieren
title: Konfigurationsdateien aktualisieren
uuid: 34b3247c-3458-49de-b1b0-dc0ebbf61c88
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Konfigurationsdateien aktualisieren{#updating-configuration-files}

Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers liest (globale Konfiguration oder Mandantenkonfiguration), werden die Konfigurationsinformationen im Arbeitsspeicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanforderung von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden.

Wenn Sie die Konfigurationsdatei ändern, speichert der Lizenzserver den Zeitpunkt, zu dem die Datei zuletzt geändert wurde. In einem konfigurierbaren Intervall prüft der Server, ob sich die Dateiänderungszeit geändert hat. Wenn er geändert wurde, lädt der Server automatisch den Inhalt der Konfigurationsdatei neu.

Wenn Sie steuern möchten, wie oft der Server nach Updates sucht, müssen Sie das `refreshDelaySeconds` Attribut im Element der globalen Konfigurationsdatei `Caching` festlegen. Wenn `refreshDelaySeconds` die Konfiguration beispielsweise auf 3600 Sekunden festgelegt ist, aktualisiert der Server die Konfiguration innerhalb von höchstens einer Stunde nach der Änderungszeit der Konfigurationsdatei. Wenn der Wert auf 0 gesetzt `refreshDelaySeconds` ist, sucht der Server bei jeder Anforderung nach Konfigurationsaktualisierungen. Es wird nicht empfohlen, dass Sie in einer beliebigen Produktions-Umgebung `refreshDelaySeconds` auf einen niedrigen Wert setzen, da dies die Leistung beeinträchtigen kann.

Das `Caching` Element steuert auch, wie viele Mandantenkonfigurationen gleichzeitig zwischengespeichert werden. Sie können diesen Wert auf eine Zahl setzen, die kleiner als die Gesamtanzahl der Mieter ist, um die Menge des Speichers zu begrenzen, der zum Zwischenspeichern der Konfigurationsinformationen verwendet wird. Wenn eine Anforderung für einen Mandanten empfangen wird, der sich nicht im Cache befindet, wird die Konfiguration geladen, bevor die Anforderung verarbeitet werden kann. Wenn der Cache voll ist, wird der zuletzt verwendete Mandant aus dem Cache entfernt.

Die zwischengespeicherte Version der Konfiguration wird in folgenden Situationen weiterhin verwendet (bis zum nächsten Mal, wenn der Server nach Updates sucht):

* Wenn eine Änderung in einer Konfigurationsdatei oder einer der Zertifikatdateien gespeichert wird, auf die in der [!DNL flashaccess-tenant.xml] Datei verwiesen wird, während der Server versucht, die Datei zu lesen
* Wenn der Zeitstempel der Datei vor der aktuellen Zeit weniger als eine Sekunde liegt
* Wenn der Zeitstempel der Datei in der Zukunft liegt

Wenn keine zwischengespeicherte Version vorhanden ist, schlägt das Laden der Konfiguration fehl und ein Fehler wird an den Client zurückgegeben. Der Server versucht dann, die Datei erneut zu laden, wenn er das nächste Mal eine Anforderung für diesen Mandanten erhält.

## Aktualisieren der globalen Konfigurationsdatei {#section_AA546C72442646CFB8906AEEBDF50587}

Sie können das HSM-Kennwort jederzeit ändern [!DNL flashaccess-global.xml] . Die Änderungen werden beim nächsten Laden der Konfigurationsdatei durch den Server wirksam. Änderungen an den Elementen &quot;Protokollierung&quot;und &quot;Zwischenspeicherung&quot;werden jedoch nicht neu geladen. Sie müssen den Server neu starten, bevor Änderungen an diesen Elementen wirksam werden.

## Aktualisieren der Mandant-Konfigurationsdatei {#section_71624DB8DF28480F84F34F0FF7FD4365}

Sie können jederzeit alle in der [!DNL flashaccess-tenant.xml] Datei angegebenen Werte ändern. Die Änderungen werden beim nächsten Laden der Konfigurationsdatei durch den Server wirksam. Der Server sucht außerdem nach allen Änderungen in allen Berechtigungsdateien ( [!DNL .pfx]) und in den Whitelist-Zertifikatdateien des Packager, auf die in der Mietkonfigurationsdatei verwiesen wird.
