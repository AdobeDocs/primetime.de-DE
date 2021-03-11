---
description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
title: Sichtbarkeit von Bildunterschriften steuern
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 1%

---


# Übersicht {#control-closed-caption-visibility}

Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.

>[!TIP]
>
>Wenn Untertiteltext angezeigt wird, wenn der Player in den Suchmodus wechselt, wird der Text nach Abschluss der Suche nicht mehr angezeigt. Stattdessen zeigt TVSDK nach einigen Sekunden den nächsten Untertiteltext im Video nach der Endsuchposition an.

>[!NOTE]
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

1. Warten Sie, bis der MediaPlayer mindestens den Status &quot;VORBEREITET&quot;aufweist (siehe [Warten Sie auf einen gültigen Status](../../../tvsdk-1.4-for-android/ui-configure/android-1.4-ui-state-prepared-wait-for.md)).
1. Um die aktuelle Sichtbarkeitseinstellung für Untertitel abzurufen, verwenden Sie die get-Methode in MediaPlayer, die einen Sichtbarkeitswert zurückgibt.

   ```java
   Visibility getCCVisibility() throws IllegalStateException;
   ```

1. Um die Sichtbarkeit von Untertiteln zu ändern, verwenden Sie die Setter-Methode und übergeben Sie einen Sichtbarkeitswert von `MediaPlayer.Visibility`.

   Beispiel:

   ```java
   mediaPlayer.setCCVisibility(Visibility.VISIBLE);
   ```

