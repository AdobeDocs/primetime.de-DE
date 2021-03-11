---
title: Aktualisieren von DRM-Richtlinien
description: Aktualisieren von DRM-Richtlinien
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Aktualisieren von DRM-Richtlinien {#updating-drm-policies}

Wenn DRM-Richtlinien aktualisiert werden, nachdem der Inhalt gepackt wurde, stellen Sie die aktualisierten DRM-Richtlinien für den Lizenzserver bereit, damit die aktualisierte Version bei der Lizenzerteilung verwendet werden kann. Wenn ein Lizenzserver Zugriff auf eine Datenbank zum Speichern von DRM-Richtlinien hat, können Sie die aktualisierte DRM-Richtlinie aus der Datenbank abrufen und `LicenseRequestMessage.setSelectedPolicy()` aufrufen, um die neue Version der DRM-Richtlinie bereitzustellen.

Bei Lizenzservern, die nicht auf eine zentrale Datenbank angewiesen sind, unterstützt das SDK DRM Policy Update-Listen. Eine DRM-Liste zur Richtlinienaktualisierung ist eine Datei, die eine Liste aktualisierter oder gesperrter DRM-Richtlinien enthält. Wenn eine DRM-Richtlinie aktualisiert wird, erstellen Sie eine neue DRM Policy Update-Liste und geben Sie die Liste regelmäßig auf alle Lizenzserver. Übergeben Sie die Liste an das SDK, indem Sie `HandlerConfiguration.setPolicyUpdateList()` festlegen. Wenn eine Update-Liste bereitgestellt wird, konsultiert das SDK diese Liste, wenn es die Inhaltsmetadaten analysiert. `ContentInfo.getUpdatedPolicies()` enthält die aktualisierten Versionen der DRM-Richtlinien, die in den Metadaten angegeben sind.

Siehe [Arbeiten mit DRM-Richtlinien](../../../protecting-content/working-policies-overview/working-with-policies.md) und [DRM-Listen zur Richtlinienaktualisierung](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)