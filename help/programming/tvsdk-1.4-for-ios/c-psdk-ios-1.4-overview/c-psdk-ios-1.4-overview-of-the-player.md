---
description: TVSDK für iOS enthält eine Reihe von Funktionen.
title: Primetime TVSDK-Funktionen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Primetime TVSDK-Funktionen {#primetime-tvsdk-features}

TVSDK für iOS umfasst eine Reihe von Funktionen und bietet die folgenden Hauptfunktionen:

* VOD- und Live-/Lineare Wiedergabe

   * Verwaltung des Wiedergabefensters, einschließlich Methoden zum Abspielen, Anhalten, Anhalten, Suchen und Abrufen der Abspielposition
   * Unterstützung für Wiederholung des vollständigen Ereignisses
   * Untertitel (608, WebVTT) und alternative Audioformate zur Verbesserung der Barrierefreiheit
   * DVR-Fähigkeit
   * Logik der adaptiven Bitrate (ABR) und erste Einrichtung von ABR-Steuerelementen
   * Abonnement zu Nicht-HLS- und HLS-Tags
   * Unterstützung für Live-Manifest-Failover

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

* Video- und Anzeigenverfolgung

   * Verfolgung von QoS-Ereignissen
   * Benachrichtigungen, die TVSDK und Ihrer Applikation dabei unterstützen, asynchron über den Status von Videos, Anzeigen und anderen Elementen zu kommunizieren, und auch die Aktivität protokollieren
   * Integration mit Adobe Analytics und Heartbeat-Unterstützung

* Protokollierung

   * Debug-Protokollierung

