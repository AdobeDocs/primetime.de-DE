---
seo-title: Konfigurationsdateien des Lizenzservers
title: Konfigurationsdateien des Lizenzservers
uuid: 7c7e0f76-2ced-45af-9542-99e06ec31cda
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Konfigurationsdateien des Lizenzservers{#license-server-configuration-files}

Für den Adobe Primetime DRM Server for Protected Streaming sind die folgenden Arten von Konfigurationsdateien erforderlich:

* Globale Konfigurationsdatei ( [!DNL flashaccess-global.xml])
* Mandantenkonfigurationsdatei für jeden Mandanten ( [!DNL flashaccess-tenant.xml])

Nachdem Sie die Konfigurationsdateien bearbeitet haben, empfiehlt Adobe, die mit dem Primetime-DRM-Server für geschütztes Streaming bereitgestellten Dienstprogramme zu verwenden, um sicherzustellen, dass die Dateien korrekt formatiert sind.

Siehe *Configuration Validator*.

Wenn Sie verhindern möchten, dass Passwörter in unverschlüsseltem Text in den Konfigurationsdateien verfügbar gemacht werden, müssen Sie alle Passwörter, die Sie in den Konfigurationsdateien für globale und Mandanten angegeben haben, mit dem von Adobe bereitgestellten Scrambler-Tool verschlüsseln.

Weitere Informationen zum Verschlüsseln von Passwörtern finden Sie unter *Password Scrambler* .
