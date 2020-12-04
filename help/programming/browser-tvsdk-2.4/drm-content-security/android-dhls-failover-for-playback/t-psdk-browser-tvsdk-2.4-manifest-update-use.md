---
description: Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.
seo-description: Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.
seo-title: Live-Übergeordnet-Manifest-Update verwenden
title: Live-Übergeordnet-Manifest-Update verwenden
uuid: 4ec665ab-b7ce-4a45-a251-13a07eb4d789
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# Live-Übergeordnet-Manifest-Update verwenden{#use-live-master-manifest-update}

Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.

1. Um Live-Übergeordnet-Manifest-Updates zu aktivieren, legen Sie die Aktualisierungshäufigkeit (in Minuten) fest, indem Sie die Eigenschaft `NetworkConfiguration.masterUpdateInterval` festlegen.
1. Optional können Sie erfolgreiche Manifestaktualisierungen verfolgen, indem Sie nach dem Ereignis `MediaPlayerItemEvent.MASTER_UPDATED` suchen.
