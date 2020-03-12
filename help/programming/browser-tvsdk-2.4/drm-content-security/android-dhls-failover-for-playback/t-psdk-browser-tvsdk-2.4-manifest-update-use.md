---
description: Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.
seo-description: Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.
seo-title: Live-Master-Manifestaktualisierung verwenden
title: Live-Master-Manifestaktualisierung verwenden
uuid: 4ec665ab-b7ce-4a45-a251-13a07eb4d789
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Live-Master-Manifestaktualisierung verwenden{#use-live-master-manifest-update}

Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.

1. Um Live-Master-Manifestaktualisierungen zu aktivieren, legen Sie die Aktualisierungshäufigkeit (in Minuten) fest, indem Sie die `NetworkConfiguration.masterUpdateInterval` Eigenschaft festlegen.
1. Optional können Sie erfolgreiche Manifestaktualisierungen verfolgen, indem Sie auf das `MediaPlayerItemEvent.MASTER_UPDATED` Ereignis warten.
