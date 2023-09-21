---
description: Gelegentlich kann Inhalt manchmal nicht wiedergegeben werden. Dies kann in beliebig vielen Situationen auftreten, darunter Fehler im Browsernetzwerk-Stack, Transportschicht, Betriebssystem, Flash Player-Laufzeit oder Primetime-DRM-System.
title: Übersicht über Testfehler
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Testen von Fehlern {#triaging-errors}

Gelegentlich kann Inhalt manchmal nicht wiedergegeben werden. Dies kann in beliebig vielen Situationen auftreten, darunter Fehler im Browsernetzwerk-Stack, Transportschicht, Betriebssystem, Flash Player-Laufzeit oder Primetime-DRM-System.

Der erste diagnostische Schritt besteht darin zu ermitteln, ob sich das Problem manifestiert, ohne dass die DRM-Verschlüsselung in die Gleichung eingeführt wird. Versuchen Sie, den Inhalt zu verpacken, weisen Sie den Packager jedoch an, den Inhalt nicht zu verschlüsseln. Wenn das Problem weiterhin besteht, ist es wahrscheinlich ein Problem beim Kodieren oder Verpacken des Inhalts oder irgendwo in der Netzwerkinfrastruktur. Wenn das Problem verschwindet, wenn der Inhalt ohne Verschlüsselung gepackt wird, liegt der Wiedergabefehler wahrscheinlich an einem DRM-Problem und Sie sollten Client/Server-Triaging durchführen.

Primetime DRM (außerhalb von Primetime Cloud DRM) ist seit mehreren Jahren auf dem Markt. Daher gibt es eine Vielzahl von von Community-bezogenen Informationen zur Fehlerbehebung und Konfiguration von Primetime DRM. Adobe hat ein Forum für Primetime DRM (ehemals Adobe Access)-Benutzer geschaffen, um Probleme und Lösungen zu sammeln und zu teilen. Um festzustellen, ob Ihr Problem bereits besprochen wurde, überprüfen Sie Folgendes: [https://forums.adobe.com/community/adobe_access](https://forums.adobe.com/community/adobe_access)

## Testen von Client-Fehlern {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}

Wenn Inhalt nicht wiedergegeben wird, überprüfen Sie bitte das rechte Bedienfeld der Beispiel-Videoplayer, das alle `DRMErrorEvent` auftritt. Wenn ein Fehlerereignis vorhanden ist, korreliert es mit einem der Flash Player Runtime-Fehler :

* [DRM Client-Fehlermeldungsreferenz](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)oder
* [AS3 Flash Runtime-Fehler](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html) (DRM-Probleme beginnen bei 3300)
