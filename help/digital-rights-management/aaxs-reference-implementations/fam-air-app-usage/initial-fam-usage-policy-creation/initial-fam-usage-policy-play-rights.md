---
seo-title: Rechte abspielen
title: Rechte abspielen
uuid: 90f2a7a6-6637-4d10-9afe-6d2e77fc4185
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Rechte abspielen {#play-rights}

In der folgenden Tabelle werden die Voreinstellungen für die Wiedergabe von Rechten beschrieben:

| Voreinstellung | Beschreibung |
|--- |--- |
| Wiedergabefenster | Die Dauer einer Lizenz ist gültig (in Minuten), nachdem der Benutzer den geschützten Inhalt zum ersten Mal wiedergegeben hat. |
| Output Protection | Steuert, ob die Ausgabe auf externen Wiedergabegeräten geschützt werden soll. Analoge und digitale Ausgaben können unabhängig angegeben werden. |
| Einschränkungen | Blacklist der Clientversionen, die keine Inhalte wiedergeben dürfen. Alle Spalten sind optional. |
| DRM | Gibt eine Liste von DRM-Versionen an, für die die Wiedergabe geschützter Inhalte nicht zulässig ist. |
| Laufzeit | Gibt eine Liste von Laufzeitversionen an, bei denen geschützte Inhalte nicht abgespielt werden dürfen. |
| Mindestsicherheitsstufe |  |
| DRM | DRM-Mindestsicherheitsstufe, die zum Abspielen geschützter Inhalte erforderlich ist. |
| Laufzeit | Mindestsicherheitsstufe der Laufzeitumgebung, die zum Abspielen geschützter Inhalte erforderlich ist. |
| Zulässige Anwendungen | Whitelist der Clientanwendungen, die Inhalte abspielen dürfen. Wenn keine Anwendungen angegeben sind, ist jede SWF- oder AIR-Anwendung zulässig. |
| SWF | Liste von SWF-URLs, die geschützte Inhalte wiedergeben dürfen. |
| AIR | Liste von AIR-Anwendungen, die geschützte Inhalte abspielen dürfen. Herausgeber-ID erforderlich ist, sind die übrigen Felder optional. |

Flash Access Manager unterstützt Richtlinien, die mehrere Wiedergaberechte enthalten. Um eine Richtlinie mit mehr als einer Wiedergaberechse zu erstellen, klicken Sie auf die Schaltfläche &quot;Hinzufügen zusätzliche Wiedergaberechte&quot;und füllen Sie die gewünschten Attribute für jede Wiedergaberechnung aus.

Bei der Nutzung einer Lizenz verwendet der Client das erste Wiedergaberecht, für das er alle Anforderungen erfüllt. Mehrere Wiedergaberechte können verwendet werden, um für verschiedene Betriebssysteme unterschiedliche Einschränkungen festzulegen. Beispielsweise ist es möglich, eine Rechte mit Output Protection für Windows anzugeben (durch Blacklist DRM Versionen unter Macintosh und Linux) und eine zweite Rechte mit Output Protection &quot;Use if available&quot;auf anderen Plattformen (durch Blacklist DRM Versionen unter Windows).
