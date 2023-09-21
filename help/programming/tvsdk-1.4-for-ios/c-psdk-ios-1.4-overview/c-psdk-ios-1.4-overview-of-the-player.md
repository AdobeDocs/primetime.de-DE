---
description: TVSDK für iOS umfasst eine Vielzahl von Funktionen.
title: Primetime TVSDK-Funktionen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Primetime TVSDK-Funktionen {#primetime-tvsdk-features}

TVSDK für iOS umfasst eine Vielzahl von Funktionen und bietet die folgenden Hauptfunktionen:

* VOD- und Live-/lineare Wiedergabe

   * Verwaltung des Wiedergabefensters, einschließlich Methoden zum Abspielen, Stoppen, Anhalten, Suchen und Abrufen der Abspielposition
   * Unterstützung für Wiederholung des vollständigen Ereignisses
   * Verdeckte Untertitel (608, WebVTT) und alternative Formen von Audio für verbesserte Barrierefreiheit
   * DVR-Funktion
   * Logik der adaptiven Bitrate (ABR) und anfängliche Einrichtung von ABR-Steuerelementen
   * Anmeldung für Nicht-HLS- und HLS-Tags
   * Unterstützung für Live-Manifest-Failover

* Werbung

   * VPAID 2.0
   * Clientseitige Anzeigenzuordnung

      * Nahtloses Hinzufügen von Anzeigen, einschließlich Unterstützung für VAST/VMAP
      * Unterstützung für benutzerdefinierte Cue-Tags für Anzeigen
      * Unterstützung für das Markieren, Ersetzen und Löschen von C3-Anzeigen
      * Anpassbarer Arbeitsablauf für Inhalte/Anzeigen, einschließlich Blackout-Signalisierung

* Inhaltsschutz

   * Zugang zu DRM-bezogenen Diensten (Digital Rights Management)
   * Wiedergabe von HLS-Streams unverschlüsselt oder mit geschütztem HTTP Live Streaming (PHLS)
   * Auflösungsbasierte Ausgabesteuerung basierend auf DRM-Politik

* Video- und Anzeigen-Tracking

   * QoS-Ereignis-Tracking
   * Benachrichtigungen, die TVSDK und Ihrer Anwendung dabei helfen, asynchron über den Status von Videos, Anzeigen und anderen Elementen zu kommunizieren, und auch über diese Protokollaktivität
   * Integration in Adobe Analytics und Heartbeat-Unterstützung

* Protokollierung

   * Debug-Protokollierung
