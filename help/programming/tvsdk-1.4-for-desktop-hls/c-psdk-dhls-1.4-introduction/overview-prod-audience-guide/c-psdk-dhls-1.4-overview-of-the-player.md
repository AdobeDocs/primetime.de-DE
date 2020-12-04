---
description: 'TVSDK für Desktop-HLS umfasst eine Reihe von Funktionen und bietet die folgenden Hauptfunktionen: '
seo-description: 'TVSDK für Desktop-HLS umfasst eine Reihe von Funktionen und bietet die folgenden Hauptfunktionen: '
seo-title: Primetime TVSDK-Funktionen
title: Primetime TVSDK-Funktionen
uuid: 0a7ebb05-7da5-49ff-928a-4d2124eaa115
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Primetime-TVSDK-Funktionen{#primetime-tvsdk-features}

TVSDK für Desktop-HLS umfasst eine Reihe von Funktionen und bietet die folgenden Hauptfunktionen:

* VOD- und Live-/Lineare Wiedergabe

   * Verwaltung des Wiedergabefensters, einschließlich Methoden zum Abspielen, Anhalten, Anhalten, Suchen und Abrufen der Abspielposition.
   * Untertitel (608, 708, WebVTT) und alternative Audioformate zur Verbesserung der Barrierefreiheit
   * Steuerelement für Textstile in Beschriftungen
   * DVR-Funktionalität, schneller Vorwärts/schneller Rücklauf (Trick-Play-Modus)
   * Trickplay für Live- und VOD-Inhalte
   * Logik der adaptiven Bitrate (ABR) und erste Einrichtung von ABR-Steuerelementen
   * Unterstützung für Live-Manifest-Failover
   * Anpassbare Wiedergabepuffer
   * 302 Umleitungsoptimierung
   * Unterstützung für Fragmentdauer, -größe und Downloadzeit

* Werbung

   * VPAID 2.0
   * Clientseitige Anzeigenzuordnung

      * Nahtlose Anzeigeneinfügung, einschließlich Unterstützung für VAST/VMAP
      * Unterstützung benutzerdefinierter Cue-Tags für Anzeigen
      * Unterstützung für das Markieren, Ersetzen und Löschen von C3-Anzeigen
      * Anpassbare Arbeitsabläufe zum Einfügen von Inhalten/Anzeigen einschließlich Blackout-Signalisierung

* Inhaltsschutz

   * Zugang zu DRM-bezogenen Diensten (Digital Rights Management)
   * Wiedergabe von HLS-Streams unverschlüsselt oder mit Protected HTTP Live Streaming (PHLS)
   * Auflösungsbasierte Ausgabesteuerung basierend auf DRM-Politik
   * Cookie-Unterstützung für Sitzungs- und Medienauth-Cookies
   * Verpacken von Token für mehrere Domänen

* Video- und Anzeigenverfolgung

   * Verfolgung von QoS-Ereignissen
   * Benachrichtigungen, die TVSDK und Ihrer Applikation dabei helfen, asynchron über den Status von Videos, Anzeigen und anderen Elementen zu kommunizieren und auch diese Aktivität zu protokollieren.
   * Integration mit Adobe Analytics und Heartbeat-Unterstützung

* Protokollierung

   * Debug-Protokollierung.
   * Unterstützung zur Verfolgung von Fragmentdauer, -größe und Downloadzeit.