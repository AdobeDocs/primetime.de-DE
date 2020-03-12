---
description: Der Berechtigungs-Manager ist der Feature Manager, der die Primetime-Authentifizierungsimplementierung unterstützt.
seo-description: Der Berechtigungs-Manager ist der Feature Manager, der die Primetime-Authentifizierungsimplementierung unterstützt.
seo-title: Übersicht über Berechtigungs-Manager
title: Übersicht über Berechtigungs-Manager
uuid: b33dfae3-a132-4215-9992-80cbf4c87a61
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Übersicht über Berechtigungs-Manager {#entitlement-manager-overview}

Der Berechtigungs-Manager ist der Feature Manager, der die Primetime-Authentifizierungsimplementierung unterstützt.

## Übersicht über Funktionen

Durch die Integration der Primetime-Authentifizierung mit der Android Primetime SDK Reference Implementation wird der Anwendung ein neuer Feature Manager hinzugefügt. Im Gegensatz zu vielen anderen Funktionsmanagern wird *der EntitlementManager jedoch an verschiedenen Stellen in der Anwendung* verwendet. Im Folgenden werden die Änderungen und Ergänzungen erläutert, die an der Referenzimplementierung zur Unterstützung der Primetime-Authentifizierung vorgenommen wurden:

### EntitlementManager-Klasse

Die `EntitlementManager` Klasse verarbeitet die gesamte Kommunikation mit dem Primetime-Authentifizierungs-SDK und kapselt die für die Workflows erforderliche Anwendungslogik. Die öffentliche API `EntitlementManager`wird von der Anwendung zum Initiieren der Workflows verwendet, während die `EntitlementMangerListener` Oberfläche einen Rückrufmechanismus für die Verarbeitung von `EntitlementManger` Ereignissen bereitstellt.

### EntilementManager-Rückrufe

Die wichtigste Aktivität der Referenzimplementierung, die `CatalogActivity`, erstellt eine Instanz von `EntitlementManagerListener` und registriert sie bei der `EntitlementManager`. Auf diese Weise signalisiert `EntitlementManager` das Signal ggf. erforderliche UI-Aktualisierungen für den Rest der Anwendung. Zu den Rückrufen gehören das Anzeigen/Ausblenden eines Dialogfelds zum Laden, das Anzeigen von Statusdialogfeldern, das Aktualisieren von Autorisierungs- und Authentifizierungssymbolen und das Starten der Videowiedergabe bei erfolgreicher Autorisierung.

### Berechtigungsdialoge

Die `EntitlementDialogFragment` Klasse generiert Dialogfeldmeldungen basierend auf dem Berechtigungsstatus, der an den Klassenkonstruktor übergeben wird. Diese Klasse wird für Authentifizierungserfolgmeldungen sowie für alle Fehlermeldungen verwendet. Das `CatalogActivity` zeigt die Berechtigungsdialogfelder an, wenn es bestimmte Ereignis von der `EntitlementManager`. Darüber hinaus `CatalogActivity` implementiert das System die `EntitlementDialogListener` Schnittstelle, die Rückrufmethoden enthält, die signalisieren, wenn ein Dialogfeld geschlossen wird oder wenn sich der Benutzer beim Primetime-Authentifizierungsdienst abmeldet.

### Auswahl und Anmeldung des Content Providers

Bei der Authentifizierung mit der Primetime-Authentifizierung können zwei neue Aktivitäten verwendet werden `MvpdPickerActivity` und `MvpdLoginActivity`der Benutzer den Inhaltsanbieter auswählen und sich anmelden. Beide Aktivitäten werden von der `CatalogActivity` über die `EntitlementManager`. Darüber hinaus müssen sowohl die `MvpdPickerActivity` und `MvpdLoginActivity` Rückgabeergebnisse an die `CatalogActivity` und damit die `CatalogActivity` Methode die `Activity.onActivityResult` Methode überschreiben.

### Schaltfläche &quot;Anmelden&quot;

Die wichtigste Aktivität der Referenzimplementierung, die `CatalogActivity`, enthält eine neue &quot;Anmelde&quot;-Schaltfläche in der Aktionsleiste. Über die Schaltfläche &quot;Anmelden&quot;kann der Benutzer die Authentifizierung mit der Primetime-Authentifizierung starten. Darüber hinaus kann der Benutzer die Authentifizierung initiieren, indem er ein geschütztes Video zur Wiedergabe auswählt. Das Symbol und der Text der Schaltfläche &quot;Anmelden&quot;ändern sich je nach Authentifizierungsstatus des Benutzers und `CatalogActivity` enthalten Code zum Aktualisieren des Symbols und des Textes der Schaltfläche beim Aktualisieren der Seite. Dazu müssen die `CatalogActivity` Beginn den Authentifizierungsstatus des Benutzers aktualisieren, `EntitlementManager.checkAuthentication()` wenn sie dies tun.

### Inhaltsberechtigung

Innerhalb der `CatalogView`werden neue Symbole über dem Inhaltssymbol angezeigt, um den Autorisierungsstatus des Benutzers für diesen Inhalt anzuzeigen. Wenn der Benutzer beispielsweise zur Ansicht eines Videos vorberechtigt ist, wird über dem Inhalt ein grünes Kreissymbol angezeigt. Wenn der Benutzer jedoch nicht zur Ansicht des Videos vorberechtigt ist, wird ein Schlüsselsymbol angezeigt. Die Anzeige dieser Symbole wird in `ContentTileAdapter`der Anwendung verarbeitet, jedoch wird die Aktualisierung ihres Status von der `CatalogActivity` , wenn ein Rückruf im `EntitlementManagerListener` Aufruf erfolgt, aus initiiert.

### Inhaltswiedergabe

Für die Videowiedergabe ist jetzt eine Autorisierungsüberprüfung durch das `EntitlementManager`erforderlich. Der Aufruf zu `EntitlementManager.getAuthorization()` erfolgt innerhalb von `CatalogView`. Wenn für das Video eine Autorisierung erforderlich ist und der Benutzer autorisiert ist, `PlayerActivity` wird das Video vom `CatalogActivity`.

