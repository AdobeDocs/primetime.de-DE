---
title: Richtlinien aktualisieren
description: Richtlinien aktualisieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Richtlinien aktualisieren {#updating-policies}

Wenn Richtlinien aktualisiert werden, nachdem der Inhalt gepackt wurde, stellen Sie die aktualisierten Richtlinien für den Lizenzserver bereit, damit die aktualisierte Version bei der Lizenzerteilung verwendet werden kann. Wenn Ihr Lizenzserver Zugriff auf eine Datenbank zum Speichern von Richtlinien hat, können Sie die aktualisierte Richtlinie aus der Datenbank abrufen und `LicenseRequestMessage.setSelectedPolicy()` , um die neue Version der Richtlinie anzugeben.

Bei Lizenzservern, die nicht auf eine zentrale Datenbank angewiesen sind, unterstützt das SDK Listen für Richtlinienaktualisierungen. Eine Liste mit aktualisierten Richtlinien ist eine Datei mit einer Liste aktualisierter oder gesperrter Richtlinien. Wenn eine Richtlinie aktualisiert wird, generieren Sie eine neue Liste für Richtlinienaktualisierungen und geben Sie die Liste regelmäßig an alle Lizenzserver weiter. Übergeben Sie die Liste an das SDK, indem Sie `HandlerConfiguration.setPolicyUpdateList()`. Wenn eine Aktualisierungsliste bereitgestellt wird, prüft das SDK diese Liste beim Analysieren der Inhaltsmetadaten. `ContentInfo.getUpdatedPolicies()` enthält die aktualisierten Versionen der Richtlinien, die in den Metadaten angegeben sind.

Siehe [Arbeiten mit Richtlinien](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) und [Listen mit Richtlinienaktualisierungen.](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
