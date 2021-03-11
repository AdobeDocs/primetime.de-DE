---
description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert wurde, wird die derzeit ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
title: Sichtbarkeit von Bildunterschriften steuern
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 1%

---


# Sichtbarkeit bei geschlossener Beschriftung {#control-closed-caption-visibility} steuern

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

1. Warten Sie, bis das `MediaPlayer` mindestens den Status &quot;VORBEREITET&quot;aufweist. Weitere Informationen finden Sie unter [Warten auf einen gültigen Status](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/ui-configure/android-3x-ui-state-prepared-wait-for.md).

1. Um die aktuelle Sichtbarkeitseinstellung für Untertitel abzurufen, verwenden Sie die get-Methode in `MediaPlayer`, die einen Sichtbarkeitswert zurückgibt.

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. Um die Sichtbarkeit von Untertiteln zu ändern, verwenden Sie die Setter-Methode und übergeben Sie einen Sichtbarkeitswert von `MediaPlayer.Visibility`.

   Beispiel:

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```
