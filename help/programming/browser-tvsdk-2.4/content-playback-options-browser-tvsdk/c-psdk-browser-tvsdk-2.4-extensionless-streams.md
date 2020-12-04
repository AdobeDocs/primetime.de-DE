---
description: Browser TVSDK unterstützt derzeit die Wiedergabe von Streams, in denen Manifeste und Fragmente keine Erweiterungen enthalten.
seo-description: Browser TVSDK unterstützt derzeit die Wiedergabe von Streams, in denen Manifeste und Fragmente keine Erweiterungen enthalten.
seo-title: Extreme Streams
title: Extreme Streams
uuid: c69ba62b-a940-4211-920d-2e559849fd6d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Extensionslose Streams{#extensionless-streams}

Browser TVSDK unterstützt derzeit die Wiedergabe von Streams, in denen Manifeste und Fragmente keine Erweiterungen enthalten.

## Fragmentstufe {#section_0E035129501D4A77BBC14192D8A53A86}

Browser TVSDK analysiert die ersten Byte der Antwort, um den Content-Typ der extensionfreien Fragmente zu ermitteln. Wenn kein gültiger Inhaltstyp erkannt wird, gibt Browser TVSDK einen Fehler aus.

## Manifeststufe {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

Browser TVSDK verwendet den Parameter `mediaResource.resourceType`, der in der `replaceCurrentResource`-Methode übergeben wird, um den Inhaltstyp der Manifest-URL zu erkennen. Weitere Informationen finden Sie unter der `AdobePSDK.MediaPlayer`-Klasse.

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

Wenn `resourceType` nicht angegeben ist, bestimmt das UI-Framework den Ressourcentyp aus der Ressourcen-URL-Erweiterung, der dann an die `replaceCurrentResource`-Methode übergeben wird.

>[!TIP]
>
>Stellen Sie bei erweiterungsfreiem Manifest sicher, dass `resourceType` immer weitergeleitet wird, während eine Ressource im UI-Framework geladen wird.

