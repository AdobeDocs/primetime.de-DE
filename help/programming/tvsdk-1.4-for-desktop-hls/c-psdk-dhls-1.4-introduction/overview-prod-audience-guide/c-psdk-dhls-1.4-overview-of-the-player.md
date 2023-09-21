---
description: TVSDK für Desktop-HLS umfasst eine Vielzahl von Funktionen und bietet die folgenden Hauptfunktionen
title: Primetime TVSDK-Funktionen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Primetime TVSDK-Funktionen{#primetime-tvsdk-features}

TVSDK für Desktop-HLS umfasst eine Vielzahl von Funktionen und bietet die folgenden Hauptfunktionen:

* VOD- und Live-/lineare Wiedergabe

   * Verwaltung des Wiedergabefensters, einschließlich Methoden zum Abspielen, Stoppen, Anhalten, Suchen und Abrufen der Abspielposition.
   * Verdeckte Untertitel (608, 708, WebVTT) und alternative Audioformen für verbesserte Barrierefreiheit
   * Steuerung des Textstils in Beschriftungen
   * DVR-Funktion, schnelle Vorwärts-/schnelle Rückspaltung (Trick-Play-Modus)
   * Trickplay für Live- und VOD-Inhalt
   * Logik der adaptiven Bitrate (ABR) und anfängliche Einrichtung von ABR-Steuerelementen
   * Unterstützung für Live-Manifest-Failover
   * Anpassbare Wiedergabepuffer
   * 302 Umleitungsoptimierung
   * Unterstützung von Fragmentdauer, -größe und Downloadzeit

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
   * Cookie- und Cookie-Unterstützung für Medienauth
   * Token-Verpackung für mehrere Domänen

* Video- und Anzeigen-Tracking

   * QoS-Ereignis-Tracking
   * Benachrichtigungen, die TVSDK und Ihrer Anwendung dabei helfen, asynchron über den Status von Videos, Anzeigen und anderen Elementen sowie über diese Protokollaktivität zu kommunizieren.
   * Integration in Adobe Analytics und Heartbeat-Unterstützung

* Protokollierung

   * Debug-Protokollierung.
   * Tracking-Unterstützung für Fragmentdauer, -größe und Downloadzeit.
