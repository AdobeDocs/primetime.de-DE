---
cloud: experience-cloud
product: primetime
audience: end-user
user-guide-title: Hilfe zur Implementierung der Primetime-Referenz
user-guide-description: Das Tutorial hilft, das TVSDK zu verstehen und die Funktions-Manager zu modifizieren, um Ihren persönlichen Player anzupassen.
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 7%

---


# PSDK 1.4 für Android-Referenzimplementierung {#reference-implementation}

+ [Übersicht über die Android-Referenzimplementierung](home.md)
+ Primetime-Referenz-Implementierung {#reference}
   + [Verwendung der Primetime-Referenzimplementierung](ref-implementation/how-to-use-ref-player.md)
   + [Referenz-Implementierungsstruktur](ref-implementation/ref-player-structure.md)
   + Verwendung von Feature-Managern {#feature-managers}
      + [So verwenden Sie Feature Manager](ref-implementation/using-feature-managers/how-to-use-feature-managers.md)
      + [Erstellen von Funktionsmanagern durch Weiterleiten von Konfigurationsinformationen an den MediaPlayer...](ref-implementation/using-feature-managers/creating-feature-managers.md)
      + [Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory](ref-implementation/using-feature-managers/turning-features-on-off.md)
      + [Umgang mit Ereignissen](ref-implementation/using-feature-managers/handling-events.md)
   + Einrichten der Development-Umgebung {#setup-dev}
      + [Einrichten der Entwicklungs-Umgebung](set-up-dev-environment/set-up-dev-environment-overview.md)
      + [Herunterladen und Konfigurieren der erforderlichen Software](set-up-dev-environment/download-prereqs-android.md)
      + [Primetime-Referenzimplementierung erstellen](set-up-dev-environment/install-the-ref-player-project.md)
   + Code {#explore-code}
      + [PlayerFragment](set-up-dev-environment/exploring-code/player-fragment.md)
      + [Funktionmanager](set-up-dev-environment/exploring-code/about-psdk-feature-managers.md)
      + [ConfigProvider](set-up-dev-environment/exploring-code/config-provider.md)
      + [SettingsActivity](set-up-dev-environment/exploring-code/settings-activity.md)
      + [Katalogformat](set-up-dev-environment/exploring-code/catalog-format.md)
      + [JSON-Objekt für Primetime-Anzeigen](set-up-dev-environment/exploring-code/json-pt-ads.md)
      + [JSON-Objekt für direkte Werbeunterbrechungen](set-up-dev-environment/exploring-code/json-direct-ad-breaks.md)
      + [JSON-Objekt für benutzerdefinierte Anzeigenmarken](set-up-dev-environment/exploring-code/json-custom-ad-markers.md)
      + [JSON-Objekt für Berechtigungsressourcen-ID](set-up-dev-environment/exploring-code/json-entitlement-resource-id.md)
      + [Beispiel für ein JSON-Feed-Format](set-up-dev-environment/exploring-code/example-json-feed-format.md)
   + Videowiedergabe implementieren {#implement-video}
      + [Grundlegende Vorgänge bei der Videowiedergabe](implement-video-playback/video-playback.md)
      + [Aktivieren der Videowiedergabe](implement-video-playback/enable-video-playback.md)
      + [DRM-Inhaltsschutz](implement-video-playback/content-protection.md)
   + [Mehrere Bitraten](implement-video-playback/mbr.md)
   + Richten Sie einen Player für die DVR-Wiedergabe mit Anzeigen {#dvr} ein.
      + [DVR ohne Anzeigeneinfügung](implement-video-playback/dvr/dvr-without-ad-insertion.md)
      + [DVR mit Anzeigeneinfügung](implement-video-playback/dvr/dvr-with-ad-insertion.md)
      + [Auswählen eines benutzerdefinierten Startpunkts für DVR](implement-video-playback/dvr/dvr-custom-start-point.md)
      + [Festlegen einer benutzerdefinierten Beginn-Zeit in der Referenzimplementierung](implement-video-playback/dvr/set-custom-start-time-dvr.md)
   + [Anzeigen von QoS-Wiedergabe und Gerätestatistiken](implement-video-playback/qos-statistics.md)
   + Anzeigen {#insert-ads} einfügen
      + [Anzeigeneinfügung](insert-ads/ad-insertion.md)
      + [Anzeigeneinfügetypen](insert-ads/ad-insertion-types.md)
      + [hinzufügen](insert-ads/add-advertising.md)
      + [Verwandte API-Dokumentation](insert-ads/aps-callbacks-ad-insertion.md)
   + Spätbindendes Audio {#late-binding-audio}
      + [Übersicht](late-binding-audio/late-binding-audio-overview.md)
      + [Integration von spätbindenden Audiodaten](late-binding-audio/aa-enable.md)
      + [Audiospuren auswählen](late-binding-audio/select-audio-tracks.md)
      + [Verwandte API-Dokumentation](late-binding-audio/aa-api-callbacks.md)
   + Berechtigungsflüsse für Primetime-Authentifizierung {#primetime-authentications}
      + [Übersicht](paytvpass-entitlement/paytvpass-entitlement-overview.md)
      + [Übersicht über Berechtigungs-Manager](paytvpass-entitlement/entitlement-overvivew.md)
      + [Primetime-Authentifizierung integrieren](paytvpass-entitlement/integrate-pass.md)
      + [Adobe Analytics Berichte konfigurieren](paytvpass-entitlement/pass-analytics-setup.md)
      + [Verwandte API-Dokumentation](paytvpass-entitlement/pass-apis-callbacks.md)
   + Video Analytics {#video-analytics}
      + [Videoanalyse](video-analytics/video-analytics-overview.md)
      + [Video Analytics Manager erstellen](video-analytics/create-video-analytics-manager.md)
      + [Videoanalyse konfigurieren](video-analytics/configure-video-analytics-manager.md)
      + [Verwandte API-Dokumentation](video-analytics/va-apis-callbacks.md)
   + [Benutzerdefinierte Benutzeroberfläche erstellen](build-custom-ui.md)
   + [Fehlerbehebung](troubleshooting.md)
