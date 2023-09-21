---
title: Rechte abspielen
description: Rechte abspielen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Rechte abspielen {#play-rights}

In der folgenden Tabelle werden die Voreinstellungen für Play Rights beschrieben:

| Präferenz | Beschreibung |
|--- |--- |
| Wiedergabefenster | Die Gültigkeitsdauer einer Lizenz (in Minuten) nach der ersten Wiedergabe des geschützten Inhalts durch den Benutzer. |
| Output Protection | Steuert, ob die Ausgabe auf externe Rendering-Geräte geschützt werden soll. Analog- und digitale Ausgaben können unabhängig angegeben werden. |
| Einschränkungen | Blockierungsliste von Clientversionen, die keine Inhalte wiedergeben dürfen. Alle Spalten sind optional. |
| DRM | Gibt eine Liste der DRM-Versionen an, die keine geschützten Inhalte wiedergeben dürfen. |
| Laufzeit | Gibt eine Liste der Laufzeitversionen an, die keine geschützten Inhalte wiedergeben dürfen. |
| Mindestsicherheitsstufe |  |
| DRM | Minimale DRM-Sicherheitsstufe, die erforderlich ist, um geschützte Inhalte wiederzugeben. |
| Laufzeit | Mindestens erforderliche Runtime-Sicherheitsstufe, um geschützte Inhalte wiederzugeben. |
| Zulässige Anwendungen | Zulassungsliste der Clientanwendungen, die Inhalte abspielen dürfen. Wenn keine Anwendungen angegeben sind, ist jede SWF- oder AIR-Anwendung zulässig. |
| SWF | Liste der SWF-URLs, die geschützte Inhalte abspielen dürfen. |
| AIR | Liste der AIR-Anwendungen, die geschützte Inhalte abspielen dürfen. Die Herausgeber-ID ist erforderlich, die übrigen Felder sind optional. |

Flash Access Manager unterstützt Richtlinien mit mehreren Wiedergabeberechtigungen. Um eine Richtlinie mit mehr als einer Play Right-Option zu erstellen, verwenden Sie die Schaltfläche &quot;Add additional Play Right&quot;(Zusätzliche Wiedergabequalität hinzufügen) und füllen Sie die gewünschten Attribute für jede Play Right-Option aus.

Bei der Nutzung einer Lizenz verwendet der Client das erste Play Right, für das er alle Anforderungen erfüllt. Es können mehrere Wiedergaberechte verwendet werden, um verschiedene Einschränkungen für verschiedene Betriebssysteme anzugeben. Beispielsweise ist es möglich, eine Berechtigung mit für Windows erforderlichem Output Protection anzugeben (indem DRM-Versionen unter Macintosh und Linux auf die Blockierungsliste gesetzt werden) und eine zweite Berechtigung mit Output Protection &quot;Use if available&quot;auf anderen Plattformen anzugeben (indem DRM-Versionen unter Windows auf die Blockierungsliste gesetzt werden).
