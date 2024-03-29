---
description: Sie können Schaltflächen einrichten, mit denen TVSDK-Methoden aufgerufen werden, um die Medien anzuhalten und wiederzugeben.
title: Schaltfläche "Wiedergabe/Pause"implementieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# Schaltfläche &quot;Wiedergabe/Pause&quot;implementieren {#implement-a-play-pause-button}

Sie können Schaltflächen einrichten, mit denen TVSDK-Methoden aufgerufen werden, um die Medien anzuhalten und wiederzugeben.

Verwenden Sie den folgenden Beispielcode, um eine Wiedergabe- oder Pause-Schaltfläche zu implementieren:

<!--<a id="example_BC2632D673FE451190A30A23145090D0"></a>-->

```
_playPauseButton =  
[[UIButton alloc] initWithFrame:CGRectMake(BUTTON_POS_X, BUTTON_POS_Y, BUTTON_SIZE_W, BUTTON_SIZE_H)]; 
[_playPauseButton setImage:[UIImage imageNamed:@"play.png"] forState:UIControlStateNormal];  
[_playPauseButton setImage:[UIImage imageNamed:@"pause.png"] forState:UIControlStateSelected]; 
[_playPauseButton addTarget:self action:@selector(playTouch:) forControlEvents:UIControlEventTouchUpInside]; 
[self addSubview:_playPauseButton]; 
 
... 
 
- (void)playTouch:(id)sender { 
    if (self.player.status == PTMediaPlayerStatusPlaying) { 
        _playPauseButton.selected = YES;  
        [self.player pause]; 
    } 
    else { 
        _playPauseButton.selected = NO; [self.player play]; 
    } 
} 
```
