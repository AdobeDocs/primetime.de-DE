---
description: Sie können das Format festlegen, z. B. Schriftart, Größe, Farbe, Kante und Deckkraft für Text mit geschlossener Beschriftung.
title: Festlegen von Stilen für Untertitel
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Festlegen von Stilen für Untertitel{#set-closed-caption-styles}

Sie können das Format festlegen, z. B. Schriftart, Größe, Farbe, Kante und Deckkraft für Text mit geschlossener Beschriftung.

1. Warten Sie auf die `MediaPlayer` mindestens im Status VORBEREITET sein.

   Weitere Informationen zu den Status finden Sie unter [Auf gültigen Status warten](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md).
1. Erstellen Sie eine `TextFormat` -Instanz.

   Sie können jetzt alle Stilparameter für Beschriftungen bereitstellen oder sie später festlegen.

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

1. (Optional) Rufen Sie die aktuellen Einstellungen des Untertitelstils mit `MediaPlayer.ccStyle`.

   Der Rückgabewert ist eine Instanz der `TextFormat` -Schnittstelle.

   Wenn zuvor kein Stil festgelegt wurde, wird ein TextFormat-Objekt mit Standardwerten für jedes Attribut zurückgegeben:

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. Um die Stileinstellungen zu ändern, verwenden Sie `MediaPlayer.ccStyle`, wobei eine Instanz der `TextFormat` -Schnittstelle.

   Sie können diese Methode auch dann verwenden, wenn der aktuelle Medien-Stream keine Untertitel enthält.

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >Das Festlegen des Stils für geschlossene Beschriftungen ist asynchron, sodass es einige Sekunden dauern kann, bis die Änderungen auf dem Bildschirm angezeigt werden.
