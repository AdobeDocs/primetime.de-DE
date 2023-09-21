---
title: Verbesserte Lizenzketten
description: Verbesserte Lizenzketten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Verbesserte Lizenzketten {#enhanced-license-chaining}

Aufgrund der verbesserten Lizenzketten in Adobe Access 3.0 wird empfohlen, beim ersten Anfordern einer Lizenz für einen bestimmten Computer sowohl ein Leaf als auch einen Root auszustellen. Wenn der Benutzer bereits über die Root-Lizenz verfügt, kann der Server nur ein Leaf ausstellen (Aufruf `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` , um zu ermitteln, ob der Client bereits über einen 3.0-erweiterten Stamm verfügt. Für nachfolgende Lizenzanfragen weist der Client darauf hin, dass er bereits über ein Leaf und einen Root verfügt. Daher sollte der Server eine neue Root-Lizenz ausstellen. Wenn die erweiterte Lizenzkachel verwendet wird `setRootKeyRetrievalInfo()` muss aufgerufen werden, um die Anmeldeinformationen bereitzustellen, die zum Entschlüsseln des Root-Verschlüsselungsschlüssels in der Richtlinie erforderlich sind.

>[!NOTE]
>
>Wenn die Richtlinie 3.0 Enhanced License Verketten unterstützt, der Client jedoch Adobe Access 2.0 ist, stellt der Server eine 2.0-Originallizenz für verkettete Lizenzen aus. Verwenden Sie LicenseRequestMessage.getClientVersion(), um die Client-Version zu bestimmen.
