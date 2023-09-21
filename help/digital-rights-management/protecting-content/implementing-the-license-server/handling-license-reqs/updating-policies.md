---
title: Aktualisieren von DRM-Richtlinien
description: Aktualisieren von DRM-Richtlinien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Aktualisieren von DRM-Richtlinien {#updating-drm-policies}

Wenn DRM-Richtlinien aktualisiert werden, nachdem der Inhalt gepackt wurde, stellen Sie die aktualisierten DRM-Richtlinien für den Lizenzserver bereit, damit die aktualisierte Version bei der Lizenzerteilung verwendet werden kann. Wenn ein Lizenzserver Zugriff auf eine Datenbank zum Speichern von DRM-Richtlinien hat, können Sie die aktualisierte DRM-Richtlinie aus der Datenbank abrufen und aufrufen `LicenseRequestMessage.setSelectedPolicy()` Bereitstellung der neuen Fassung der DRM-Politik.

Für Lizenzserver, die nicht auf eine zentrale Datenbank angewiesen sind, unterstützt das SDK DRM Policy Update Lists. Eine DRM-Richtlinienaktualisierungsliste ist eine Datei mit einer Liste aktualisierter oder widerrufener DRM-Richtlinien. Wenn eine DRM-Richtlinie aktualisiert wird, generieren Sie eine neue DRM Policy Update List und pushen Sie die Liste regelmäßig auf alle Lizenzserver. Übergeben Sie die Liste an das SDK, indem Sie `HandlerConfiguration.setPolicyUpdateList()`. Wenn eine Aktualisierungsliste bereitgestellt wird, prüft das SDK diese Liste bei der Analyse der Inhaltsmetadaten. `ContentInfo.getUpdatedPolicies()` enthält die aktualisierten Versionen der DRM-Richtlinien, die in den Metadaten angegeben sind.

Siehe [Arbeiten mit DRM-Richtlinien](../../../protecting-content/working-policies-overview/working-with-policies.md) und [Listen zur Aktualisierung von DRM-Richtlinien](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
