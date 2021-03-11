---
description: Der Berechtigungs-Manager ist der Feature Manager, der die Primetime-Authentifizierungsimplementierung unterstützt.
title: Übersicht über Berechtigungs-Manager
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Übersicht über den Berechtigungs-Manager {#entitlement-manager-overview}

Der Berechtigungs-Manager ist der Feature Manager, der die Primetime-Authentifizierungsimplementierung unterstützt.

## Übersicht über Funktionen

Durch die Integration der Primetime-Authentifizierung mit der Android Primetime SDK Reference Implementation wird der Anwendung ein neuer Feature Manager hinzugefügt. Im Gegensatz zu vielen anderen Funktionsmanagern wird der EntitlementManager jedoch an mehreren Stellen in der Anwendung verwendet. ** Im Folgenden werden die Änderungen und Ergänzungen erläutert, die an der Referenzimplementierung zur Unterstützung der Primetime-Authentifizierung vorgenommen wurden:

### EntitlementManager-Klasse

Die `EntitlementManager`-Klasse verarbeitet die gesamte Kommunikation mit dem Primetime-Authentifizierungs-SDK und kapselt die für die Workflows erforderliche Anwendungslogik. Die öffentliche API von `EntitlementManager` wird von der Anwendung zum Initiieren der Workflows verwendet, während die `EntitlementMangerListener`-Schnittstelle einen Rückrufmechanismus für die Verarbeitung von `EntitlementManger`-Ereignissen bereitstellt.

### EntilementManager-Rückrufe

Die Hauptinstanz der Referenzimplementierung, die `CatalogActivity`, erstellt eine Instanz von `EntitlementManagerListener` und registriert sie mit der `EntitlementManager`. Auf diese Weise signalisiert das `EntitlementManager` möglicherweise benötigte UI-Aktualisierungen für den Rest der Anwendung. Zu den Rückrufen gehören das Anzeigen/Ausblenden eines Dialogfelds zum Laden, das Anzeigen von Statusdialogfeldern, das Aktualisieren von Autorisierungs- und Authentifizierungssymbolen und das Starten der Videowiedergabe bei erfolgreicher Autorisierung.

### Berechtigungsdialoge

Die `EntitlementDialogFragment`-Klasse generiert Dialogfeldmeldungen basierend auf dem Berechtigungsstatus, der an den Klassenkonstruktor übergeben wird. Diese Klasse wird für Authentifizierungserfolgmeldungen sowie für alle Fehlermeldungen verwendet. Das `CatalogActivity` zeigt die Berechtigungsdialogfelder an, wenn es bestimmte Ereignis von dem `EntitlementManager` empfängt. Darüber hinaus implementiert das `CatalogActivity` die `EntitlementDialogListener`-Schnittstelle, die Rückrufmethoden enthält, die signalisieren, wenn ein Dialogfeld geschlossen wird oder wenn der Benutzer sich vom Primetime-Authentifizierungsdienst abmeldet.

### Auswahl und Anmeldung des Content Providers

Bei der Authentifizierung mit der Primetime-Authentifizierung können zwei neue Aktivitäten, `MvpdPickerActivity` und `MvpdLoginActivity`, dem Benutzer die Auswahl des Inhaltsanbieters und der Anmeldung ermöglichen. Beide Aktivitäten werden von `CatalogActivity` über `EntitlementManager` gestartet. Darüber hinaus müssen sowohl die Ergebnisse `MvpdPickerActivity` als auch `MvpdLoginActivity` an die `CatalogActivity`-Methode zurückgegeben werden, und deshalb muss die `CatalogActivity`-Methode die `Activity.onActivityResult`-Methode außer Kraft setzen.

### Schaltfläche &quot;Anmelden&quot;

Die wichtigste Aktivität der Referenzimplementierung, die `CatalogActivity`, enthält eine neue Schaltfläche &quot;Anmelden&quot;in der Aktionsleiste. Über die Schaltfläche &quot;Anmelden&quot;kann der Benutzer die Authentifizierung mit der Primetime-Authentifizierung starten. Darüber hinaus kann der Benutzer die Authentifizierung initiieren, indem er ein geschütztes Video zur Wiedergabe auswählt. Das Symbol und der Text der Schaltfläche &quot;Anmelden&quot;ändern sich je nach Authentifizierungsstatus des Benutzers und das `CatalogActivity` enthält Code, um das Symbol und den Text der Schaltfläche beim Aktualisieren der Seite zu aktualisieren. Zu diesem Zweck wird beim `CatalogActivity`-Beginn `EntitlementManager.checkAuthentication()` aufgerufen, um den Authentifizierungsstatus des Benutzers zu aktualisieren.

### Inhaltsberechtigung

Innerhalb von `CatalogView` werden über dem Inhaltssymbol neue Symbole angezeigt, um den Autorisierungsstatus des Benutzers für diesen Inhalt anzuzeigen. Wenn der Benutzer beispielsweise zur Ansicht eines Videos vorberechtigt ist, wird über dem Inhalt ein grünes Kreissymbol angezeigt. Wenn der Benutzer jedoch nicht zur Ansicht des Videos vorberechtigt ist, wird ein Schlüsselsymbol angezeigt. Die Anzeige dieser Symbole wird in `ContentTileAdapter` verarbeitet, jedoch wird die Aktualisierung ihres Status von `CatalogActivity` initiiert, wenn ein Rückruf in `EntitlementManagerListener` aufgerufen wird.

### Inhaltswiedergabe

Für die Videowiedergabe ist jetzt eine Autorisierungsüberprüfung durch das `EntitlementManager` erforderlich. Der Aufruf von `EntitlementManager.getAuthorization()` erfolgt innerhalb von `CatalogView`. Wenn für das Video eine Autorisierung erforderlich ist und der Benutzer autorisiert ist, wird `PlayerActivity` von `CatalogActivity` aus gestartet.

