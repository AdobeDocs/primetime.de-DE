---
title: Roku SSO-Übersicht
description: Über Roku SSO
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---


# Roku SSO-Übersicht {#overview}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Einführung {#roku-sso-intro}

In diesem Dokument werden die Informationen beschrieben, die erforderlich sind, um die Single-Sign-On-Funktion auf Roku-Geräten nutzen zu können. Adobe Primetime Authentication arbeitet mit Roku zusammen, um die Benutzererfahrung bei der Anmeldung zu verbessern und Single Sign-On für TV-Abonnenten überall auf der Welt zu ermöglichen.

Die Lösung basiert auf der Client-losen REST-API der Adobe Primetime-Authentifizierung, sodass die meisten Programmierer ihre Anwendungen nicht aktualisieren müssen, um Single Sign-On nutzen zu können.

## Aktivieren von Roku SSO {#enable-roku-sso}

Roku SSO ist standardmäßig aktiviert, es sei denn, der Programmierer oder MVPD fordert die Deaktivierung von SSO an.

Jeder Programmierer kann SSO für bestimmte Integrationen auf der Roku-Plattform aktivieren/deaktivieren.

### Was ein Programmierer tun sollte, damit Roku SSO funktioniert {#make-roku-sso-work}

Für Programmiereranwendungen, die die REST-API auf Clientgeräten implementieren, funktioniert die Roku-SSO ohne Änderungen. Roku OS fügt bei jeder Anfrage zwei HTTP-Header zu Adobe Primetime-Authentifizierungsendpunkten hinzu.

Bei Programmiereranwendungen, die eine Server-zu-Server-Lösung für REST-API implementieren, sollte sich der Programmierer an das Roku-Team wenden und nach einer Konfiguration fragen, bei der diese beiden Header bei allen API-Flüssen an ihre Domäne gesendet werden.

Von Roku bereitgestellte Abonnenten-ID, die anstelle der von der Anwendung übergebenen Geräte-ID verwendet werden soll, um eine anwendungsübergreifende (und geräteübergreifende) SSO zu gewährleisten.

Wenden Sie sich an Ihren Kundenbetreuer, um genauere Informationen zum Format der erforderlichen Kopfzeilen zu erhalten.

### Mögliche Probleme {#possible-issues}

Programmierer sollten überprüfen, ob ihre aktuellen Implementierungen, die auf der Client-losen REST-API der Adobe basieren, die Plattform-SSO von Roku nicht behindern. Unten finden Sie eine Liste möglicher Probleme und wie diese gelöst werden sollten.

| Problem | Mögliche Ursache | Mögliche Lösungen | |-|-|-| |Kein Roku-SSO-Header an Adobe gesendet|Verwenden von HTTP anstelle von HTTPS für Aufrufe an Adobe Primetime-Authentifizierungsdomänen|HTTPS verwenden| |Das MVPD-Logo wird für SSO-Token nicht angezeigt/nicht aktualisiert|Die Benutzeroberfläche basiert auf lokalem Speicher. Anwendungen sollten die Benutzeroberfläche (und den lokalen Speicher bei Bedarf aktualisieren, nachdem die Authentifizierung überprüft wurde)| |Logout auf kein AuthZ|Anwendungsdesign|Anwendung sollte aktualisiert werden, damit sich das Programm nicht hinter den Kulissen abmelden kann|

## FAQs {#faq}

* **Wie wird die einmalige Anmeldung funktionieren?**

   SSO funktioniert für alle Programmierer-Anwendungen, die durch Adobe Primetime-Authentifizierung unterstützt werden, auf allen Roku-Geräten, die demselben Roku-Benutzer zugeordnet sind.
Nicht alle MVPDs ermöglichen Roku SSO.

* **Werden die Authentifizierungs-TTLs geändert?**

   Das erste gültige Authentifizierungstoken wird für die Durchführung der einmaligen Anmeldung verwendet. In diesem Fall verwenden alle anderen Anwendungen, die über SSO authentifiziert werden, dieselbe TTL, bis sie abläuft. Wenn Sie also von einer Anwendung zur anderen navigieren, teilt die zweite Anwendung die TTL der ersten authentifizierten Anwendung.

* **Funktionieren andere Adobe-Funktionen wie bisher?**

   Alle Primetime-Authentifizierungsfunktionen funktionieren wie bisher.

* **Gibt es einen Opt-in-/Opt-out-Prozess für Programmierer, der von SSO auf der Roku-Plattform profitiert?**

   Dies ist eine Konfigurationsänderung im TVE-Dashboard der Adobe. Jeder Programmierer kann SSO für bestimmte Integrationen auf der Roku-Plattform aktivieren/deaktivieren.
