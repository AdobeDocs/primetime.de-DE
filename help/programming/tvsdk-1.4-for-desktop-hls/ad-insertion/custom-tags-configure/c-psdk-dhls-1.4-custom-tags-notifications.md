---
description: Mit der MediaPlayerItem.timedMetadata -Eigenschaft können Sie auf alle TimedMetadata -Objekte zugreifen, die aus den Wiedergabelisten/Manifesttags oder aus ID3-Tags im Medienstream erstellt wurden. Die MediaPlayerItem.hasTimedMetadata -Eigenschaft gibt an, ob ein abonniertes benutzerdefiniertes Tag im aktuellen Medium vorhanden ist.
title: Benachrichtigungen für Manifesttags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Benachrichtigungen für Manifesttags{#notifications-for-manifest-tags}

Mit der MediaPlayerItem.timedMetadata -Eigenschaft können Sie auf alle TimedMetadata -Objekte zugreifen, die aus den Wiedergabelisten/Manifesttags oder aus ID3-Tags im Medienstream erstellt wurden. Die MediaPlayerItem.hasTimedMetadata -Eigenschaft gibt an, ob ein abonniertes benutzerdefiniertes Tag im aktuellen Medium vorhanden ist.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die folgenden Ereignisse warten, die Ihre Anwendung über zugehörige Aktivitäten informieren:

* `MediaPlayerItemEvent.ITEM_CREATED`: Die erste Liste von `TimedMetadata` -Objekte sind verfügbar, nachdem `MediaPlayerItem` erstellt wird. Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Bei Live-/linearen Streams, bei denen das Manifest/die Wiedergabeliste regelmäßig aktualisiert wird, können zusätzliche benutzerdefinierte Tags in der aktualisierten Wiedergabeliste/dem aktualisierten Manifest angezeigt werden, sodass zusätzliche TimedMetadata-Objekte zum `MediaPlayerItem.timedMetadata` -Eigenschaft. Dieses Ereignis benachrichtigt Ihre Anwendung in diesem Fall.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Jedes Mal, wenn ein neuer `TimedMetadata` -Objekt erstellt wird, wird dieses Ereignis von der `MediaPlayer`. Dieses Ereignis wird nicht für die `TimedMetadata` -Objekt, das während der Initialisierungsphase erstellt wurde.
