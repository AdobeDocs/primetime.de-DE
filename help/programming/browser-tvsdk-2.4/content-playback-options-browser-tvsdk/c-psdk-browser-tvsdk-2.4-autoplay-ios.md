---
title: Automatische Wiedergabe unter iOS
description: Automatische Wiedergabe unter iOS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '93'
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

