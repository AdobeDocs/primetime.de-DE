---
title: Lizenzverkettung
description: Lizenzverkettung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Lizenzketten{#license-chaining}

Wenn die für die Lizenzgenerierung verwendete Richtlinie Lizenzketten unterstützt, muss der Server entscheiden, ob eine Leaf-Lizenz, eine Root-Lizenz oder beides ausgegeben werden soll. Um festzustellen, welche Art von Lizenz eine Richtlinie unterstützt, verwenden Sie `Policy.getLicenseChainType()` oder rufen Sie `Policy.getRootLicenseId()` auf, um zu ermitteln, ob die Richtlinie über eine Stammlizenz verfügt. Bei der Verkettung von Adobe Access 2.0-Lizenzen stellt der Server in der Regel eine Laublizenz aus, wenn er zum ersten Mal eine Lizenz für einen bestimmten Rechner und danach eine Root-Lizenz anfordert. Rufen Sie `LicenseRequestMessage.clientHasLeafForPolicy()` auf, um festzustellen, ob auf dem Computer bereits eine Laublizenz für die angegebene Richtlinie vorhanden ist.
