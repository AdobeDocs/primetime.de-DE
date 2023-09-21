---
description: Sie können diese Funktion aktivieren und auf zugehörige Ereignisse überprüfen.
title: Update des Live-Master-Manifests verwenden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---

# Update des Live-Master-Manifests verwenden{#use-live-master-manifest-update}

Sie können diese Funktion aktivieren und auf zugehörige Ereignisse überprüfen.

1. Um Aktualisierungen des Live-Master-Manifests zu aktivieren, legen Sie die Aktualisierungshäufigkeit (in Minuten) fest, indem Sie die `NetworkConfiguration.masterUpdateInterval` -Eigenschaft.
1. Optional können Sie erfolgreiche Manifestaktualisierungen verfolgen, indem Sie auf die `MediaPlayerItemEvent.MASTER_UPDATED` -Ereignis.
