---
description: Browser TVSDK unterstützt derzeit die Wiedergabe von Streams, in denen Manifeste und Fragmente keine Erweiterungen enthalten.
seo-description: Browser TVSDK unterstützt derzeit die Wiedergabe von Streams, in denen Manifeste und Fragmente keine Erweiterungen enthalten.
seo-title: Extreme Streams
title: Extreme Streams
uuid: c69ba62b-a940-4211-920d-2e559849fd6d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Extreme Streams{#extensionless-streams}

Browser TVSDK unterstützt derzeit die Wiedergabe von Streams, in denen Manifeste und Fragmente keine Erweiterungen enthalten.

## Fragmentebene {#section_0E035129501D4A77BBC14192D8A53A86}

Browser TVSDK analysiert die ersten Byte der Antwort, um den Content-Typ der extensionfreien Fragmente zu ermitteln. Wenn kein gültiger Inhaltstyp erkannt wird, gibt Browser TVSDK einen Fehler aus.

## Manifestebene {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

Browser TVSDK verwendet den `mediaResource.resourceType` Parameter, der in der `replaceCurrentResource` Methode übergeben wird, um den Content-Typ der Manifest-URL zu erkennen. Weitere Informationen finden Sie in der `AdobePSDK.MediaPlayer` Klasse.

Im UI-Framework-Player können Sie den Ressourcentyp in der Medienressource wie folgt angeben:

```js
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
  player: { 
    mediaResource: { 
      resourceUrl:'Specify Resource Url', 
      resourceType: ‘Specify Resource Type. Refer AdobePSDK.MediaResourceType' 
    } 
  } 
}); 
```

Wenn `resourceType` keine Angabe erfolgt, bestimmt das UI-Framework den Ressourcentyp aus der Ressource-URL-Erweiterung, die dann an die `replaceCurrentResource` Methode übergeben wird.

>[!TIP]
>
>Für ein erweiterungsfreies Manifest müssen Sie sicherstellen, dass beim Laden einer Ressource im UI-Framework immer weitergegeben `resourceType` wird.

