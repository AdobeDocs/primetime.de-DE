---
title: Primetime-Versionshinweise
seo-title: Adobe Primetime Versionshinweise
description: 'null'
seo-description: 'null'
translation-type: tm+mt
source-git-commit: a42c5b4478967822c920d96b05d5f04a6dec8c25
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 27%

---


# Primetime-Versionshinweise

Willkommen bei den Adobe Primetime Versionshinweisen. Die im linken Navigationsbereich aufgelisteten Dokumente enthalten veröffentlichungsspezifische Informationen, Systemanforderungen, Einschränkungen, behobene Probleme und bekannte Probleme.

## Erweiterungen und Fehlerbehebungen in PTAI 21.2.2

Die Version unterstützt die Stream-Einfügung/Synchronisierung von EXT-X-IMAGE-STREAM-INF in HLS-Streams. Die Funktion wird durch eine serverseitige Konfiguration aktiviert. Wenden Sie sich an Ihren Kundenbetreuer, um die Funktion zu aktivieren.

## Fehlerbehebungen in TVSDK 3.13 Android

Diese Version bietet eine Problemumgehung zum Problem des Einfrierens des Widevine DRM-Streams oder der Anzeige von schwarzen Rahmen auf ABR-Switches auf FireTV-Geräten, zu denen Fire TV der 3. Generation von Pendant und Fire TV-Cuben der 1. und 2. Generation gehören.

Um das Problem zu beheben, stellen Sie die API `MediaPlayer.flushVideoDecoderOnHeaderChange(true)` für die angegebenen Fire TV-Geräte ein, bevor Sie die Wiedergabe starten. Der Standardwert ist false.

Weitere Informationen finden Sie unter [TVSDK für Android-Versionshinweise](../release-notes/tvsdk-3x-android.md).

## Erweiterungen und Fehlerbehebungen in den iOS-Versionshinweisen zu TVSDK 3.12

Die Veröffentlichung konzentrierte sich auf die Lösung der wichtigsten Kundenprobleme.

Weitere Informationen zur aktuellen Version von [iOS](../release-notes/tvsdk-3x-ios.md) finden Sie unter .

## Siehe auch

| Benutzerhandbuch | Beschreibung |
|--- |--- |
| [Hilfe zur Primetime-Programmierung](/help/programming/home.md) | Ermöglicht die Entwicklung von Anwendungen und Video-Playern mit Java auf Android-Geräten und Objective-C auf iOS-Geräten. |
| [Hilfe zur Primetime-Migration und -Konversion](/help/migration-guides/home.md) | Erklärt den Konversions- und Migrationsprozess zum Übergang von der vorhandenen Primetime TVSDK-Suite zur Suite der nächsten Generation. |
| [Referenzimplementierung](/help/android-reference-implementation/home.md) | Das Tutorial hilft, das TVSDK zu verstehen und die Funktions-Manager zu modifizieren, um Ihren persönlichen Player anzupassen. |
| [Primetime-API-Verweise](/help/reference/api-references.md) | Enthält detaillierte Informationen über TVSDK-Funktionen, Datenstrukturen und andere Programmkonstrukte. |
| [Digital Rights Management](/help/digital-rights-management/home.md) | Hilft Ihnen, mehr über verschiedene Benutzerszenarien in Digital Rights Management (DRM) zu erfahren |
| [Hilfe zu Primetime Ad Insertion](/help/primetime-ad-insertion/home.md) | Erklärt, wie man Inhalte durch Einfügen nutzergerechter dynamischer Anzeigen auf dem Server monetarisieren und die Zielgruppe mit personalisierten Anzeigen ansprechen kann. |
| [Archive](https://helpx.adobe.com/primetime/archives.html) | Laden Sie PDFs der archivierten Dokumentation herunter. |

## Hilfreiche Ressourcen

* [Adobe Primetime kennenlernen](https://www.adobe.com/in/marketing/primetime.html)

* [Parallelüberwachung](https://tve.helpdocsonline.com/concurrency-monitoring-introduction)

* [Primetime-Authentifizierung](https://tve.helpdocsonline.com/home)

* [Adobe Primetime DRM-Foren](https://forums.adobe.com/community/adobe_access)

* [Adobe Primetime Developer Resources](https://www.adobe.com/devnet/primetime.html)
