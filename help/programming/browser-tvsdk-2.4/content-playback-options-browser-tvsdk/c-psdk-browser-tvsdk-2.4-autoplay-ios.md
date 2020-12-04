---
description: 'null'
seo-description: 'null'
seo-title: Automatische Wiedergabe unter iOS
title: Automatische Wiedergabe unter iOS
uuid: d15bad24-be50-49e5-90f4-68dbda96fb6d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Automatische Wiedergabe unter iOS{#autoplay-on-ios}

Die Implementierung der Volume-API von AdobePSDK.MediaPlayer ermöglicht die automatische Wiedergabe von Inhalten auf Geräten mit iOS Version 10 oder höher. iOS erlaubt die automatische Wiedergabe nur, wenn die Lautstärke stummgeschaltet ist. Wenn die Lautstärke auf null eingestellt ist, setzt die API die `muted`-Eigenschaft des Video-Tags auf `true`, andernfalls wird `muted`-Eigenschaft auf `false` eingestellt. Die `play`-API Beginn die Wiedergabe ohne Benutzerinteraktion oder Benutzergeste.

Legen Sie für die automatische Wiedergabe auf dem iPhone zusätzlich die `playsInline`-Eigenschaft des `video`-Tags auf `true` fest.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>Die Verwendung der Eigenschaft `playsInline` Beginn die Wiedergabe ohne Vollbildmodus.

