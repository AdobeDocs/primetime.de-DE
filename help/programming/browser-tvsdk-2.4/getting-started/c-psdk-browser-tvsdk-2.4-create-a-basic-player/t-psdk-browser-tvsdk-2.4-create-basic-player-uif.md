---
description: 'null'
seo-description: 'null'
seo-title: Erstellen eines einfachen Players mit dem UI-Framework
title: Erstellen eines einfachen Players mit dem UI-Framework
uuid: d1a82dbb-1c05-4d0c-b6bc-e07cbede93cb
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 1%

---


# Erstellen eines einfachen Players mit dem UI-Framework{#create-a-basic-player-using-the-ui-framework}

So erstellen Sie einen einfachen Player mit dem UI-Framework:

1. Erstellen Sie ein `<div>` für Ihre Player-Instanz.

   Beispiel:

   ```
   <div id="video1" > 
    </div>
   ```

1. Laden Sie den Player.

   ```js
   <script> 
       (function(){ 
           var player = ptp.videoPlayer('#video1'); 
       })(); 
   </script>
   ```

   Wenn der Player erstellt wird, erhält das angegebene `<div>`-Element die CSS-Klasse `ptp-main-video-div-style`. Das resultierende DOM wird in etwa wie folgt angezeigt:

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <video class="vp-video-element"></video> 
   </div>
   ```

1. hinzufügen eines UI-Steuerelements.

   Fügen Sie beispielsweise eine Steuerleiste hinzu, die angezeigt wird, wenn der Mauszeiger über den Player bewegt wird:

   ```js
   <script> 
       (function(){ 
           function myControlBarBehavior(element, configuration, player) { 
               return ptp.controlBarBehavior(element, configuration, player); 
           } 
           var player = ptp.videoPlayer('#video1', { 
               controlBar: { 
                   behavior: myControlBarBehavior, 
                   classNames: 'ptp-control-bar my_control_bar' 
               } 
           }); 
       })(); 
   </script>
   ```

   Das resultierende DOM wird wie folgt angezeigt:

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <div class="ptp-control-bar my_control_bar"></div> 
       <video class="vp-video-element"></video> 
   </div>
   ```

Das Objekt, das vom Aufruf von `ptp.videoPlayer()` zurückgegeben wird, stellt ein Verhalten bereit, das die TVSDK-Medienplayer-API umschließt und eine programmgesteuerte Steuerung der Wiedergabe ermöglicht. Wenn Sie die Media Player-Instanz aufrufen, wird die Benutzeroberfläche auf der Grundlage der vom Medienplayer ausgelösten Ereignis aktualisiert:

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
