---
title: Überblick über die Aktualisierung von Konfigurationsdateien
description: Überblick über die Aktualisierung von Konfigurationsdateien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Überblick über die Aktualisierung von Konfigurationsdateien {#updating-configuration-files-overview}

Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers (globale oder Mandantenkonfiguration) liest, werden die Konfigurationsinformationen im Speicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanfrage von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden. (Weitere Informationen dazu, welche Konfigurationswerte auf Updates überprüft werden, finden Sie unten.)

Um die Konfiguration bei Änderungen neu zu laden, speichert der Lizenzserver den Zeitpunkt der letzten Änderung der Datei. In einem konfigurierbaren Intervall überprüft der Server, ob sich die Dateiänderungszeit geändert hat, und lädt in diesem Fall den Inhalt der Datei neu.

Um zu steuern, wie oft der Server nach Aktualisierungen sucht, legen Sie die `refreshDelaySeconds` -Attribut im Caching-Element der globalen Konfigurationsdatei. Wenn beispielsweise `refreshDelaySeconds` auf 3600 Sekunden eingestellt ist, dauert es höchstens eine Stunde ab dem Zeitpunkt, zu dem die Datei aktualisiert wird, bis Konfigurationsaktualisierungen vom Server erkannt werden. Wenn `refreshDelaySeconds` auf 0 gesetzt ist, überprüft der Server bei jeder Anfrage auf Konfigurationsaktualisierungen. Einstellung `refreshDelaySeconds` für Produktionsumgebungen nicht empfohlen, da dies die Leistung beeinträchtigen könnte.

Das Caching-Element steuert auch, wie viele Mandantenkonfigurationen gleichzeitig zwischengespeichert werden. Sie können diesen Wert auf eine Zahl setzen, die kleiner ist als die Gesamtanzahl der Mandanten, um die zum Zwischenspeichern der Konfigurationsinformationen verwendete Speicherkapazität zu begrenzen. Wenn eine Anfrage für einen Mandanten empfangen wird, der sich nicht im Cache befindet, wird die Konfiguration geladen, bevor die Anfrage verarbeitet werden kann. Wenn der Cache voll ist, wird der zuletzt verwendete Mandant aus dem Cache entfernt.

Wenn eine Änderung in einer Konfigurationsdatei oder in einer der Zertifikatdateien gespeichert wird, auf die in [!DNL flashaccess-tenant.xml] während der Server versucht, die Datei zu lesen, oder wenn der Zeitstempel der Datei weniger als eine Sekunde vor der aktuellen Zeit liegt oder sich in der Zukunft befindet, wird die zwischengespeicherte Version der Konfiguration bis zum nächsten Mal verwendet, wenn der Server nach Updates sucht. Wenn keine zwischengespeicherte Version vorhanden ist, schlägt das Laden der Konfiguration fehl und ein Fehler wird an den Client zurückgegeben. Der Server versucht, die Datei erneut zu laden, wenn er das nächste Mal eine Anfrage für diesen Mandanten erhält.
