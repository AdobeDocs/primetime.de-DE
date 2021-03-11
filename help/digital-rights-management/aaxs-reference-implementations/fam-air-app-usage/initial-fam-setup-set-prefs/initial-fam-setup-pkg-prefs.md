---
title: Packager-Voreinstellungen
description: Packager-Voreinstellungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Packager-Voreinstellungen {#packager-preferences}

Diese Registerkarte enthält die zum Verpacken von Inhalten erforderlichen Einstellungen. In der folgenden Tabelle werden die folgenden Voreinstellungen beschrieben:

| Voreinstellung | Beschreibung |
|--- |--- |
| Transportzertifikat für Lizenzserver | Das von der Adobe ausgestellte Servertransportzertifikat. Dieses Zertifikat dient zum Schützen der Kommunikation zwischen dem Client und dem Lizenzserver. Die Datei muss sich im Ressourcenverzeichnis befinden. |
| HSM aktivieren | Gibt an, ob Zertifikate und Berechtigungen auf einem HSM gespeichert werden. In diesem Fall werden Voreinstellungen für Zertifikate und Berechtigungen deaktiviert und die Eigenschaften auf der Registerkarte &quot;HSM&quot;müssen angegeben werden. |
| Schlüsselverschlüsselungsoptionen | Gibt an, wie der Inhaltsverschlüsselungsschlüssel zum Zeitpunkt der Verpackung verschlüsselt wird |
| Lizenzserverzertifikat | Das Lizenzserverzertifikat, ausgestellt von der Adobe. Die Datei muss sich im Ressourcenverzeichnis befinden. Der CEK wird mit dem öffentlichen Schlüssel des Lizenzservers verschlüsselt. Nur Inhaber des privaten Lizenzservers dürfen den CEK entschlüsseln. |
| Packager-Berechtigung | Die von der Adobe ausgestellte Paketberechtigung. Diese Datei dient zum Unterschreiben der Metadaten während der Verpackung. |
| Dateiname | Die `PKCS#12`-Datei (.pfx) mit Zertifikat und privatem Schlüssel. Die Datei muss sich im Ressourcenverzeichnis befinden. |
| Dateikennwort | Kennwort für die .pfx-Datei |
| Eigenschaften von globalen überwachten Ordnern | Gibt Einstellungen an, die allen auf diesem Server konfigurierten überwachten Ordnern gemein sind. |
| Prüfintervall in Millisekunden | Gibt an, wie oft überwachte Ordner nach neuen zu verpackenden Inhalten suchen sollen. Der Server durchläuft alle konfigurierten überwachten Ordner und schläft dann für diesen Zeitraum. |
| Suffix für Ausgabedateinamen | Gibt eine Dateierweiterung an, die den Ausgabedateien hinzugefügt werden soll. Wenn beispielsweise .out angegeben ist und die Eingabedatei video.flv lautet, lautet die Ausgabedatei video.out.flv. |
| Sicherungseingabedateien | Gibt an, ob eine Kopie des Originalinhalts gespeichert werden soll. Wenn diese Option nicht ausgewählt ist, wird die Originaldatei gelöscht, nachdem die Verpackung erfolgreich abgeschlossen wurde. |
| Unterordnername für Eingabesicherung | Wenn die Option &quot;Eingabedateien sichern&quot;aktiviert ist, wird ein Ordner angegeben, in dem Eingabedateien gespeichert werden. Diese Option gibt einen Ordnernamen relativ zum Eingabeordner des überwachten Ordners an. Wenn der Ordner nicht vorhanden ist, wird er während der Verpackung erstellt. |
| Vorhandene Ausgabedateien überschreiben | Gibt an, ob die Ausgabedatei überschrieben werden kann, wenn bereits eine Datei mit demselben Namen vorhanden ist. Wenn diese Option nicht aktiviert ist und die Ausgabedatei bereits vorhanden ist, wird die Verarbeitung der Eingabedatei übersprungen. |
