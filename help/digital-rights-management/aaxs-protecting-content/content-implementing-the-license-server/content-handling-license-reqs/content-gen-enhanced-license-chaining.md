---
seo-title: Erweiterte Lizenzketten
title: Erweiterte Lizenzketten
uuid: dc0e0a46-d3cd-44e8-a45d-3e22787be44e
translation-type: tm+mt
source-git-commit: da8736769f7b47318dbd955aa854f83ae64d6d7b

---


# Erweiterte Lizenzketten {#enhanced-license-chaining}

Aufgrund der verbesserten Lizenzverkettung in Adobe Access 3.0 wird empfohlen, beim ersten Anfordern einer Lizenz für einen bestimmten Computer sowohl ein Leaf als auch einen Root auszustellen. Wenn der Benutzer bereits über eine Root-Lizenz verfügt, kann der Server nur ein Leaf ausgeben (Aufruf, um festzustellen, ob der Client bereits über einen 3.0-Erweiterten Stammordner verfügt). `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` Bei nachfolgenden Lizenzanforderungen weist der Client darauf hin, dass er bereits über einen Leaf und einen Stamm verfügt. Daher sollte der Server eine neue Root-Lizenz ausstellen. Wenn die erweiterte Lizenzkachel verwendet wird, `setRootKeyRetrievalInfo()` muss aufgerufen werden, um die Anmeldeinformationen bereitzustellen, die zum Entschlüsseln des Stamm-Verschlüsselungsschlüssels in der Richtlinie erforderlich sind.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Wenn die Richtlinie die erweiterte Lizenzketten für 3.0 unterstützt, der Client jedoch Adobe Access 2.0 ist, stellt der Server eine ursprüngliche verkettete Lizenz für 2.0 aus. Verwenden Sie zur Bestimmung der Clientversion LicenseRequestMessage.getClientVersion().

