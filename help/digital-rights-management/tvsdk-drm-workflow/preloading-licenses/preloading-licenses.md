---
seo-title: Übersicht über Vorausfüllen-Lizenzen für die Offline-Wiedergabe
title: Übersicht über Vorausfüllen-Lizenzen für die Offline-Wiedergabe
uuid: 71e5169b-7f70-4723-9f9b-fdff822c5876
translation-type: tm+mt
source-git-commit: 9bbcb228d3367fbf53de811bf2941ca653ce3b0e

---


# Vorausfüllen-Lizenzen für die Offline-Wiedergabe {#pre-loading-licenses-for-offline-playback}

Sie können die Lizenzen vorladen, die erforderlich sind, um durch Primetime DRM geschützte Inhalte wiederzugeben. Mit vorab geladenen Lizenzen können Benutzer den Inhalt unabhängig davon, ob sie über eine aktive Internetverbindung verfügen, Ansicht werden.

Der Preload-Prozess selbst *erfordert* eine Internetverbindung. Sie können Lizenzen `DRMManager.loadVoucher()` bereits im Voraus laden. Später, wenn der Kunde den gewünschten Inhalt abspielen möchte, wurde das DRM-System vorgerüstet und kann den geschützten Inhalt sofort abspielen.
