---
seo-title: Aktualisieren von DRM-Richtlinien
title: Aktualisieren von DRM-Richtlinien
uuid: 6f7a1432-88e4-499b-a008-6c8cf0e9c09b
translation-type: tm+mt
source-git-commit: d5986e9bc8689bf37abdf242a41aea5e768df754

---


# Aktualisieren von DRM-Richtlinien {#updating-drm-policies}

Wenn DRM-Richtlinien aktualisiert werden, nachdem der Inhalt gepackt wurde, stellen Sie die aktualisierten DRM-Richtlinien für den Lizenzserver bereit, damit die aktualisierte Version bei der Lizenzerteilung verwendet werden kann. Wenn ein Lizenzserver Zugriff auf eine Datenbank zum Speichern von DRM-Richtlinien hat, können Sie die aktualisierte DRM-Richtlinie aus der Datenbank abrufen und die neue Version der DRM-Richtlinie `LicenseRequestMessage.setSelectedPolicy()` bereitstellen.

Bei Lizenzservern, die nicht auf eine zentrale Datenbank angewiesen sind, unterstützt das SDK DRM Policy Update-Listen. Eine DRM-Liste zur Richtlinienaktualisierung ist eine Datei, die eine Liste aktualisierter oder gesperrter DRM-Richtlinien enthält. Wenn eine DRM-Richtlinie aktualisiert wird, erstellen Sie eine neue DRM Policy Update-Liste und geben Sie die Liste regelmäßig auf alle Lizenzserver. Übergeben Sie die Liste durch Festlegen an das SDK `HandlerConfiguration.setPolicyUpdateList()`. Wenn eine Update-Liste bereitgestellt wird, konsultiert das SDK diese Liste, wenn es die Inhaltsmetadaten analysiert. `ContentInfo.getUpdatedPolicies()` enthält die aktualisierten Versionen der DRM-Richtlinien, die in den Metadaten angegeben sind.

Siehe Listen [zur Aktualisierung von DRM-Richtlinien](../../../protecting-content/working-policies-overview/working-with-policies.md) und [DRM-Richtlinien](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)