---
description: Mit der MediaPlayerItem.timedMetadata-Eigenschaft haben Sie Zugriff auf alle TimedMetadata-Objekte, die aus den Tags "playlist/manifest"oder aus ID3-Tags im Medienstream erstellt wurden. Die MediaPlayerItem.hasTimedMetadata-Eigenschaft gibt an, ob ein abonniertes benutzerdefiniertes Tag im aktuellen Medium vorhanden ist.
title: Benachrichtigungen für Manifesttags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Benachrichtigungen für Manifesttags{#notifications-for-manifest-tags}

Mit der MediaPlayerItem.timedMetadata-Eigenschaft haben Sie Zugriff auf alle TimedMetadata-Objekte, die aus den Tags &quot;playlist/manifest&quot;oder aus ID3-Tags im Medienstream erstellt wurden. Die MediaPlayerItem.hasTimedMetadata-Eigenschaft gibt an, ob ein abonniertes benutzerdefiniertes Tag im aktuellen Medium vorhanden ist.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die folgenden Ereignis achten, die Ihre Anwendung über die zugehörige Aktivität informieren:

* `MediaPlayerItemEvent.ITEM_CREATED`: Die anfängliche Liste von  `TimedMetadata` Objekten ist verfügbar, nachdem die erstellt  `MediaPlayerItem` wurde. Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Bei Live-/linearen Streams, bei denen die Manifest-/Wiedergabeliste regelmäßig aktualisiert wird, können in der aktualisierten Wiedergabeliste/dem Manifest zusätzliche benutzerdefinierte Tags angezeigt werden, sodass der  `MediaPlayerItem.timedMetadata` Eigenschaft möglicherweise zusätzliche TimedMetadata-Objekte hinzugefügt werden. Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Jedes Mal, wenn ein neues  `TimedMetadata` Objekt erstellt wird, wird dieses Ereignis vom  `MediaPlayer`Objekt abgesetzt. Dieses Ereignis wird nicht für das `TimedMetadata`-Objekt ausgelöst, das während der Initialisierungsphase erstellt wurde.

