---
description: Die MediaPlayerItem.timedMetadata -Eigenschaft bietet Zugriff auf alle TimedMetadata -Objekte, die aus den Wiedergabelisten/Manifesttags oder aus ID3-Tags im Medienstream erstellt werden.
title: Benachrichtigungen für Manifesttags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Benachrichtigungen für Manifesttags{#notifications-for-manifest-tags}

Die MediaPlayerItem.timedMetadata -Eigenschaft bietet Zugriff auf alle TimedMetadata -Objekte, die aus den Wiedergabelisten/Manifesttags oder aus ID3-Tags im Medienstream erstellt werden.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

Die `MediaPlayerItem.hasTimedMetadata` -Eigenschaft gibt an, ob ein abonniertes benutzerdefiniertes Tag im aktuellen Medium vorhanden ist. Sie können zeitgesteuerte Metadaten überwachen, indem Sie auf die `Events.TimedMetadataEvent`, die von der MediaPlayer-Instanz jedes Mal ausgelöst wird, wenn eine neue `TimedMetadata` -Objekt erstellt.
