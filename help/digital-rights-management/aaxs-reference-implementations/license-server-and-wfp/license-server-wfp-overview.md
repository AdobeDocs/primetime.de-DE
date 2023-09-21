---
title: Lizenzserver und überwachter Ordner-Packager - Übersicht
description: Lizenzserver und überwachter Ordner-Packager - Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Lizenzserver und überwachter Ordner-Packager - Übersicht {#license-server-and-watched-folder-packager-overview}

Der Referenz-Implementierungsserver kann Ihnen beim Erstellen eines Lizenzservers mithilfe des Adobe Access SDK helfen. In dieser Implementierung werden Benutzer anhand von Benutzereinträgen in einer Datenbank authentifiziert. Der Server enthält eine geschäftliche Demonstrationslogik für die Lizenzerteilung. Außerdem wird Kompatibilitätsunterstützung für Flash Media Rights Management Server 1.0 und 1.5 implementiert.

Der Referenz-Implementierungsserver enthält auch eine Implementierung des Packager für überwachte Ordner. Diese Komponente kann zusammen mit dem Lizenzserver oder auf einem separaten Computer bereitgestellt werden. Mit dieser Paketimplementierung können mehrere überwachte Ordner erstellt werden. Wenn Inhalte in den überwachten Ordner abgelegt werden, packt der Packager den Inhalt automatisch.

Der Lizenzserver und der Packager werden als separate WAR-Dateien bereitgestellt, sodass Sie auswählen können, ob sie auf separaten Servern oder in einer einzelnen Apache Tomcat®-Instanz ausgeführt werden sollen. Der Lizenzserver befindet sich im [!DNL flashaccess.war] und sich der Packager in [!DNL flashaccess-packager.war]. Das optionale [!DNL edcws.war] unterstützt Lizenzanfragen von FMRMS 1.x-Clients.

Der Beispielcode für die Referenzimplementierung zeigt die folgenden Funktionen:

* Lizenzserver:

   * Umgang mit Authentifizierungsanfragen mithilfe einer Datenbank zur Validierung von Benutzername/Kennwort
   * Bearbeitung von Lizenzanfragen und Bestimmung des Lizenztyps, der bei Verwendung der Lizenzketten ausgestellt werden soll.
   * Erteilung von Lizenzen für Inhalte, die mehrere Richtlinien enthalten
   * Ausstellen von Lizenzen, die die Bereitstellung von Remote-Schlüssel für iOS-Clients unterstützen (Adobe Primetime erforderlich)
   * Erteilung von Lizenzen, die eine externe Suche/Abrufen des Inhaltsverschlüsselungsschlüssels (CEK) erfordern
   * Verwenden der Datenbank, um zu bestimmen, ob der Benutzer zum Anzeigen von Inhalten berechtigt ist
   * Verwenden von Listen zum Aktualisieren von Richtlinien
   * Verwenden von Maschinensperrlisten
   * Verwenden einer HSM- oder PKCS12-Datei zum Speichern von Anmeldeinformationen
   * In der Eigenschaftendatei angegebene Kennwörter verschlüsseln
   * Angabe mehrerer Lizenzserver- oder Transportberechtigungen (nach der Verlängerung der Anmeldedaten werden die alten Anmeldedaten auf dem Server beibehalten, damit der vorhandene Inhalt ohne erneute Verpackung wiederverwendet werden kann)
   * Einschränken von DRM-/Runtime-Versionen, die Anfragen an den Lizenzserver senden dürfen
   * Festlegen von Voreinstellungen für das Zurücksetzen der Client-Uhr
   * Beschränkung der zulässigen Zeitdifferenz zwischen Anforderungszeit und Serverzeit (um Wiederholungsangriffe zu vermeiden)
   * Umgang mit Anfragen von FMRMS 1.x-Clients (Trigger FMRMS 1.x-Client für die Aktualisierung auf Adobe Access 2.0 oder höher)
   * Konvertieren von FMRMS 1.x-Metadaten in Adobe-Metadaten ohne Zwischenschritte mithilfe von in einer Datenbank gespeicherten FMRMS 1.x-Lizenzinformationen
   * Beispielcode für die Konvertierung von FMRMS 1.x-Richtlinien in Adobe Access-Richtlinien
   * Beispielskripte zum Importieren von FMRMS 1.x-Lizenzinformationen aus einer vorhandenen Datenbank
   * Abrufen der Server-Version
   * Domänenregistrierung
   * Domain-Deregistrierung
   * Synchronisierungsanforderungen
   * Lizenzrückgabe

* Paketserver:

   * Implementieren einer Paketimplementierung, die Inhalt, der einem überwachten Ordner hinzugefügt wird, automatisch packt
   * Verwenden einer HSM- oder PKCS12-Datei zum Speichern von Anmeldeinformationen
   * In der Eigenschaftendatei angegebene Kennwörter verschlüsseln
   * Packager konfigurieren, Richtlinien erstellen und Listen mit Richtlinienaktualisierungen mithilfe einer AIR-Anwendung erstellen
