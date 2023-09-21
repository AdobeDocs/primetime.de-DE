---
title: Paketeinstellungen
description: Paketeinstellungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Paketeinstellungen {#packager-preferences}

Dieser Tab enthält die zum Verpacken von Inhalten erforderlichen Einstellungen. In der folgenden Tabelle werden diese Voreinstellungen beschrieben:

| Präferenz | Beschreibung |
|--- |--- |
| Lizenzserver-Transportzertifikat | Das vom Adobe ausgestellte Server-Transportzertifikat. Dieses Zertifikat dient zur Sicherung der Kommunikation zwischen dem Client und dem Lizenzserver. Die Datei muss sich im Ressourcenverzeichnis befinden. |
| HSM aktivieren | Gibt an, ob Zertifikate und Berechtigungen auf einem HSM gespeichert werden. Ist dies der Fall, werden die Voreinstellungen für Zertifikate und Berechtigungen deaktiviert und die Eigenschaften auf der HSM-Registerkarte müssen angegeben werden. |
| Schlüsselverschlüsselungsoptionen | Gibt an, wie der Inhaltsverschlüsselungsschlüssel beim Verpacken verschlüsselt wird |
| Lizenzserver-Zertifikat | Lizenzserver-Zertifikat, ausgestellt von Adobe. Die Datei muss sich im Ressourcenverzeichnis befinden. Der CEK wird mit dem öffentlichen Schlüssel des Lizenzservers verschlüsselt. Nur Inhaber des privaten Lizenzservers dürfen den CEK entschlüsseln. |
| Packager Credential | Die von Adobe ausgestellte Paketberechtigung. Diese Datei wird verwendet, um die Metadaten während der Verpackung zu signieren. |
| Dateiname | Die `PKCS#12` ( .pfx)-Datei mit Zertifikat und privatem Schlüssel. Die Datei muss sich im Ressourcenverzeichnis befinden. |
| File Password | Kennwort für .pfx-Datei |
| Eigenschaften für globale überwachte Ordner | Gibt Einstellungen an, die für alle auf diesem Server konfigurierten überwachten Ordner gelten. |
| Prüfung des Intervalls in Millisekunden | Gibt an, wie oft überwachte Ordner nach neuen Inhalten für das Paket suchen sollen. Der Server durchläuft alle konfigurierten überwachten Ordner und schläft dann für diesen Zeitraum. |
| Suffix für Ausgabedateinamen | Gibt eine Dateierweiterung zum Hinzufügen zu Ausgabedateien an. Wenn beispielsweise .out angegeben ist und die Eingabedatei video.flv lautet, lautet die Ausgabedatei video.out.flv. |
| Backup-Eingabedateien | Gibt an, ob eine Kopie des Originalinhalts gespeichert werden soll. Wenn diese Option nicht aktiviert ist, wird die Originaldatei nach erfolgreichem Abschluss der Verpackung gelöscht. |
| Name des Unterordners für die Eingabesicherung | Wenn die Option &quot;Backup Input Files&quot;ausgewählt ist, gibt einen Ordner an, in dem Eingabedateien gespeichert werden. Diese Option gibt einen Ordnernamen an, der relativ zum Eingabeordner des überwachten Ordners ist. Wenn der Ordner nicht vorhanden ist, wird er während der Verpackung erstellt. |
| Vorhandene Ausgabedateien überschreiben | Gibt an, ob die Ausgabedatei überschrieben werden kann, wenn bereits eine Datei mit demselben Namen vorhanden ist. Wenn diese Option nicht aktiviert ist und die Ausgabedatei bereits existiert, wird die Verarbeitung der Eingabedatei übersprungen. |
