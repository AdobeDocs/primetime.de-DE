---
title: Lizenzverkettung
description: Lizenzverkettung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Lizenzverkettung{#license-chaining}

Wenn die für die Lizenzgenerierung verwendete Richtlinie Lizenzketten unterstützt, muss der Server entscheiden, ob eine Leaf-Lizenz, eine Root-Lizenz oder beides ausgegeben wird. Um festzustellen, welche Art von Lizenz eine Richtlinie unterstützt, verwenden Sie `Policy.getLicenseChainType()`oder Aufruf `Policy.getRootLicenseId()` , um zu ermitteln, ob die Richtlinie über eine Stammlizenz verfügt. Mit der Lizenzketten von Adobe Access 2.0 gibt der Server in der Regel eine Laublizenz aus, wenn der Benutzer zum ersten Mal eine Lizenz für einen bestimmten Computer und anschließend eine Root-Lizenz anfordert. Rufen Sie auf, um festzustellen, ob der Computer bereits über eine Laublizenz für die angegebene Richtlinie verfügt `LicenseRequestMessage.clientHasLeafForPolicy()`.
