---
title: Überblick über das Vorausfüllen von Lizenzen für die Offline-Wiedergabe
description: Überblick über das Vorausfüllen von Lizenzen für die Offline-Wiedergabe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# Vorausfüllen von Lizenzen für die Offline-Wiedergabe {#pre-loading-licenses-for-offline-playback}

Sie können die Lizenzen vorausfüllen, die erforderlich sind, um durch Primetime DRM geschützte Inhalte wiederzugeben. Mit vorab geladenen Lizenzen können Benutzer den Inhalt anzeigen, unabhängig davon, ob sie über eine aktive Internetverbindung verfügen oder nicht.

Der Preload-Prozess selbst *does* eine Internetverbindung benötigen. Sie können `DRMManager.loadVoucher()` vorziehen, um die Lizenzen vorab zu laden. Später, wenn der Kunde den gewünschten Inhalt abspielen möchte, wurde das DRM-System vorinstalliert und kann den geschützten Inhalt sofort abspielen.
