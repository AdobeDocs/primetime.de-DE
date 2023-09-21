---
description: Browser TVSDK unterstützt derzeit die Wiedergabe von Streams, in denen Manifeste und Fragmente keine Erweiterungen enthalten.
title: Erweiterungslose Streams
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Erweiterungslose Streams{#extensionless-streams}

Browser TVSDK unterstützt derzeit die Wiedergabe von Streams, in denen Manifeste und Fragmente keine Erweiterungen enthalten.

## Fragmentebene {#section_0E035129501D4A77BBC14192D8A53A86}

Browser TVSDK analysiert die ersten Byte der Antwort, um den Inhaltstyp von extensionlosen Fragmenten zu erkennen. Wenn kein gültiger Inhaltstyp erkannt wird, gibt Browser TVSDK einen Fehler aus.

## Manifestebene {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

Browser TVSDK verwendet die `mediaResource.resourceType` -Parameter, der im `replaceCurrentResource` -Methode, um den Inhaltstyp der Manifest-URL zu erkennen. Weitere Informationen finden Sie unter `AdobePSDK.MediaPlayer` -Klasse.

Im UI Framework-Player können Sie den Ressourcentyp in der Medienressource wie folgt angeben:

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

Wenn `resourceType` nicht angegeben ist, bestimmt das UI Framework den Ressourcentyp aus der Ressource-URL-Erweiterung, die dann an `replaceCurrentResource` -Methode.

>[!TIP]
>
>Stellen Sie für ein Manifest ohne Erweiterung sicher, dass `resourceType` beim Laden einer Ressource im UI-Framework immer übergeben wird.
