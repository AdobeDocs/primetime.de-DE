---
description: Sie können die Sichtbarkeit geschlossener Untertitel steuern. Wenn die Sichtbarkeit aktiviert ist, wird der aktuell ausgewählte Track angezeigt.
title: Sichtbarkeit der Untertitel steuern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Sichtbarkeit der Untertitel steuern{#control-closed-caption-visibility}

Sie können die Sichtbarkeit geschlossener Untertitel steuern. Wenn die Sichtbarkeit aktiviert ist, wird der aktuell ausgewählte Track angezeigt.

>[!TIP]
>
>Wenn Sie ändern, welcher Track aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.

Wenn der Untertiteltext angezeigt wird, wenn der Player in den Suchmodus wechselt, wird der Text nach Abschluss der Suche nicht mehr angezeigt. Stattdessen zeigt Browser TVSDK nach einigen Sekunden den nächsten Untertiteltext im Video nach der Endsuchposition an.

>[!TIP]
>
>Die Sichtbarkeitswerte für geschlossene Untertitel werden mit `MediaPlayer.VISIBLE` und `MediaPlayer.INVISIBLE`.

1. Verwenden Sie die `MediaPlayer.ccVisibility` -Eigenschaft, um auf die aktuelle Sichtbarkeitseinstellung für die geschlossenen Beschriftungen zuzugreifen.
