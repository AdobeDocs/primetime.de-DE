---
keywords: setSecure;VideoEngineView
title: Bildschirmaufnahme aktivieren
description: Bildschirmaufnahme aktivieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---


# Bildschirmerfassung aktivieren{#enable-screen-capture}

TVSDK deaktiviert standardmäßig die Bildschirmerfassung. Der Player ruft `setSecure(true)` zum Zeitpunkt der Konstruktion auf dem `com.adobe.ave.VideoEngineView`-Objekt auf. Sie haben Zugriff auf dieses Objekt, da Sie ein `VideoEngineView`-Objekt erstellen und es an das `VideoEngine`-Objekt übergeben müssen.

So aktivieren Sie die Bildschirmerfassung in Ihrer App:

1. Erstellen Sie das `com.adobe.ave.VideoEngineView`-Objekt.
1. Rufen Sie `setSecure(false)` für Ihr `VideoEngineView`-Objekt auf.
