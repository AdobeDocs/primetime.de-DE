---
title: Erstellen eines einfachen Players mithilfe des UI Framework
description: Erstellen eines einfachen Players mithilfe des UI Framework
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# Erstellen eines einfachen Players mithilfe des UI Framework{#create-a-basic-player-using-the-ui-framework}

So erstellen Sie einen einfachen Player mit dem UI Framework:

1. Erstellen Sie eine `<div>` für Ihre Player-Instanz.

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

   Wenn der Player erstellt wird, wird die angegebene `<div>` -Element erhält eine CSS-Klasse von `ptp-main-video-div-style`. Das resultierende DOM sieht ungefähr so aus:

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <video class="vp-video-element"></video> 
   </div>
   ```

1. Fügen Sie ein UI-Steuerelement hinzu.

   Fügen Sie beispielsweise eine Steuerleiste hinzu, die angezeigt wird, wenn Sie den Mauszeiger über den Player bewegen:

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

Das Objekt, das vom Aufrufen `ptp.videoPlayer()` bietet ein Verhalten, das die TVSDK-Medienplayer-API umbricht und eine programmgesteuerte Wiedergabe ermöglicht. Wenn Sie Aufrufe für die Medienplayer-Instanz ausführen, aktualisiert sich die Benutzeroberfläche selbst auf der Grundlage der vom Medienplayer ausgelösten Ereignisse:

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
