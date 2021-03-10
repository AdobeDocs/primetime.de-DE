---
title: Übersicht über Vorausfüllen-Lizenzen für die Offline-Wiedergabe
description: Übersicht über Vorausfüllen-Lizenzen für die Offline-Wiedergabe
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---


# Vorausfüllen-Lizenzen für die Offline-Wiedergabe {#pre-loading-licenses-for-offline-playback}

Sie können die Lizenzen vorladen, die erforderlich sind, um durch Primetime DRM geschützte Inhalte wiederzugeben. Mit vorab geladenen Lizenzen können Benutzer den Inhalt unabhängig davon, ob sie über eine aktive Internetverbindung verfügen, Ansicht werden.

Der Preload-Vorgang selbst *erfordert eine Internetverbindung.* Sie können zum Vorausladen von Lizenzen `DRMManager.loadVoucher()` vorzeitig verwenden. Später, wenn der Kunde den gewünschten Inhalt abspielen möchte, wurde das DRM-System vorgerüstet und kann den geschützten Inhalt sofort abspielen.
