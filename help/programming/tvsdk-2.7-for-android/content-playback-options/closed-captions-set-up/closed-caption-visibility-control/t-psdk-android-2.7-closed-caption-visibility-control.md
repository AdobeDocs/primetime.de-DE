---
description: Sie können die Sichtbarkeit geschlossener Untertitel steuern. Wenn die Sichtbarkeit aktiviert wurde, wird der aktuell ausgewählte Track angezeigt. Wenn Sie ändern, welcher Track aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.
title: Sichtbarkeit der Untertitel steuern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Übersicht {#control-closed-caption-visibility-overview}

Sie können die Sichtbarkeit geschlossener Untertitel steuern. Wenn die Sichtbarkeit aktiviert wurde, wird der aktuell ausgewählte Track angezeigt. Wenn Sie ändern, welcher Track aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.

>[!TIP]
>
>Wenn der Untertiteltext angezeigt wird, wenn der Player in den Suchmodus wechselt, wird der Text nach Abschluss der Suche nicht mehr angezeigt. Stattdessen zeigt TVSDK nach einigen Sekunden den nächsten Untertiteltext im Video nach der Endsuchposition an.
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

1. Warten Sie auf die `MediaPlayer` mindestens den Status VORBEREITET haben.

   Weitere Informationen finden Sie unter ui-state-prepared-wait-for .
1. Um die aktuelle Sichtbarkeitseinstellung für geschlossene Untertitel zu erhalten, verwenden Sie die Getter-Methode in `MediaPlayer`, der einen Sichtbarkeitswert zurückgibt.

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. Um die Sichtbarkeit für geschlossene Beschriftungen zu ändern, verwenden Sie die Set-Methode und übergeben Sie einen Sichtbarkeitswert von `MediaPlayer.Visibility`.

   Beispiel:

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```
