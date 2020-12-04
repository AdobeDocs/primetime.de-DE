---
seo-title: Lizenzverkettung
title: Lizenzverkettung
uuid: dcc12663-ef9e-4c73-b837-66fcec39358b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Lizenzketten{#license-chaining}

Wenn die für die Lizenzgenerierung verwendete Richtlinie Lizenzketten unterstützt, muss der Server entscheiden, ob eine Leaf-Lizenz, eine Root-Lizenz oder beides ausgegeben werden soll. Um festzustellen, welche Art von Lizenz eine Richtlinie unterstützt, verwenden Sie `Policy.getLicenseChainType()` oder rufen Sie `Policy.getRootLicenseId()` auf, um zu ermitteln, ob die Richtlinie über eine Stammlizenz verfügt. Bei der Verkettung von Adobe Access 2.0-Lizenzen stellt der Server in der Regel eine Laublizenz aus, wenn er zum ersten Mal eine Lizenz für einen bestimmten Rechner und danach eine Root-Lizenz anfordert. Rufen Sie `LicenseRequestMessage.clientHasLeafForPolicy()` auf, um festzustellen, ob auf dem Computer bereits eine Laublizenz für die angegebene Richtlinie vorhanden ist.
