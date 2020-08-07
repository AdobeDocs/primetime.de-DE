---
seo-title: Erweiterte Lizenzketten
title: Erweiterte Lizenzketten
uuid: f869b4e7-4b24-4832-94a7-b7143567ab58
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Enhanced License Chaining {#enhanced-license-chaining}

Wenn eine DRM-Richtlinie zum Generieren einer Lizenz verwendet wird, die Lizenzketten unterstützt, muss der Server entscheiden, ob eine Leaf-Lizenz, eine Root-Lizenz oder beides ausgegeben werden soll. Wenn Sie bestimmen möchten, welche Art von Lizenz eine DRM-Richtlinie unterstützt, müssen Sie die DRM-Richtlinie mit einer Root-Lizenz verknüpfen `Policy.getLicenseChainType()`oder aufrufen, um festzustellen, ob die DRM-Richtlinie über eine Root-Lizenz verfügt. `Policy.getRootLicenseId()` Dies ist der Fall. Bei der Verkettung von Adobe Primetime DRM 2.0-Lizenzen stellt der Server in der Regel eine Laublizenz aus, wenn ein Benutzer danach zum ersten Mal eine Lizenz für einen bestimmten Computer und eine Root-Lizenz anfordert. Wenn Sie ermitteln möchten, ob auf dem Computer bereits eine Laublizenz für die angegebene Richtlinie vorhanden ist, müssen Sie `LicenseRequestMessage.clientHasLeafForPolicy()`einen Aufruf ausführen.

Aufgrund der verbesserten Lizenzketten in Adobe Primetime DRM 3.0 wird empfohlen, beim ersten Anfordern einer Lizenz für einen bestimmten Computer sowohl ein Leaf als auch einen Root auszustellen. Wenn der Benutzer bereits über eine Root-Lizenz verfügt, kann der Server nur ein Leaf ausgeben (Aufruf, um festzustellen, ob der Client bereits über einen 3.0-Erweiterten Stammordner verfügt). `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` Bei nachfolgenden Lizenzanforderungen weist der Client dann darauf hin, dass er bereits über einen Leaf und einen Stamm verfügt. Daher sollte der Server eine neue Root-Lizenz ausstellen. Wenn die erweiterte Lizenzkachel verwendet wird, `setRootKeyRetrievalInfo()` muss aufgerufen werden, um die Anmeldeinformationen bereitzustellen, die zum Entschlüsseln des Stamm-Verschlüsselungsschlüssels in der DRM-Richtlinie erforderlich sind.

>[!NOTE]
>
>Wenn die Richtlinie die erweiterte Lizenzketten von 3.0 unterstützt, der Client jedoch Primetime DRM 2.0 ist, gibt der Server eine ursprüngliche verkettete Lizenz von 2.0 aus. Verwenden Sie zur Bestimmung der Clientversion `LicenseRequestMessage.getClientVersion()`.

