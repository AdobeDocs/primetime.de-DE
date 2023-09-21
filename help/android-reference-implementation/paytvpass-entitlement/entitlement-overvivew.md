---
description: Der Berechtigungs-Manager ist der Feature Manager, der die Primetime-Authentifizierungsimplementierung unterstützt.
title: Übersicht über Entitäts-Manager
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Übersicht über Entitäts-Manager {#entitlement-manager-overview}

Der Berechtigungs-Manager ist der Feature Manager, der die Primetime-Authentifizierungsimplementierung unterstützt.

## Funktionsübersicht

Durch die Integration der Primetime-Authentifizierung mit der Referenzimplementierung des Android Primetime SDK wird der Anwendung ein neuer Feature Manager hinzugefügt. Im Gegensatz zu vielen anderen Feature-Managern gilt Folgendes: *Der EntitlementManager wird in der Anwendung an mehreren Stellen verwendet.*. Im Folgenden finden Sie einen Überblick über die Änderungen und Ergänzungen der Referenzimplementierung zur Unterstützung der Primetime-Authentifizierung:

### EntitlementManager-Klasse

Die `EntitlementManager` -Klasse verarbeitet die gesamte Kommunikation mit dem Primetime-Authentifizierungs-SDK und kapselt die für die Berechtigungs-Workflows erforderliche Anwendungslogik. Die `EntitlementManager`Die öffentliche API der Anwendung wird verwendet, um Berechtigungs-Workflows zu initiieren, während die `EntitlementMangerListener` -Schnittstelle bietet einen Callback-Mechanismus, der von der Anwendung verarbeitet werden kann `EntitlementManger` -Ereignisse.

### Callbacks von EntitlementManger

Die Hauptaktivität der Referenzimplementierung, die `CatalogActivity`erstellt eine Instanz von `EntitlementManagerListener` und registriert sie bei der `EntitlementManager`. Auf diese Weise wird die `EntitlementManager` weist möglicherweise auf erforderliche UI-Aktualisierungen für den Rest der Anwendung hin. Zu den Rückrufen gehören das Anzeigen/Ausblenden eines Ladedialogfelds, das Anzeigen von Statusdialogfeldern, das Aktualisieren von Autorisierungs- und Authentifizierungssymbolen und das Starten der Videowiedergabe bei erfolgreicher Autorisierung.

### Berechtigungsdialogfelder

Die `EntitlementDialogFragment` -Klasse generiert Dialogfeldmeldungen basierend auf dem an den Klassenkonstruktor übergebenen Berechtigungsstatus. Diese Klasse wird für Authentifizierungs-Erfolgsnachrichten sowie für alle Fehlermeldungen verwendet. Die `CatalogActivity` zeigt die Berechtigungsdialogfelder an, wenn sie bestimmte Ereignisse von der `EntitlementManager`. Darüber hinaus wird die `CatalogActivity` implementiert die `EntitlementDialogListener` -Schnittstelle, die Callback-Methoden enthält, um zu signalisieren, wann ein Dialogfeld geschlossen wird oder ob sich der Benutzer beim Primetime-Authentifizierungsdienst abmeldet.

### Auswahl und Anmeldung des Content Providers

Bei der Authentifizierung mit der Primetime-Authentifizierung werden zwei neue Aktivitäten gestartet: `MvpdPickerActivity` und `MvpdLoginActivity`, erlauben Sie dem Benutzer, seinen Inhaltsanbieter auszuwählen und sich anzumelden. Beide Aktivitäten werden ausgehend von der `CatalogActivity` über die `EntitlementManager`. Darüber hinaus wird bei beiden `MvpdPickerActivity` und `MvpdLoginActivity` die Ergebnisse an `CatalogActivity` und damit die `CatalogActivity` muss die `Activity.onActivityResult` -Methode.

### Schaltfläche &quot;Anmelden&quot;

Die Hauptaktivität der Referenzimplementierung, die `CatalogActivity`enthält eine neue &quot;Anmelden&quot;-Schaltfläche in der Symbolleiste. Über die Schaltfläche Anmelden kann der Benutzer die Authentifizierung mit der Primetime-Authentifizierung starten. Darüber hinaus kann der Benutzer die Authentifizierung initiieren, indem er ein geschütztes Video für die Wiedergabe auswählt. Das Symbol und der Text der Schaltfläche Anmelden ändern sich je nach Authentifizierungsstatus des Benutzers und dem `CatalogActivity` enthält Code, um das Symbol und den Text der Schaltfläche beim Aktualisieren der Seite zu aktualisieren. Zu diesem Zweck muss die Variable `CatalogActivity` starts, it aufrufen `EntitlementManager.checkAuthentication()` , um den Authentifizierungsstatus des Benutzers zu aktualisieren.

### Inhaltsberechtigungen

Innerhalb der `CatalogView`werden am oberen Rand des Inhaltssymbols neue Symbole angezeigt, um den Autorisierungsstatus des Benutzers für diesen Inhalt zu signalisieren. Wenn der Benutzer beispielsweise zur Ansicht eines Videos vorberechtigt ist, wird über dem Inhalt ein grünes Kreissymbol angezeigt. Wenn der Benutzer jedoch nicht zur Ansicht des Videos vorberechtigt ist, wird ein Schlüsselsymbol angezeigt. Die Anzeige dieser Symbole wird in `ContentTileAdapter`, jedoch wird die Aktualisierung ihres Status von der `CatalogActivity` wenn ein Rückruf in der Variablen `EntitlementManagerListener` aufgerufen wird.

### Inhaltswiedergabe

Für die Videowiedergabe ist jetzt eine Autorisierungsprüfung durch die `EntitlementManager`. Der Aufruf an `EntitlementManager.getAuthorization()` innerhalb von `CatalogView`. Wenn für das Video eine Autorisierung erforderlich ist und der Benutzer autorisiert ist, wird die `PlayerActivity` wird über die `CatalogActivity`.
