---
title: Automatische Wiedergabe in iOS
description: Automatische Wiedergabe in iOS
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Automatische Wiedergabe in iOS{#autoplay-on-ios}

Die Implementierung der Volume-API von AdobePSDK.MediaPlayer ermöglicht die automatische Wiedergabe von Inhalten auf Geräten mit iOS-Version 10 oder höher. iOS ermöglicht die automatische Wiedergabe nur, wenn das Volumen stummgeschaltet ist. Wenn die Lautstärke auf null gesetzt ist, setzt die API die `muted` -Eigenschaft des Video-Tags zu `true`, andernfalls `muted` -Eigenschaft auf `false`. Die `play` API startet die Wiedergabe ohne Benutzerinteraktion oder Benutzergeste.

Legen Sie für die automatische Wiedergabe in iPhone zusätzlich die `playsInline` -Eigenschaft der `video` Tag in `true`.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>Verwendung von `playsInline` -Eigenschaft startet die Wiedergabe ohne den Vollbildmodus.
