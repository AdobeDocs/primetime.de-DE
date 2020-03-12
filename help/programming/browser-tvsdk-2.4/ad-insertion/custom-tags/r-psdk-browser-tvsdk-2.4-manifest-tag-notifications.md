---
description: Die MediaPlayerItem.timedMetadata-Eigenschaft bietet Zugriff auf alle TimedMetadata-Objekte, die aus den Tags "playlist/manifest"oder aus ID3-Tags im Medienstream erstellt werden.
seo-description: Die MediaPlayerItem.timedMetadata-Eigenschaft bietet Zugriff auf alle TimedMetadata-Objekte, die aus den Tags "playlist/manifest"oder aus ID3-Tags im Medienstream erstellt werden.
seo-title: Benachrichtigungen für Manifesttags
title: Benachrichtigungen für Manifesttags
uuid: 50727455-b37b-4e39-8efb-a97de3164074
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Benachrichtigungen für Manifesttags{#notifications-for-manifest-tags}

Die MediaPlayerItem.timedMetadata-Eigenschaft bietet Zugriff auf alle TimedMetadata-Objekte, die aus den Tags &quot;playlist/manifest&quot;oder aus ID3-Tags im Medienstream erstellt werden.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

Die `MediaPlayerItem.hasTimedMetadata` Eigenschaft gibt an, ob ein abonniertes benutzerdefiniertes Tag im aktuellen Medium vorhanden ist. Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die Daten warten, `Events.TimedMetadataEvent`die die MediaPlayer-Instanz jedes Mal auslöst, wenn ein neues `TimedMetadata` Objekt erstellt wird.
