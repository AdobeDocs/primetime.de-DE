---
description: Eine Anzeige kann mehrere kreative Elemente enthalten, von denen eines für die Wiedergabe ausgewählt ist.
title: Gültige Mime-Typen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# Gültige MIME-Typen{#valid-mime-types}

Eine Anzeige kann mehrere kreative Elemente enthalten, von denen eines für die Wiedergabe ausgewählt ist.

Bei Mime-Typen können Sie angeben, welcher kreative Typ von Benutzern priorisiert werden kann. Anhand der von Benutzern angegebenen Mime-Typen und der Mime-Typen, die von Browser TVSDK unterstützt werden, wird bestimmt, welche kreativen Elemente priorisiert werden.

So legen Sie die gültigen MIME-Typen in Browser TVSDK fest:

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

wobei `mimeTypes` ein Array von Strings ist und jede Zeichenfolge einen Mime-Typ darstellt.

Wenn mehrere Mediendateien für eine Anzeige zurückgegeben werden, hängt die Auswahl von der Reihenfolge ab, in der die Mediendateien im `validMimeTypes`-Array angezeigt werden. Die Mime-Typen mit niedrigerem Index erhalten eine Präferenz gegenüber den Mime-Typen mit höherem Index.
