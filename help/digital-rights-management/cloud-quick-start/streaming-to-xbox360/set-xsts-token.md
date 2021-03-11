---
title: Festlegen des XSTS-Tokens im Player
description: Festlegen des XSTS-Tokens im Player
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---


# Festlegen des XSTS-Tokens im Player{#set-the-xsts-token-in-your-player}

In Xbox360 legen Sie das Token asynchron als Reaktion auf das `MediaPlayer.RequestKeyAttribute`-Ereignis fest.

Legen Sie das XSTS-Token fest.

Die mit Ihrer Software gebündelte Beispielanwendung zeigt, wie das XSTS-Token im Player festgelegt wird. Im Folgenden finden Sie den entsprechenden Codeausschnitt aus dem Beispielplayer:

```
   MediaPlayer mMediaPlayer;  
 
mMediaPlayer.RequestKeyAttribute += Player_RequestKeyAttribute;  
 
private void Player_RequestKeyAttribute(object sender, RequestKeyAttributeEventArgs args) {  
    string token = "";  
    // XBOX XSTS Token...  
    KeyAttribute keyAttribute = new KeyAttribute(System.Text.Encoding.UTF8.GetBytes(token), null);  
    mMediaPlayer.SetKeyAttribute(args.RequestIdentifier, keyAttribute);  
} 
```

