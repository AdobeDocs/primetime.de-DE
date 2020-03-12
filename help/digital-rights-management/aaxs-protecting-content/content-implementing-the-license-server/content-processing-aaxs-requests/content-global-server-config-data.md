---
seo-title: Globale Serverkonfigurationsdaten
title: Globale Serverkonfigurationsdaten
uuid: f6d6cb01-2645-4cd2-83ec-0272323a67cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Globale Serverkonfigurationsdaten{#global-server-configuration-data}

Neben der vom Lizenzserver verwendeten Konfiguration werden `HandlerConfiguration` Konfigurationsinformationen gespeichert, die an den Client gesendet werden können, um zu steuern, wie Lizenzen erzwungen werden. Dies geschieht durch Erstellen einer `ServerConfigData` Klasse und Aufrufen `HandlerConfiguration.setServerConfigData()` (diese Einstellungen gelten nur für Lizenzen, die von diesem Lizenzserver erteilt werden). Die Uhrzeitrückhaltetoleranz ist eine Eigenschaft, die vom Lizenzserver festgelegt werden kann, um zu steuern, wie der Client Lizenzen durchsetzt. Standardmäßig können Benutzer ihre Computeruhr auf 4 Stunden einstellen, ohne Lizenzen zu ungültigen. Wenn ein Lizenzserveroperator eine andere Einstellung verwenden möchte, kann der neue Wert in der `ServerConfigData` Klasse festgelegt werden. Wenn Sie den Wert einer dieser Einstellungen ändern, stellen Sie sicher, dass Sie die Versionsnummer durch Aufruf erhöhen `setVersion()`. Die neuen Werte werden nur dann an den Client gesendet, wenn die Version auf dem Client unter der aktuellen `ServerConfigData` Version liegt.
