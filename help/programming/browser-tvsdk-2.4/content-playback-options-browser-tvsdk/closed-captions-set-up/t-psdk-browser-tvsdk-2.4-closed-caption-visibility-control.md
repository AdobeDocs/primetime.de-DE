---
description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt.
title: Sichtbarkeit von Bildunterschriften steuern
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Sichtbarkeit bei geschlossener Beschriftung kontrollieren{#control-closed-caption-visibility}

Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt.

>[!TIP]
>
>Wenn Sie ändern, welche Spur aktuell ist, bleibt die Sichtbarkeitseinstellung gleich.

Wenn Untertiteltext angezeigt wird, wenn der Player in den Suchmodus wechselt, wird der Text nach Abschluss der Suche nicht mehr angezeigt. Stattdessen zeigt Browser TVSDK nach einigen Sekunden den nächsten Untertiteltext im Video nach der Endsuchposition an.

>[!TIP]
>
>Die Sichtbarkeitswerte für Untertitel werden mit `MediaPlayer.VISIBLE` und `MediaPlayer.INVISIBLE` gesteuert.

1. Verwenden Sie die Eigenschaft `MediaPlayer.ccVisibility`, um auf die aktuelle Sichtbarkeitseinstellung für die Bildunterschriften zuzugreifen.

