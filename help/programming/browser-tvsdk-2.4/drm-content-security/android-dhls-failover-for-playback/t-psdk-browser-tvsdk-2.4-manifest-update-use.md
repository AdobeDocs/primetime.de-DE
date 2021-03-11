---
description: Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.
title: Live-Übergeordnet-Manifest-Update verwenden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---


# Live-Übergeordnet-Manifest-Update verwenden{#use-live-master-manifest-update}

Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.

1. Um Live-Übergeordnet-Manifest-Updates zu aktivieren, legen Sie die Aktualisierungshäufigkeit (in Minuten) fest, indem Sie die Eigenschaft `NetworkConfiguration.masterUpdateInterval` festlegen.
1. Optional können Sie erfolgreiche Manifestaktualisierungen verfolgen, indem Sie nach dem Ereignis `MediaPlayerItemEvent.MASTER_UPDATED` suchen.
