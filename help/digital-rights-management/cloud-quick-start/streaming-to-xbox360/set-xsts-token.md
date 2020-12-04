---
description: 'null'
seo-description: 'null'
seo-title: Festlegen des XSTS-Tokens im Player
title: Festlegen des XSTS-Tokens im Player
uuid: 8995e029-deee-4e23-9cda-a50de8c4f2c0
translation-type: tm+mt
source-git-commit: b7f52b71bde1d7bf59ef51d4f6f90dfaa07e347b
workflow-type: tm+mt
source-wordcount: '66'
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

