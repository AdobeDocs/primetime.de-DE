---
seo-title: Enhanced License Chaining
title: Enhanced License Chaining
uuid: dc0e0a46-d3cd-44e8-a45d-3e22787be44e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Enhanced License Chaining {#enhanced-license-chaining}

Aufgrund der verbesserten Lizenzverkettung in Adobe Access 3.0 wird empfohlen, beim ersten Anfordern einer Lizenz für einen bestimmten Computer sowohl ein Leaf- als auch ein Root-System auszustellen. If the user already has the Root license, the server may issue only a Leaf (call `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` to determine if the client already has a 3.0 Enhanced Root). Bei nachfolgenden Lizenzanforderungen weist der Client darauf hin, dass er bereits über einen Leaf und einen Stamm verfügt. Daher sollte der Server eine neue Root-Lizenz ausstellen. Wenn die erweiterte Lizenzkachel verwendet wird, `setRootKeyRetrievalInfo()` muss aufgerufen werden, um die Anmeldeinformationen bereitzustellen, die zum Entschlüsseln des Stamm-Verschlüsselungsschlüssels in der Richtlinie erforderlich sind.

>[!NOTE]
>
>Wenn die Richtlinie die erweiterte Lizenzketten von 3.0 unterstützt, der Client jedoch Adobe Access 2.0 ist, stellt der Server eine 2.0-Originallizenz aus. Verwenden Sie zur Bestimmung der Clientversion LicenseRequestMessage.getClientVersion().

