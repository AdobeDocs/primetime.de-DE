---
description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt.
seo-description: Sie können die Sichtbarkeit von Bildunterschriften steuern. Wenn die Sichtbarkeit aktiviert ist, wird die aktuell ausgewählte Spur angezeigt.
seo-title: Sichtbarkeit von Bildunterschriften steuern
title: Sichtbarkeit von Bildunterschriften steuern
uuid: b161a729-73f3-4019-a95e-013b42779842
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '143'
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

