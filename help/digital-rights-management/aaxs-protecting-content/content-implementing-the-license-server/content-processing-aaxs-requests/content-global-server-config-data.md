---
title: Globale Server-Konfigurationsdaten
description: Globale Server-Konfigurationsdaten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Globale Server-Konfigurationsdaten{#global-server-configuration-data}

Zusätzlich zur Konfiguration, die vom Lizenzserver verwendet wird, `HandlerConfiguration` speichert Konfigurationsinformationen, die an den Client gesendet werden können, um zu steuern, wie Lizenzen durchgesetzt werden. Erstellen Sie dazu eine `ServerConfigData` -Klasse und Aufrufen `HandlerConfiguration.setServerConfigData()` (diese Einstellungen gelten nur für Lizenzen, die von diesem Lizenzserver ausgestellt werden). Die Uhrzeitwindback-Toleranz ist eine Eigenschaft, die vom Lizenzserver festgelegt werden kann, um zu steuern, wie der Client Lizenzen erzwingt. Standardmäßig können Benutzer ihre Maschinenuhr auf 4 Stunden zurücksetzen, ohne Lizenzen ungültig zu machen. Wenn ein Lizenzserver-Benutzer eine andere Einstellung verwenden möchte, kann der neue Wert im `ServerConfigData` -Klasse. Wenn Sie den Wert einer dieser Einstellungen ändern, müssen Sie die Versionsnummer erhöhen, indem Sie `setVersion()`. Die neuen Werte werden nur an den Client gesendet, wenn die Version auf dem Client unter der aktuellen Version liegt `ServerConfigData` -Version.
