---
title: Verbesserte Lizenzketten
description: Verbesserte Lizenzketten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Verbesserte Lizenzketten {#enhanced-license-chaining}

Wenn eine DRM-Richtlinie verwendet wird, um eine Lizenz zu generieren, die Lizenzketten unterstützt, muss der Server entscheiden, ob er eine Leaf-Lizenz, eine Root-Lizenz oder beides ausstellt. Wenn Sie feststellen möchten, welche Art von Lizenz eine DRM-Richtlinie unterstützt, müssen Sie `Policy.getLicenseChainType()`oder Aufruf `Policy.getRootLicenseId()` um festzustellen, ob die DRM-Richtlinie über eine Stammlizenz verfügt. Mit der Adobe Primetime DRM 2.0-Lizenzverkettung stellt der Server normalerweise eine Laublizenz aus, wenn ein Benutzer danach zum ersten Mal eine Lizenz für einen bestimmten Computer und eine Root-Lizenz anfordert. Wenn Sie feststellen möchten, ob der Computer bereits über eine Laublizenz für die angegebene Richtlinie verfügt, müssen Sie `LicenseRequestMessage.clientHasLeafForPolicy()`.

Aufgrund der verbesserten Lizenzketten in Adobe Primetime DRM 3.0 wird empfohlen, beim ersten Anfordern einer Lizenz für einen bestimmten Computer sowohl ein Leaf als auch einen Root auszustellen. Wenn der Benutzer bereits über die Root-Lizenz verfügt, kann der Server nur ein Leaf ausstellen (Aufruf `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` , um zu ermitteln, ob der Client bereits über einen 3.0-erweiterten Stamm verfügt. Bei nachfolgenden Lizenzanfragen weist der Client dann darauf hin, dass er bereits über ein Leaf und einen Root verfügt. Daher sollte der Server eine neue Root-Lizenz ausstellen. Wenn die erweiterte Lizenzkachel verwendet wird `setRootKeyRetrievalInfo()` muss aufgerufen werden, um die Anmeldeinformationen bereitzustellen, die zum Entschlüsseln des Root-Verschlüsselungsschlüssels in der DRM-Richtlinie erforderlich sind.

>[!NOTE]
>
>Wenn die Richtlinie 3.0 Enhanced License Verketten unterstützt, der Client jedoch Primetime DRM 2.0 ist, gibt der Server eine 2.0-Originallizenz für verkettete Lizenzen aus. Verwenden Sie zum Bestimmen der Clientversion die `LicenseRequestMessage.getClientVersion()`.
