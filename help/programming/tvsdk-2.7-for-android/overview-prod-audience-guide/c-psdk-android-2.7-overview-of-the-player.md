---
description: TVSDK für Android 2.5 enthält eine Reihe von Funktionen, die Sie in Ihren Playern implementieren können.
title: Primetime TVSDK-Funktionen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Primetime TVSDK-Funktionen {#primetime-tvsdk-features}

TVSDK für Android 2.7 enthält eine Reihe von Funktionen, die Sie in Ihren Playern implementieren können.

TVSDK-Funktionen:

* **VOD- und Live-/Lineare Wiedergabe**

   * Verwaltung des Wiedergabefensters, einschließlich Methoden zum Abspielen, Anhalten, Anhalten, Suchen und Abrufen der Abspielposition
   * Unterstützung für Wiederholung des vollständigen Ereignisses
   * Untertitel (608, 708, WebVTT) und alternative Audioformate zur Verbesserung der Barrierefreiheit
   * Steuerelemente für den Textstil in Beschriftungen
   * DVR-Funktionalität, &quot;Fast Forward&quot;und &quot;Fast Rewind&quot;(die beiden letzteren werden als *Trick-Play-Modus* bezeichnet)
   * Logik der adaptiven Bitrate (ABR) und erste Einrichtung von ABR-Steuerelementen
   * Unterstützung für Live-Manifest-Failover
   * Anpassbare Wiedergabepuffer
   * Unterstützung für Fragmentdauer, -größe und Downloadzeit

* **Werbung**

   * VPAID 2.0
   * Clientseitige Anzeigenzuordnung

      * Nahtlose Anzeigeneinfügung, einschließlich Unterstützung für VAST/VMAP
      * Unterstützung benutzerdefinierter Cue-Tags für Anzeigen
      * Unterstützung für das Markieren, Ersetzen und Löschen von C3-Anzeigen
      * Anpassbare Arbeitsabläufe zum Einfügen von Inhalten/Anzeigen einschließlich Blackout-Signalisierung

* **Inhaltsschutz**

   * Zugang zu DRM-bezogenen Diensten (Digital Rights Management)
   * Wiedergabe von HLS-Streams unverschlüsselt oder mit Protected HTTP Live Streaming (PHLS)
   * Auflösungsbasierte Ausgabesteuerung basierend auf DRM-Politik

* **Video- und Anzeigenverfolgung**

   * Verfolgung von QoS-Ereignissen
   * Benachrichtigungen, die TVSDK und Ihrer Anwendung helfen, asynchron über den Status von Videos, Anzeigen und anderen Elementen zu kommunizieren. In den Benachrichtigungen wird auch die Aktivität protokolliert.

* **Protokollierung**

   * Debug-Protokollierung
   * Unterstützung zur Verfolgung von Fragmentdauer, -größe und Downloadzeit.