---
title: Anwenden von Einschränkungen bei der Anzeigenauflösung
description: Anwenden von Einschränkungen bei der Anzeigenauflösung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Anwenden von Einschränkungen bei der Anzeigenauflösung {#apply-ad-resolution-constraints}

Es kann vorkommen, dass bestimmte Anzeigenanbieter nur langsam reagieren, was dazu führen kann, dass die Startzeiten von Videos zunehmen. Primetime Ad Insertion unterstützt Timeouts von Anzeigenanfragen und die gesamte Phase der Anzeigenauflösung, um die Auswirkungen dieser langsamen Anzeigenanbieter zu begrenzen.  Fallback-Anzeigen können auch eingefügt werden, wenn nachgelagerte Anzeigenanbieter zu langsam sind, um zu reagieren.  Weitere Informationen finden Sie unter [`ptadtimeout` Parameter in der Bootstrap-API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).
