---
description: 'null'
keywords: setSecure;VideoEngineView
seo-description: 'null'
seo-title: Bildschirmaufnahme aktivieren
title: Bildschirmaufnahme aktivieren
uuid: f3d18729-e13e-47f9-b4b8-f93a2874ef16
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Bildschirmaufnahme aktivieren{#enable-screen-capture}

TVSDK deaktiviert standardmäßig die Bildschirmerfassung. Der Player ruft `setSecure(true)` das `com.adobe.ave.VideoEngineView` Objekt zur Bauzeit auf. Sie haben Zugriff auf dieses Objekt, da Sie ein `VideoEngineView` Objekt erstellen und es an das `VideoEngine` Objekt übergeben müssen.

So aktivieren Sie die Bildschirmerfassung in Ihrer App:

1. Erstellen Sie das `com.adobe.ave.VideoEngineView` Objekt.
1. Rufen Sie `setSecure(false)` Ihr `VideoEngineView` Objekt auf.
