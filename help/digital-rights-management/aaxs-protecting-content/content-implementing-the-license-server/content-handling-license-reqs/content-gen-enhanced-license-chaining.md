---
seo-title: Erweiterte Lizenzketten
title: Erweiterte Lizenzketten
uuid: dc0e0a46-d3cd-44e8-a45d-3e22787be44e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Erweiterte Lizenzketten {#enhanced-license-chaining}

Aufgrund der verbesserten Lizenzverkettung in Adobe Access 3.0 wird empfohlen, beim ersten Anfordern einer Lizenz für einen bestimmten Computer sowohl ein Leaf- als auch ein Root-System auszustellen. Wenn der Benutzer bereits über eine Root-Lizenz verfügt, kann der Server nur ein Leaf ausstellen (Aufruf `LicenseRequestMessage.clientHasEnhancedRootForPolicy()`, um zu ermitteln, ob der Client bereits über einen 3.0-Erweiterten Stammordner verfügt). Bei nachfolgenden Lizenzanforderungen weist der Client darauf hin, dass er bereits über einen Leaf und einen Stamm verfügt. Daher sollte der Server eine neue Root-Lizenz ausstellen. Wenn die erweiterte Lizenzverkettung verwendet wird, muss `setRootKeyRetrievalInfo()` aufgerufen werden, um die Anmeldeinformationen bereitzustellen, die zum Entschlüsseln des Stamm-Verschlüsselungsschlüssels in der Richtlinie erforderlich sind.

>[!NOTE]
>
>Wenn die Richtlinie die erweiterte Lizenzketten von 3.0 unterstützt, der Client jedoch Adobe Access 2.0 ist, stellt der Server eine 2.0-Originallizenz aus. Verwenden Sie zur Bestimmung der Clientversion LicenseRequestMessage.getClientVersion().

