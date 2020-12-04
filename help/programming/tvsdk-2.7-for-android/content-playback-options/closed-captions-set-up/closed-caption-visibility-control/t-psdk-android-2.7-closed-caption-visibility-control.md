---
description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert wurde, wird die derzeit ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
seo-description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert wurde, wird die derzeit ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
seo-title: Sichtbarkeit von Bildunterschriften steuern
title: Sichtbarkeit von Bildunterschriften steuern
uuid: b9d48d70-2554-4948-8654-fa45093c3782
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Übersicht {#control-closed-caption-visibility-overview}

Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert wurde, wird die derzeit ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.

>[!TIP]
>
>Wenn Untertiteltext angezeigt wird, wenn der Player in den Suchmodus wechselt, wird der Text nach Abschluss der Suche nicht mehr angezeigt. Stattdessen zeigt TVSDK nach einigen Sekunden den nächsten Untertiteltext im Video nach der Endsuchposition an.
>
>Die Sichtbarkeitswerte für Untertitel werden in `MediaPlayer.Visibility` definiert.
>
>
```java
>enum Visibility {  
>       VISIBLE,  
>       INVISIBLE 
>}
>```

1. Warten Sie, bis das `MediaPlayer` mindestens den Status &quot;VORBEREITET&quot;aufweist.

   Weitere Informationen finden Sie unter ui-state-prepare-wait-for .
1. Um die aktuelle Sichtbarkeitseinstellung für Untertitel abzurufen, verwenden Sie die get-Methode in `MediaPlayer`, die einen Sichtbarkeitswert zurückgibt.

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. Um die Sichtbarkeit von Untertiteln zu ändern, verwenden Sie die Setter-Methode und übergeben Sie einen Sichtbarkeitswert von `MediaPlayer.Visibility`.

   Beispiel:

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```

