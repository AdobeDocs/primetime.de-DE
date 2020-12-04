---
seo-title: Überblick über das Aktualisieren von Konfigurationsdateien
title: Überblick über das Aktualisieren von Konfigurationsdateien
uuid: e9be21cf-ad23-4ed6-8bef-f194bc1fd749
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---


# Übersicht über Konfigurationsdateien aktualisieren{#updating-configuration-files-overview}

Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers liest (globale Konfiguration oder Mandantenkonfiguration), werden die Konfigurationsinformationen im Arbeitsspeicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanforderung von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden. (Einzelheiten dazu, welche Konfigurationswerte auf Updates überprüft werden, finden Sie unten.)

Um die Konfiguration bei Änderungen neu zu laden, speichert der Lizenzserver den Zeitpunkt, zu dem die Datei zuletzt geändert wurde. In einem konfigurierbaren Intervall überprüft der Server, ob sich die Dateiänderungszeit geändert hat, und lädt dann den Inhalt der Datei neu.

Um zu steuern, wie oft der Server nach Updates sucht, legen Sie das `refreshDelaySeconds`-Attribut im Cache-Element der globalen Konfigurationsdatei fest. Wenn `refreshDelaySeconds` beispielsweise auf 3600 Sekunden eingestellt ist, dauert es höchstens eine Stunde nach der Aktualisierung der Datei, bis alle Konfigurationsaktualisierungen vom Server erkannt werden. Ist `refreshDelaySeconds` auf 0 gesetzt, sucht der Server bei jeder Anforderung nach Konfigurationsaktualisierungen. Die Einstellung von `refreshDelaySeconds` auf einen niedrigen Wert wird für Produktionsumgebungen nicht empfohlen, da dies die Umgebung beeinträchtigen könnte.

Das Caching-Element steuert auch, wie viele Mandantenkonfigurationen gleichzeitig zwischengespeichert werden. Sie können diesen Wert auf eine Zahl einstellen, die kleiner als die Gesamtanzahl der Mieter ist, um die Menge des Speichers zu begrenzen, der zum Zwischenspeichern der Konfigurationsinformationen verwendet wird. Wenn eine Anforderung für einen Mandanten nicht im Cache empfangen wird, wird die Konfiguration geladen, bevor die Anforderung verarbeitet werden kann. Wenn der Cache voll ist, wird der zuletzt verwendete Mandant aus dem Cache entfernt.

Wenn eine Änderung in einer Konfigurationsdatei oder in einer der Zertifikatdateien gespeichert wird, auf die in [!DNL flashaccess-tenant.xml] verwiesen wird, während der Server versucht, die Datei zu lesen, oder wenn der Zeitstempel der Datei weniger als eine Sekunde vor der aktuellen Zeit liegt oder sich in der Zukunft befindet, wird die zwischengespeicherte Version der Konfiguration verwendet, bis der Server das nächste Mal auf Updates überprüft. Wenn keine zwischengespeicherte Version vorhanden ist, schlägt das Laden der Konfiguration fehl und ein Fehler wird an den Client zurückgegeben. Der Server versucht, die Datei erneut zu laden, wenn er das nächste Mal eine Anforderung für diesen Mandanten erhält.
