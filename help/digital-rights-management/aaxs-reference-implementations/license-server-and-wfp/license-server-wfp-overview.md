---
title: Überblick über den Lizenzserver und den überwachten Ordner-Packager
description: Überblick über den Lizenzserver und den überwachten Ordner-Packager
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---


# Überblick über den Lizenzserver und den überwachten Ordner-Packager {#license-server-and-watched-folder-packager-overview}

Der Referenz-Implementierungsserver kann Ihnen beim Erstellen eines Lizenzservers mit dem Adobe Access SDK helfen. Bei dieser Implementierung werden Benutzer anhand von Benutzereinträgen in einer Datenbank authentifiziert. Der Server enthält eine Geschäftslogik für die Lizenzerteilung. Es implementiert außerdem Kompatibilitätsunterstützung für Flash Media Rights Management Server 1.0 und 1.5.

Der Referenz-Implementierungsserver enthält auch eine Implementierung des Pakets für überwachte Ordner. Diese Komponente kann zusammen mit dem Lizenzserver oder auf einem separaten Computer bereitgestellt werden. Mit dieser Paketimplementierung können mehrere überwachte Ordner erstellt werden. Wenn Inhalte in den überwachten Ordner abgelegt werden, verpackt der Packager den Inhalt automatisch.

Der Lizenzserver und der Packager werden als separate WAR-Dateien bereitgestellt, sodass Sie auswählen können, ob diese auf separaten Servern oder in einer einzigen Apache Tomcat®-Instanz ausgeführt werden sollen. Der Lizenzserver befindet sich im Ordner [!DNL flashaccess.war] und der Packager befindet sich im Ordner [!DNL flashaccess-packager.war]. Das optionale [!DNL edcws.war] enthält Unterstützung für Lizenzanforderungen von FMRMS 1.x-Clients.

Der Beispielcode für die Referenzimplementierung zeigt die folgenden Funktionen:

* Lizenzserver:

   * Verarbeiten von Authentifizierungsanforderungen mit einer Datenbank zur Überprüfung von Benutzername/Kennwort
   * Bearbeitung von Lizenzanfragen und Bestimmung des Lizenztyps, der bei Verwendung der Lizenzverkettung erteilt werden soll.
   * Erteilung von Lizenzen für Inhalte mit mehreren Richtlinien
   * Ausgabenlizenzen, die Remote Key Versand für iOS-Clients unterstützen (Adobe Primetime erforderlich)
   * Erteilung von Lizenzen, für die eine externe Suche/Abfrage des Content Encryption Key (CEK) erforderlich ist
   * Datenbank verwenden, um zu ermitteln, ob der Benutzer zur Ansicht von Inhalten berechtigt ist
   * Listen zur Richtlinienaktualisierung verwenden
   * Verwenden von Listen zum Zurücknehmen des Computers
   * Verwenden einer HSM- oder PKCS12-Datei zum Speichern von Berechtigungen
   * Verschlüsseln von in der Eigenschaftendatei angegebenen Kennwörtern
   * Angabe mehrerer Lizenzserver- oder Transportberechtigungen (nach der Erneuerung der Anmeldeinformationen werden die alten Anmeldeinformationen auf dem Server gespeichert, damit vorhandene Inhalte ohne erneute Verpackung verbraucht werden können)
   * Einschränkung von DRM-/Laufzeitversionen, die Anforderungen an den Lizenzserver stellen dürfen
   * Voreinstellungen für die Zeitrücklaufzeit des Clients festlegen
   * Einschränkung der zulässigen Zeitdifferenz zwischen Anforderungszeit und Serverzeit (um Wiederholungsangriffe zu vermeiden)
   * Bearbeitung von Anfragen von FMRMS 1.x-Clients (Trigger FMRMS 1.x-Client für Aktualisierung auf Adobe Access 2.0 oder höher)
   * Konvertieren von FMRMS 1.x-Metadaten in Adobe Access-Metadaten mithilfe von in einer Datenbank gespeicherten FMRMS 1.x-Lizenzinformationen
   * Beispielcode für die Konvertierung von FMRMS 1.x-Richtlinien in Adobe Access-Richtlinien
   * Beispielskripte zum Importieren von FMRMS 1.x-Lizenzinformationen aus einer vorhandenen Datenbank
   * Serverversion abrufen
   * Domänenregistrierung
   * Domänenderegistrierung
   * Synchronisierungsanfragen
   * Lizenzrückgabe

* Packager Server:

   * Implementieren einer Packager-Implementierung, die Inhalte, die einem überwachten Ordner hinzugefügt werden, automatisch verpackt
   * Verwenden einer HSM- oder PKCS12-Datei zum Speichern von Berechtigungen
   * Verschlüsseln von in der Eigenschaftendatei angegebenen Kennwörtern
   * Konfigurieren des Packager, Erstellen von Richtlinien und Erstellen von Listen zur Richtlinienaktualisierung mit einer AIR-Anwendung

