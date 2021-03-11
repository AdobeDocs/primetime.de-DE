---
title: Konfigurationsdateien des Lizenzservers
description: Konfigurationsdateien des Lizenzservers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Konfigurationsdateien des Lizenzservers{#license-server-configuration-files}

Für den Adobe Primetime DRM Server for Protected Streaming sind die folgenden Arten von Konfigurationsdateien erforderlich:

* Globale Konfigurationsdatei ( [!DNL flashaccess-global.xml])
* Mandantenkonfigurationsdatei für jeden Mandanten ( [!DNL flashaccess-tenant.xml])

Nachdem Sie die Konfigurationsdateien bearbeitet haben, empfiehlt Adobe, die mit dem Primetime-DRM-Server für geschütztes Streaming bereitgestellten Dienstprogramme zu verwenden, um sicherzustellen, dass die Dateien korrekt formatiert sind.

Siehe *Configuration Validator*.

Wenn Sie vermeiden möchten, dass Passwörter in unverschlüsselten Textteilen in den Konfigurationsdateien verfügbar gemacht werden, müssen Sie alle Passwörter, die Sie in den Konfigurationsdateien für Global und Pachting angegeben haben, mit dem von der Adobe bereitgestellten Scrambler-Tool verschlüsseln.

Weitere Informationen zum Verschlüsseln von Kennwörtern finden Sie unter *Password Scrambler*.
