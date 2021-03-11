---
description: Sie können das Format festlegen, z. B. Schriftart, Größe, Farbe, Kante und Deckkraft für Text mit geschlossener Beschriftung.
title: Stile für Untertitel festlegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Stile für Untertitel festlegen{#set-closed-caption-styles}

Sie können das Format festlegen, z. B. Schriftart, Größe, Farbe, Kante und Deckkraft für Text mit geschlossener Beschriftung.

1. Warten Sie, bis `MediaPlayer` mindestens im Status &quot;VORBEREITT&quot;ist.

   Weitere Informationen zu den Status finden Sie unter [Warten auf einen gültigen Status](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md).
1. Erstellen Sie eine `TextFormat`-Instanz.

   Sie können jetzt alle Formatierungsparameter für Bildunterschriften bereitstellen oder sie später festlegen.

   ```js
   new TextFormat( 
       font,   
       fontColor,  
       edgeColor,   
       fontEdge,  
       backgroundColor,   
       fillColor,  
       size,   
       fontOpacity,   
       backgroundOpacity,  
       fillOpacity, 
       bottomInset 
       safeArea) → {AdobePSDK.TextFormat}
   ```

1. (Optional) Rufen Sie die aktuellen Stileinstellungen für geschlossene Beschriftungen mit `MediaPlayer.ccStyle` ab.

   Der Rückgabewert ist eine Instanz der `TextFormat`-Schnittstelle.

   Wenn zuvor kein Stil festgelegt wurde, wird ein TextFormat-Objekt mit Standardwerten für jedes Attribut zurückgegeben:

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. Um die Stileinstellungen zu ändern, verwenden Sie `MediaPlayer.ccStyle` und übergeben Sie eine Instanz der `TextFormat`-Schnittstelle.

   Sie können diese Methode auch dann verwenden, wenn der aktuelle Medienstream keine Untertitel enthält.

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >Das Festlegen des Stils für die Bildunterschrift ist asynchron, sodass es einige Sekunden dauern kann, bis die Änderungen auf dem Bildschirm angezeigt werden.

