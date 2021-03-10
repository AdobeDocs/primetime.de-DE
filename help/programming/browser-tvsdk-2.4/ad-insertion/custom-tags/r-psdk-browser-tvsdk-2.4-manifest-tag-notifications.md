---
description: Die MediaPlayerItem.timedMetadata-Eigenschaft bietet Zugriff auf alle TimedMetadata-Objekte, die aus den Tags "playlist/manifest"oder aus ID3-Tags im Medienstream erstellt werden.
title: Benachrichtigungen für Manifesttags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Benachrichtigungen für Manifesttags{#notifications-for-manifest-tags}

Die MediaPlayerItem.timedMetadata-Eigenschaft bietet Zugriff auf alle TimedMetadata-Objekte, die aus den Tags &quot;playlist/manifest&quot;oder aus ID3-Tags im Medienstream erstellt werden.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

Die `MediaPlayerItem.hasTimedMetadata`-Eigenschaft gibt an, ob ein abonniertes benutzerdefiniertes Tag im aktuellen Medium vorhanden ist. Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf das `Events.TimedMetadataEvent` achten, das die MediaPlayer-Instanz jedes Mal auslöst, wenn ein neues `TimedMetadata`-Objekt erstellt wird.
