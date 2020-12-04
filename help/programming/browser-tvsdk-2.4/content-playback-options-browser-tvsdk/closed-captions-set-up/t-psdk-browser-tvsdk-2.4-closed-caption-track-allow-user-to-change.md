---
description: Im Folgenden finden Sie ein Beispiel dafür, wie ein Benutzer eine Untertitel-Spur auswählen kann.
seo-description: Im Folgenden finden Sie ein Beispiel dafür, wie ein Benutzer eine Untertitel-Spur auswählen kann.
seo-title: Benutzer können die Verfolgung ändern
title: Benutzer können die Verfolgung ändern
uuid: bd3d4d20-9b52-4365-b656-83ec2a405a1c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '97'
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

