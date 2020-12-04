---
description: Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers liest (globale Konfiguration oder Mandantenkonfiguration), werden die Konfigurationsinformationen im Arbeitsspeicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanforderung von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden.
seo-description: Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers liest (globale Konfiguration oder Mandantenkonfiguration), werden die Konfigurationsinformationen im Arbeitsspeicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanforderung von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden.
seo-title: Konfigurationsdateien aktualisieren
title: Konfigurationsdateien aktualisieren
uuid: 34b3247c-3458-49de-b1b0-dc0ebbf61c88
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---


# Konfigurationsdateien aktualisieren{#updating-configuration-files}

Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers liest (globale Konfiguration oder Mandantenkonfiguration), werden die Konfigurationsinformationen im Arbeitsspeicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanforderung von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden.

Wenn Sie die Konfigurationsdatei ändern, speichert der Lizenzserver den Zeitpunkt, zu dem die Datei zuletzt geändert wurde. In einem konfigurierbaren Intervall prüft der Server, ob sich die Dateiänderungszeit geändert hat. Wenn er geändert wurde, lädt der Server automatisch den Inhalt der Konfigurationsdatei neu.

Wenn Sie steuern möchten, wie oft der Server nach Updates sucht, müssen Sie das `refreshDelaySeconds`-Attribut im `Caching`-Element der globalen Konfigurationsdatei festlegen. Wenn `refreshDelaySeconds` beispielsweise auf 3600 Sekunden eingestellt ist, aktualisiert der Server die Konfiguration innerhalb von höchstens einer Stunde nach der Änderungszeit der Konfigurationsdatei. Ist `refreshDelaySeconds` auf 0 gesetzt, sucht der Server bei jeder Anforderung nach Konfigurationsaktualisierungen. Es wird nicht empfohlen, `refreshDelaySeconds` in einer beliebigen Produktions-Umgebung auf einen niedrigen Wert festzulegen, da dies die Leistung beeinträchtigen kann.

Das `Caching`-Element steuert auch, wie viele Mandantenkonfigurationen gleichzeitig zwischengespeichert werden. Sie können diesen Wert auf eine Zahl setzen, die kleiner als die Gesamtanzahl der Mieter ist, um die Menge des Speichers zu begrenzen, der zum Zwischenspeichern der Konfigurationsinformationen verwendet wird. Wenn eine Anforderung für einen Mandanten empfangen wird, der sich nicht im Cache befindet, wird die Konfiguration geladen, bevor die Anforderung verarbeitet werden kann. Wenn der Cache voll ist, wird der zuletzt verwendete Mandant aus dem Cache entfernt.

Die zwischengespeicherte Version der Konfiguration wird in folgenden Situationen weiterhin verwendet (bis zum nächsten Mal, wenn der Server nach Updates sucht):

* Wenn eine Änderung in einer Konfigurationsdatei oder einer der Zertifikatdateien gespeichert wird, auf die in der Datei [!DNL flashaccess-tenant.xml] verwiesen wird, während der Server versucht, die Datei zu lesen
* Wenn der Zeitstempel der Datei vor der aktuellen Zeit weniger als eine Sekunde liegt
* Wenn der Zeitstempel der Datei in der Zukunft liegt

Wenn keine zwischengespeicherte Version vorhanden ist, schlägt das Laden der Konfiguration fehl und ein Fehler wird an den Client zurückgegeben. Der Server versucht dann, die Datei erneut zu laden, wenn er das nächste Mal eine Anforderung für diesen Mandanten erhält.

## Aktualisieren der globalen Konfigurationsdatei {#section_AA546C72442646CFB8906AEEBDF50587}

Sie können das HSM-Kennwort jederzeit in [!DNL flashaccess-global.xml] ändern. Die Änderungen werden beim nächsten Laden der Konfigurationsdatei durch den Server wirksam. Änderungen an den Elementen &quot;Protokollierung&quot;und &quot;Zwischenspeicherung&quot;werden jedoch nicht neu geladen. Sie müssen den Server neu starten, bevor Änderungen an diesen Elementen wirksam werden.

## Aktualisieren der Mandant-Konfigurationsdatei {#section_71624DB8DF28480F84F34F0FF7FD4365}

Sie können jederzeit alle Werte ändern, die in der Datei [!DNL flashaccess-tenant.xml] angegeben sind. Die Änderungen werden beim nächsten Laden der Konfigurationsdatei durch den Server wirksam. Der Server sucht außerdem nach allen Änderungen in allen Berechtigungsdateien ( [!DNL .pfx]) und Packager-Zulassungslisten-Zertifikatdateien, auf die in der Mietkonfigurationsdatei verwiesen wird.
