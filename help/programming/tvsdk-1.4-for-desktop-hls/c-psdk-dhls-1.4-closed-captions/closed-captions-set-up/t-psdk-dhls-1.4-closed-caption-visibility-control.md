---
description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
seo-description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
seo-title: Sichtbarkeit von Bildunterschriften steuern
title: Sichtbarkeit von Bildunterschriften steuern
uuid: 360d1158-67d9-40d9-b4b6-8ef46f9d73c0
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Sichtbarkeit von Bildunterschriften steuern{#control-closed-caption-visibility}

Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.

>[!TIP]
>
>Wenn Untertiteltext angezeigt wird, wenn der Player in den Suchmodus wechselt, wird der Text nach Abschluss der Suche nicht mehr angezeigt. Stattdessen zeigt TVSDK nach einigen Sekunden den nächsten Untertiteltext im Video nach der Endsuchposition an.

>[!NOTE]
>
>Die Sichtbarkeitswerte für Untertitel werden in `ClosedCaptionsVisibility`definiert. >
>
```>
>public static const HIDDEN:String = hidden; 
>public static const VISIBLE:String = visible;
>```>



1. Warten Sie, bis der Status &quot;VORBEREITET&quot; `MediaPlayer` mindestens vorliegt (siehe [Warten auf einen gültigen Status](../../t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-ui-configure/t-psdk-dhls-1.4-ui-state-prepared-wait-for.md)).
1. Um die aktuelle Sichtbarkeitseinstellung für Untertitel abzurufen, verwenden Sie die get-Methode in `MediaPlayer`, die einen Sichtbarkeitswert zurückgibt.

   ```
   public function get ccVisibility():String
   ```

1. Um die Sichtbarkeit für Untertitel zu ändern, verwenden Sie die Setter-Methode und übergeben Sie einen Sichtbarkeitswert von `ClosedCaptionsVisibility`.

   Beispiel:

   ```
   public function set ccVisibility(value:String):void
   ```

1. Definieren Sie eine Dropdown-Liste.

   ```
   <s:DropDownList id="ccTracksList" width="85" 
                   dataProvider="{_ccTracks}" 
                   change="onCCTrackChange(event)" 
                   prompt="CC"/>
   ```

1. Definieren Sie ein bindbares Array mit Untertitelspuren.

   ```
   [Bindable] private var _ccTracks:ArrayCollection =  
     new ArrayCollection(); // active tracks 
   ```

1. Richten Sie Listener ein.

   ```
   player.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.addEventListener(MediaPlayerItemEvent.CAPTIONS_UPDATED, onCaptionUpdated);
   ```

   So entfernen Sie die Listener aus Ihrem Zerstörungscode:

   ```
   player.removeEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.removeEventListener(MediaPlayerItemEvent.CAPTIONS_UPDATED, onCaptionUpdated);
   ```

1. Erstellen und aktualisieren Sie die Liste, wenn ein Benutzer eine Auswahl aus der Liste trifft.

   ```
   private function onCCTrackChange(event:IndexChangeEvent):void { 
       var ccTrackIndex:int = event.newIndex; 
       var ccTracks:Vector.<ClosedCaptionsTrack> =  
         _player.currentItem.closedCaptionsTracks; 
       if (ccTrackIndex == 0) { 
           _player.ccVisibility = MediaPlayer.INVISIBLE; 
       } 
       else if (ccTrackIndex <= _ccTracks.length) { 
           var index:Number = findFromActiveIndex(ccTracks, ccTrackIndex - 1); 
           _player.currentItem.selectClosedCaptionsTrack(ccTracks[index]); 
           _player.ccVisibility = MediaPlayer.VISIBLE; 
       } 
   } 
   
   private function findFromActiveIndex(ccTracks:Vector.<ClosedCaptionsTrack>,  
     ccTrackIndex:int):Number { 
       var count:Number = 0; 
       for each (var ccTrack:ClosedCaptionsTrack in ccTracks) { 
           if (count < ccTrackIndex) 
               count = count + 1; 
           else 
               return count; 
       } 
       return -1; 
   } 
   
   private function onItemCreated(event:MediaPlayerItemEvent):void { 
       ... (you are likely to need more code here for other reasons) 
       updateCCTracks(_player.currentItem.closedCaptionsTracks); 
   } 
   
   private function onCaptionUpdated(event:MediaPlayerItemEvent):void { 
       ... (you are likely to need more code here for other reasons) 
       updateCCTracks(_player.currentItem.closedCaptionsTracks,  
                     (_player.ccVisibility == MediaPlayer.VISIBLE) ?  
                      _player.currentItem.selectedClosedCaptionsTrack : null); 
   } 
   
   private function updateCCTracks(tracks:Vector.<ClosedCaptionsTrack>,  
     selectedTrack:ClosedCaptionsTrack = null):void { 
       _ccTracks.removeAll(); 
   
       _ccTracks.addItem( 
           { 
               "label": "CC off", 
               "data": "cc-off" 
           } 
       ); 
   
       var selectedIndex:int = 0; 
       for each (var ccTrack:ClosedCaptionsTrack in tracks) { 
           _ccTracks.addItem( 
               { 
                   "label": ccTrack.name, 
                   "data": ccTrack.name 
               } 
           ); 
           if (selectedTrack && ccTrack.name == selectedTrack.name && 
           ccTrack.language == selectedTrack.language && 
           ccTrack.serviceType == selectedTrack.serviceType) { 
               selectedIndex = _ccTracks.length - 1; 
           } 
       } 
   
       var hasCC:Boolean = _ccTracks.length > 0; 
       ccTracksList.enabled = hasCC; 
       ccTracksList.mouseEnabled = hasCC; 
       ccTracksList.selectedIndex = selectedIndex; 
   } 
   ```

