---
title: Konfigurationsdateien des Lizenzservers
description: Konfigurationsdateien des Lizenzservers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Konfigurationsdateien des Lizenzservers{#license-server-configuration-files}

Der Adobe Primetime DRM-Server für geschütztes Streaming erfordert die folgenden Arten von Konfigurationsdateien:

* Globale Konfigurationsdatei ( [!DNL flashaccess-global.xml])
* Mandantenkonfigurationsdatei für jeden Mandanten ( [!DNL flashaccess-tenant.xml])

Nach Abschluss der Bearbeitung der Konfigurationsdateien empfiehlt Adobe, die mit dem Primetime-DRM-Server bereitgestellten Dienstprogramme für geschütztes Streaming zu verwenden, um zu überprüfen, ob die Dateien korrekt formatiert sind.

Siehe *Konfigurationsvalidator*.

Wenn Sie vermeiden möchten, Passwörter in Klartext in den Konfigurationsdateien verfügbar zu machen, müssen Sie alle Passwörter verschlüsseln, die Sie in den globalen und Mandanten-Konfigurationsdateien angegeben haben, indem Sie das von Adobe bereitgestellte Scrambler-Tool verwenden.

Siehe *Password Scrambler* für weitere Informationen zum Verschlüsseln von Kennwörtern.
