---
title: Globale Serverkonfigurationsdaten
description: Globale Serverkonfigurationsdaten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# Globale Serverkonfigurationsdaten{#global-server-configuration-data}

Zusätzlich zur vom Lizenzserver verwendeten Konfiguration speichert `HandlerConfiguration` Konfigurationsinformationen, die an den Client gesendet werden können, um zu steuern, wie Lizenzen erzwungen werden. Dies geschieht durch Erstellen einer `ServerConfigData`-Klasse und Aufrufen von `HandlerConfiguration.setServerConfigData()` (diese Einstellungen gelten nur für Lizenzen, die von diesem Lizenzserver erteilt werden). Die Uhrzeitrückhaltetoleranz ist eine Eigenschaft, die vom Lizenzserver festgelegt werden kann, um zu steuern, wie der Client Lizenzen durchsetzt. Standardmäßig können Benutzer ihre Computeruhr auf 4 Stunden einstellen, ohne Lizenzen zu ungültigen. Wenn ein Lizenzserveroperator eine andere Einstellung verwenden möchte, kann der neue Wert in der Klasse `ServerConfigData` festgelegt werden. Wenn Sie den Wert einer dieser Einstellungen ändern, stellen Sie sicher, dass Sie die Versionsnummer inkrementieren, indem Sie `setVersion()` aufrufen. Die neuen Werte werden nur dann an den Client gesendet, wenn die Version auf dem Client unter der aktuellen `ServerConfigData`-Version liegt.
