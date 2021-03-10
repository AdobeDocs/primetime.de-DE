---
description: Im Folgenden finden Sie ein Beispiel dafür, wie ein Benutzer eine Untertitel-Spur auswählen kann.
title: Benutzer können die Verfolgung ändern
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# Dem Benutzer das Ändern der Spur{#allow-the-user-to-change-the-track} erlauben

Im Folgenden finden Sie ein Beispiel dafür, wie ein Benutzer eine Untertitel-Spur auswählen kann.

1. Um die verfügbaren Untertitelspuren anzuzeigen, verwenden Sie die Eigenschaft `MediaPlayerItem.closedCaptionsTracks`.

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. Um festzulegen, welche Untertitel-Spur aktuell ist, verwenden Sie die `MediaPlayerItem.selectClosedCaptionsTrack`-Methode.
1. Nachdem das Medienplayer-Element vorbereitet wurde, rufen Sie es mit der ` MediaPlayer.  currentItem `-Methode vom Medienplayer ab.

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```

