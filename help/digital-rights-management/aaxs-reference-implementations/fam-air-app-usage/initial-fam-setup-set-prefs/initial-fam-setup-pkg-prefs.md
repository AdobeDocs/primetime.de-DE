---
seo-title: Packager-Voreinstellungen
title: Packager-Voreinstellungen
uuid: 3e9c971d-3a5f-4f3e-97e7-baab63b1f67f
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Packager-Voreinstellungen {#packager-preferences}

Diese Registerkarte enthält die zum Verpacken von Inhalten erforderlichen Einstellungen. In der folgenden Tabelle werden die folgenden Voreinstellungen beschrieben:

| Voreinstellung | Beschreibung |
|--- |--- |
| Transportzertifikat für Lizenzserver | Das von Adobe ausgestellte Servertransportzertifikat. Dieses Zertifikat dient zum Schützen der Kommunikation zwischen dem Client und dem Lizenzserver. Die Datei muss sich im Ressourcenverzeichnis befinden. |
| HSM aktivieren | Gibt an, ob Zertifikate und Berechtigungen auf einem HSM gespeichert werden. In diesem Fall werden Voreinstellungen für Zertifikate und Berechtigungen deaktiviert und die Eigenschaften auf der Registerkarte &quot;HSM&quot;müssen angegeben werden. |
| Schlüsselverschlüsselungsoptionen | Gibt an, wie der Inhaltsverschlüsselungsschlüssel zum Zeitpunkt der Verpackung verschlüsselt wird |
| Lizenzserverzertifikat | Das von Adobe ausgestellte License Server-Zertifikat. Die Datei muss sich im Ressourcenverzeichnis befinden. Der CEK wird mit dem öffentlichen Schlüssel des Lizenzservers verschlüsselt. Nur Inhaber des privaten Lizenzservers dürfen den CEK entschlüsseln. |
| Packager-Berechtigung | Die von Adobe ausgestellte Paketberechtigung. Diese Datei dient zum Unterschreiben der Metadaten während der Verpackung. |
| Dateiname | Die `PKCS#12` (.pfx)-Datei, die Zertifikat und privaten Schlüssel enthält. Die Datei muss sich im Ressourcenverzeichnis befinden. |
| Dateikennwort | Kennwort für die .pfx-Datei |
| Eigenschaften von globalen überwachten Ordnern | Gibt Einstellungen an, die allen auf diesem Server konfigurierten überwachten Ordnern gemein sind. |
| Prüfintervall in Millisekunden | Gibt an, wie oft überwachte Ordner nach neuen zu verpackenden Inhalten suchen sollen. Der Server durchläuft alle konfigurierten überwachten Ordner und schläft dann für diesen Zeitraum. |
| Suffix für Ausgabedateinamen | Gibt eine Dateierweiterung an, die den Ausgabedateien hinzugefügt werden soll. Wenn beispielsweise .out angegeben ist und die Eingabedatei video.flv lautet, lautet die Ausgabedatei video.out.flv. |
| Sicherungseingabedateien | Gibt an, ob eine Kopie des Originalinhalts gespeichert werden soll. Wenn diese Option nicht ausgewählt ist, wird die Originaldatei gelöscht, nachdem die Verpackung erfolgreich abgeschlossen wurde. |
| Unterordnername für Eingabesicherung | Wenn die Option &quot;Eingabedateien sichern&quot;aktiviert ist, wird ein Ordner angegeben, in dem Eingabedateien gespeichert werden. Diese Option gibt einen Ordnernamen relativ zum Eingabeordner des überwachten Ordners an. Wenn der Ordner nicht vorhanden ist, wird er während der Verpackung erstellt. |
| Vorhandene Ausgabedateien überschreiben | Gibt an, ob die Ausgabedatei überschrieben werden kann, wenn bereits eine Datei mit demselben Namen vorhanden ist. Wenn diese Option nicht aktiviert ist und die Ausgabedatei bereits vorhanden ist, wird die Verarbeitung der Eingabedatei übersprungen. |
