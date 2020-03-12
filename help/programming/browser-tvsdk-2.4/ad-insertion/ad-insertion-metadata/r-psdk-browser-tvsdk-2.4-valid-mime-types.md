---
description: Eine Anzeige kann mehrere kreative Elemente enthalten, von denen eines für die Wiedergabe ausgewählt ist.
seo-description: Eine Anzeige kann mehrere kreative Elemente enthalten, von denen eines für die Wiedergabe ausgewählt ist.
seo-title: Gültige Mime-Typen
title: Gültige Mime-Typen
uuid: ab2baac9-a9ef-44f1-83a1-2e6e471e3231
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Gültige Mime-Typen{#valid-mime-types}

Eine Anzeige kann mehrere kreative Elemente enthalten, von denen eines für die Wiedergabe ausgewählt ist.

Bei Mime-Typen können Sie angeben, welcher kreative Typ von Benutzern priorisiert werden kann. Anhand der von Benutzern angegebenen Mime-Typen und der Mime-Typen, die von Browser TVSDK unterstützt werden, wird bestimmt, welche kreativen Elemente priorisiert werden.

So legen Sie die gültigen MIME-Typen in Browser TVSDK fest:

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

wobei `mimeTypes` es sich um ein Array von Strings handelt und jede Zeichenfolge einen Mime-Typ darstellt.

Werden mehrere Mediendateien für eine Anzeige zurückgegeben, hängt die Auswahl von der Reihenfolge ab, in der die Mediendateien im `validMimeTypes` Array angezeigt werden. Die Mime-Typen mit niedrigerem Index erhalten eine Präferenz gegenüber den Mime-Typen mit höherem Index.
