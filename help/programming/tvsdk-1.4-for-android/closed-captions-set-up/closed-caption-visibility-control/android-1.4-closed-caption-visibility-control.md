---
description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
seo-description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt. Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
seo-title: Sichtbarkeit von Bildunterschriften steuern
title: Sichtbarkeit von Bildunterschriften steuern
uuid: 42913347-8158-474e-aa3c-ba4d38baba12
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

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

