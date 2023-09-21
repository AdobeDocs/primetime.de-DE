---
description: Die Konfigurationsdatei "flashaccess-global.xml"enthält Einstellungen, die für alle Mandanten des Lizenzservers gelten.
title: Globale Konfigurationsdatei
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Globale Konfigurationsdatei{#global-configuration-file}

Die Konfigurationsdatei &quot;flashaccess-global.xml&quot;enthält Einstellungen, die für alle Mandanten des Lizenzservers gelten.

Sie müssen die Konfigurationsdatei im [!DNL LicenseServer.ConfigRoot] Verzeichnis.

Siehe [!DNL configs] -Verzeichnis für ein Beispiel einer globalen Konfigurationsdatei.

Die globale Konfigurationsdatei enthält:

* Zwischenspeicherung - Steuert die Zwischenspeicherung von Konfigurationsdateien im Speicher.

  Siehe *Aktualisieren von Konfigurationsdateien* für Informationen zu den Cacheeinstellungen.
* Protokollierung - Gibt die Protokollierungsstufe und die Häufigkeit des Rollierens von Protokolldateien an.
* HSM-Kennwort: Nur erforderlich, wenn HSM zum Speichern von Server-Anmeldeinformationen verwendet wird.

Siehe Kommentare in der Beispiel-globalen Konfigurationsdatei, die sich in Primetime DRM befindet. `<DVD>`\Adobe Primetime DRM Server für geschütztes Streaming\Konfigurationen für weitere Informationen.
