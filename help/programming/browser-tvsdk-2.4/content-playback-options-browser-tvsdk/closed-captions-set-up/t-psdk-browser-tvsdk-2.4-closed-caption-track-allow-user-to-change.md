---
description: Im Folgenden finden Sie ein Beispiel dafür, wie ein Benutzer eine Verfolgung mit geschlossener Beschriftung auswählen kann.
title: Benutzer können die Verfolgung ändern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---

# Benutzer können die Verfolgung ändern{#allow-the-user-to-change-the-track}

Im Folgenden finden Sie ein Beispiel dafür, wie ein Benutzer eine Verfolgung mit geschlossener Beschriftung auswählen kann.

1. Um die verfügbaren Untertitelspuren anzuzeigen, verwenden Sie die `MediaPlayerItem.closedCaptionsTracks` -Eigenschaft.

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. Um festzulegen, welche Untertitelspur aktuell ist, verwenden Sie die `MediaPlayerItem.selectClosedCaptionsTrack` -Methode.
1. Nachdem das Medienplayer-Element vorbereitet wurde, rufen Sie es mithilfe der ` MediaPlayer.  currentItem ` -Methode.

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```
