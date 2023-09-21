---
title: Grundlegende Richtlinienoptionen
description: Grundlegende Richtlinienoptionen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Grundlegende Richtlinienoptionen {#basic-policy-options}

In der folgenden Tabelle werden die Grundeinstellungen für Richtlinien beschrieben:

| Präferenz | Beschreibung |
|---|---|
| Richtliniendauer | Gibt die Gültigkeitsdauer des mit dieser Richtlinie geschützten Inhalts an. |
|  | Beginnen bei | Lizenzen können bis zu diesem Datum/zu dieser Uhrzeit nicht verwendet werden. |
|  | Ende bei | Lizenzen können nach diesem Datum/dieser Uhrzeit nicht mehr verwendet werden. |
|  | Ende nach | Gibt die Gültigkeitsdauer einer Lizenz (in Minuten) an, beginnend mit dem Zeitpunkt des Pakets. |
| Lizenzzwischenspeicherung | Gibt an, ob Lizenzen vom Client zwischengespeichert werden können. |
|  | | Lizenzen können nach diesem Datum/dieser Uhrzeit nicht mehr verwendet werden. |
|  | Löschen nach | Gibt die Gültigkeitsdauer einer Lizenz (in Minuten) an, beginnend mit dem Zeitpunkt der Lizenzerteilung durch den Lizenzserver. |
|  | Unbegrenzt zwischenspeichern | Die Lizenz kann auf unbestimmte Zeit auf dem Client zwischengespeichert werden. |
|  | Keine Lizenzzwischenspeicherung | Die Lizenz kann vom Client nicht zwischengespeichert werden. Jede Wiedergabe des Inhalts durch den Benutzer muss eine neue Lizenz vom Server erhalten. |
| Authentifizierung | |
|  | Anonym | Zum Anzeigen des Inhalts ist keine Authentifizierung erforderlich. |
|  | Authentifiziert | Authentifizierung mit Benutzername/Kennwort ist erforderlich. |
| Lizenzketten aktivieren | Ermöglicht die Aktualisierung einer Lizenz mit einer übergeordneten Stammlizenz für die Batch-Aktualisierung von Lizenzen. Sobald die Laublizenz abläuft, kann der Server dem Client eine Root-Lizenz erteilen, mit der alle mit dieser Richtlinie geschützten Inhalte erneuert werden. |
