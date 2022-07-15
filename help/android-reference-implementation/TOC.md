---
product: primetime
audience: end-user
user-guide-title: Hilfe zur Primetime-Referenzimplementierung
user-guide-description: Das Tutorial hilft, das TVSDK zu verstehen und die Funktions-Manager zu modifizieren, um Ihren persönlichen Player anzupassen.
source-git-commit: 95626ebde981d1996652a67bc9e0cea05f24aa6d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# PSDK 1.4 für Android-Referenzimplementierung {#reference-implementation}

+ [Übersicht über die Implementierung der Android-Referenz](home.md)
+ Primetime-Referenzimplementierung {#reference}
   + [Verwendung der Primetime-Referenzimplementierung](ref-implementation/how-to-use-ref-player.md)
   + [Referenz-Implementierungsstruktur](ref-implementation/ref-player-structure.md)
   + Verwenden von Feature Manager {#feature-managers}
      + [Verwenden von Feature Manager](ref-implementation/using-feature-managers/how-to-use-feature-managers.md)
      + [Erstellen von Funktions-Managern durch Weiterleiten von Konfigurationsinformationen an den MediaPlayer ...](ref-implementation/using-feature-managers/creating-feature-managers.md)
      + [Aktivieren oder Deaktivieren von Funktionen mit ManagerFactory](ref-implementation/using-feature-managers/turning-features-on-off.md)
      + [Umgang mit Ereignissen](ref-implementation/using-feature-managers/handling-events.md)
   + Einrichten der Entwicklungsumgebung {#setup-dev}
      + [Einrichten der Entwicklungsumgebung](set-up-dev-environment/set-up-dev-environment-overview.md)
      + [Herunterladen und Konfigurieren von Voraussetzungs-Software](set-up-dev-environment/download-prereqs-android.md)
      + [Erstellen der Primetime-Referenzimplementierung](set-up-dev-environment/install-the-ref-player-project.md)
   + Code durchsuchen {#explore-code}
      + [PlayerFragment](set-up-dev-environment/exploring-code/player-fragment.md)
      + [Funktionsmanager](set-up-dev-environment/exploring-code/about-psdk-feature-managers.md)
      + [ConfigProvider](set-up-dev-environment/exploring-code/config-provider.md)
      + [SettingsActivity](set-up-dev-environment/exploring-code/settings-activity.md)
      + [Katalogformat](set-up-dev-environment/exploring-code/catalog-format.md)
      + [JSON-Objekt für Primetime-Anzeigen](set-up-dev-environment/exploring-code/json-pt-ads.md)
      + [JSON-Objekt für direkte Werbeunterbrechungen](set-up-dev-environment/exploring-code/json-direct-ad-breaks.md)
      + [JSON-Objekt für benutzerdefinierte Anzeigenmarken](set-up-dev-environment/exploring-code/json-custom-ad-markers.md)
      + [JSON-Objekt für Kennung der Berechtigungsressource](set-up-dev-environment/exploring-code/json-entitlement-resource-id.md)
      + [Beispiel für ein JSON-Feed-Format](set-up-dev-environment/exploring-code/example-json-feed-format.md)
   + Implementieren der Videowiedergabe {#implement-video}
      + [Grundlegende Vorgänge der Videowiedergabe](implement-video-playback/video-playback.md)
      + [Videowiedergabe aktivieren](implement-video-playback/enable-video-playback.md)
      + [DRM-Inhaltsschutz](implement-video-playback/content-protection.md)
   + [Mehrere Bitraten](implement-video-playback/mbr.md)
   + Einrichten eines Players für die DVR-Wiedergabe mit Anzeigen {#dvr}
      + [DVR ohne Anzeigeneinfügung](implement-video-playback/dvr/dvr-without-ad-insertion.md)
      + [DVR mit Anzeigeneinfügung](implement-video-playback/dvr/dvr-with-ad-insertion.md)
      + [Auswählen eines benutzerdefinierten Startpunkts für DVR](implement-video-playback/dvr/dvr-custom-start-point.md)
      + [Festlegen einer benutzerdefinierten Startzeit in der Referenzimplementierung](implement-video-playback/dvr/set-custom-start-time-dvr.md)
   + [Anzeigen von QoS-Wiedergabe und Gerätestatistiken](implement-video-playback/qos-statistics.md)
   + Anzeigen einfügen {#insert-ads}
      + [Anzeigeneinfügung](insert-ads/ad-insertion.md)
      + [Anzeigeneinfügetypen](insert-ads/ad-insertion-types.md)
      + [Hinzufügen von Werbung](insert-ads/add-advertising.md)
      + [Verwandte API-Dokumentation](insert-ads/aps-callbacks-ad-insertion.md)
   + Spätbindende Audiowiedergabe {#late-binding-audio}
      + [Übersicht](late-binding-audio/late-binding-audio-overview.md)
      + [Integrieren von spätbindendem Audio](late-binding-audio/aa-enable.md)
      + [Auswählen der Audiospuren](late-binding-audio/select-audio-tracks.md)
      + [Verwandte API-Dokumentation](late-binding-audio/aa-api-callbacks.md)
   + Berechtigungsflüsse zur Primetime-Authentifizierung {#primetime-authentications}
      + [Übersicht](paytvpass-entitlement/paytvpass-entitlement-overview.md)
      + [Übersicht über Entitäts-Manager](paytvpass-entitlement/entitlement-overvivew.md)
      + [Integrieren der Primetime-Authentifizierung](paytvpass-entitlement/integrate-pass.md)
      + [Adobe Analytics Reporting konfigurieren](paytvpass-entitlement/pass-analytics-setup.md)
      + [Verwandte API-Dokumentation](paytvpass-entitlement/pass-apis-callbacks.md)
   + Video Analytics {#video-analytics}
      + [Video Analytics](video-analytics/video-analytics-overview.md)
      + [Video Analytics Manager erstellen](video-analytics/create-video-analytics-manager.md)
      + [Video Analytics konfigurieren](video-analytics/configure-video-analytics-manager.md)
      + [Verwandte API-Dokumentation](video-analytics/va-apis-callbacks.md)
   + [Benutzerdefinierte Benutzeroberfläche erstellen](build-custom-ui.md)
   + [Fehlerbehebung](troubleshooting.md)
