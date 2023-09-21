---
title: Aktualisieren der globalen Konfigurationsdatei
description: Aktualisieren der globalen Konfigurationsdatei
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---

# Aktualisieren der globalen Konfigurationsdatei{#updating-the-global-configuration-file}

Das HSM-Kennwort in [!DNL flashaccess-global.xml] kann jederzeit geändert werden. Die Änderungen werden wirksam, wenn der Server das nächste Mal die Konfigurationsdatei neu lädt. Änderungen an den Elementen &quot;Protokollierung&quot;und &quot;Zwischenspeicherung&quot;werden jedoch nicht neu geladen. Änderungen an diesen Elementen erfordern einen Neustart des Servers.
