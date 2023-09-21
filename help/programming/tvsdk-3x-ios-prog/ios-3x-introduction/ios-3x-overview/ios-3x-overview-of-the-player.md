---
description: TVSDK für Android 3.4 enthält eine Reihe von Funktionen, die Sie in Ihre Player implementieren können.
title: Primetime TVSDK-Funktionen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Primetime TVSDK-Funktionen {#primetime-tvsdk-features}

TVSDK für iOS umfasst eine Vielzahl von Funktionen, die Sie in Ihren Playern implementieren können.

TVSDK-Funktionen:

* **VOD- und Live-/lineare Wiedergabe**

   * Verwaltung des Wiedergabefensters, einschließlich Methoden zum Abspielen, Stoppen, Anhalten, Suchen und Abrufen der Abspielposition
   * Unterstützung für Wiederholung des vollständigen Ereignisses
   * Verdeckte Untertitel (608, 708, WebVTT) und alternative Audioformen für verbesserte Barrierefreiheit
   * Steuerelemente für die Formatierung von Text in Beschriftungen
   * DVR-Fähigkeit, schnell vorwärts und schnell zurückspulen (die beiden letzteren sind bekannt als *Trick-Play-Modus*)
   * Logik der adaptiven Bitrate (ABR) und anfängliche Einrichtung von ABR-Steuerelementen
   * Unterstützung für Live-Manifest-Failover
   * Anpassbare Wiedergabepuffer
   * Unterstützung von Fragmentdauer, -größe und Downloadzeit

* **Werbung**

   * VPAID 2.0
   * Clientseitige Anzeigenzuordnung

      * Nahtloses Hinzufügen von Anzeigen, einschließlich Unterstützung für VAST/VMAP
      * Unterstützung für benutzerdefinierte Cue-Tags für Anzeigen
      * Unterstützung für das Markieren, Ersetzen und Löschen von C3-Anzeigen
      * Anpassbarer Arbeitsablauf für Inhalte/Anzeigen, einschließlich Blackout-Signalisierung

* **Inhaltsschutz**

   * Zugang zu DRM-bezogenen Diensten (Digital Rights Management)
   * Wiedergabe von HLS-Streams unverschlüsselt oder mit geschütztem HTTP Live Streaming (PHLS)
   * Auflösungsbasierte Ausgabesteuerung basierend auf DRM-Politik

* **Video- und Anzeigen-Tracking**

   * QoS-Ereignis-Tracking
   * Benachrichtigungen, die TVSDK und Ihrer Anwendung dabei helfen, asynchron über den Status von Videos, Anzeigen und anderen Elementen zu kommunizieren. In Benachrichtigungen wird auch die Aktivität Protokollierung protokolliert.

* **Protokollierung**

   * Debug-Protokollierung
   * Tracking-Unterstützung für Fragmentdauer, -größe und Downloadzeit.
