---
seo-title: Richtlinien aktualisieren
title: Richtlinien aktualisieren
uuid: f6686c8b-bedf-4ec5-a14e-f03326519f89
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Richtlinien aktualisieren {#updating-policies}

Wenn Richtlinien nach dem Verpacken des Inhalts aktualisiert werden, stellen Sie die aktualisierten Richtlinien für den Lizenzserver bereit, damit die aktualisierte Version bei der Lizenzerteilung verwendet werden kann. Wenn Ihr Lizenzserver Zugriff auf eine Datenbank zum Speichern von Richtlinien hat, können Sie die aktualisierte Richtlinie aus der Datenbank abrufen und `LicenseRequestMessage.setSelectedPolicy()` aufrufen, um die neue Version der Richtlinie bereitzustellen.

Bei Lizenzservern, die nicht auf eine zentrale Datenbank angewiesen sind, unterstützt das SDK Listen zur Richtlinienaktualisierung. Eine Liste zur Richtlinienaktualisierung ist eine Datei mit einer Liste aktualisierter oder gesperrter Richtlinien. Wenn eine Richtlinie aktualisiert wird, erstellen Sie eine neue Liste zur Richtlinienaktualisierung und schieben Sie die Liste in regelmäßigen Abständen auf alle Lizenzserver. Übergeben Sie die Liste an das SDK, indem Sie `HandlerConfiguration.setPolicyUpdateList()` festlegen. Wenn eine Update-Liste bereitgestellt wird, konsultiert das SDK diese Liste beim Analysieren der Inhaltsmetadaten. `ContentInfo.getUpdatedPolicies()` enthält die aktualisierten Versionen der Richtlinien, die in den Metadaten angegeben sind.

Siehe [Arbeiten mit Richtlinien](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) und [Listen zur Richtlinienaktualisierung.](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
