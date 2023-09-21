---
description: Eine Anzeige kann über mehrere kreative Elemente verfügen, von denen eine ausgewählt wird, um wiedergegeben zu werden.
title: Gültige MIME-Typen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Gültige MIME-Typen{#valid-mime-types}

Eine Anzeige kann über mehrere kreative Elemente verfügen, von denen eine ausgewählt wird, um wiedergegeben zu werden.

Bei MIME-Typen können Sie festlegen, welche kreativen Typen Benutzer priorisieren können. Anhand der von Benutzern angegebenen MIME-Typen und der MIME-Typen, die vom Browser TVSDK unterstützt werden, wird bestimmt, welche kreativen Inhalte priorisiert werden.

So legen Sie gültige MIME-Typen in Browser TVSDK fest:

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

where `mimeTypes` ist ein Array von Zeichenfolgen, und jede Zeichenfolge stellt einen MIME-Typ dar.

Wenn für eine Anzeige mehrere Mediendateien zurückgegeben werden, hängt die Auswahl von der Reihenfolge ab, in der die Mediendateien in `validMimeTypes` Array. Die MIME-Typen mit niedrigerem Index erhalten eine Voreinstellung gegenüber den MIME-Typen mit höherem Index.
