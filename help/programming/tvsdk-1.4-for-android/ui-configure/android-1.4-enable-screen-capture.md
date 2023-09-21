---
keywords: setSecure;VideoEngineView
title: Aktivieren der Bildschirmaufzeichnung
description: Aktivieren der Bildschirmaufzeichnung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---

# Aktivieren der Bildschirmaufzeichnung{#enable-screen-capture}

TVSDK deaktiviert standardmäßig die Bildschirmaufzeichnung. Der Player ruft `setSecure(true)` auf `com.adobe.ave.VideoEngineView` Objekt während der Erstellung. Sie haben Zugriff auf dieses Objekt, da Sie eine `VideoEngineView` Objekt und versorgen Sie es mit dem `VideoEngine` -Objekt.

So aktivieren Sie die Bildschirmaufzeichnung in Ihrer App:

1. Erstellen Sie die `com.adobe.ave.VideoEngineView` -Objekt.
1. Aufruf `setSecure(false)` auf `VideoEngineView` -Objekt.
