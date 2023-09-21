---
title: Globale Konfigurationsdatei
description: Globale Konfigurationsdatei
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Globale Konfigurationsdatei{#global-configuration-file}

Die Konfigurationsdatei &quot;flashaccess-global.xml&quot;enthält Einstellungen, die für alle Mandanten des Lizenzservers gelten. Diese Datei muss sich unter *LicenseServer.ConfigRoot*. Eine globale Beispielkonfigurationsdatei finden Sie im Ordner &quot;configs&quot;. Die globale Konfigurationsdatei enthält Folgendes:

* Zwischenspeicherung - Steuert die Zwischenspeicherung von Konfigurationsdateien im Speicher. Eine Erläuterung der Cacheeinstellungen finden Sie unter &quot;Aktualisieren von Konfigurationsdateien&quot;.
* Protokollierung - Gibt die Protokollierungsstufe und die Häufigkeit des Rollierens von Protokolldateien an.
* HSM-Kennwort: Nur erforderlich, wenn HSM zum Speichern von Server-Anmeldeinformationen verwendet wird.

Siehe die Kommentare in der Beispiel-globalen Konfigurationsdatei unter `<AdobeAccessDVD>\Adobe Access Server for Protected Streaming\configs` für weitere Details.
