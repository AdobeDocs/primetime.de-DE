---
description: Sie können die Sichtbarkeit geschlossener Untertitel steuern. Wenn die Sichtbarkeit aktiviert ist, wird der aktuell ausgewählte Track angezeigt. Wenn Sie ändern, welcher Track aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
title: Sichtbarkeit der Untertitel steuern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Übersicht {#control-closed-caption-visibility}

Sie können die Sichtbarkeit geschlossener Untertitel steuern. Wenn die Sichtbarkeit aktiviert ist, wird der aktuell ausgewählte Track angezeigt. Wenn Sie ändern, welcher Track aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.

>[!TIP]
>
>Wenn der Beschriftungstext angezeigt wird, wenn der Player in den Suchmodus wechselt, wird der Text nach Abschluss der Suche nicht mehr angezeigt. Stattdessen zeigt TVSDK nach einigen Sekunden den nächsten Untertiteltext im Video nach der Endsuchposition an.

>[!NOTE]
>
>Die Sichtbarkeitswerte für geschlossene Beschriftungen werden in `MediaPlayer.Visibility`.
>
>```java
>enum Visibility { 
>       VISIBLE,  
>       INVISIBLE 
>}
>```
>

1. Warten Sie, bis der MediaPlayer mindestens den Status VORBEREITET aufweist (siehe [Auf gültigen Status warten](../../../tvsdk-1.4-for-android/ui-configure/android-1.4-ui-state-prepared-wait-for.md)).
1. Um die aktuelle Sichtbarkeitseinstellung für geschlossene Untertitel zu erhalten, verwenden Sie die Getter-Methode in MediaPlayer, die einen Sichtbarkeitswert zurückgibt.

   ```java
   Visibility getCCVisibility() throws IllegalStateException;
   ```

1. Um die Sichtbarkeit für geschlossene Beschriftungen zu ändern, verwenden Sie die Set-Methode und übergeben Sie einen Sichtbarkeitswert von `MediaPlayer.Visibility`.

   Beispiel:

   ```java
   mediaPlayer.setCCVisibility(Visibility.VISIBLE);
   ```
