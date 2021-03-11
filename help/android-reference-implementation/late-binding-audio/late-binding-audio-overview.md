---
description: Sie können Steuerelemente für späte Bindungen aktivieren und erstellen.
title: Übersicht
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Übersicht {#overview}

Sie können Steuerelemente für späte Bindungen aktivieren und erstellen.

Der HLS-Standard erlaubt Streams mit mehreren Formaten, was bedeutet, dass wir die Audio- und Videospuren eines Streams voneinander trennen können. Die Videospur mit mehreren Darstellungen (z. B. 240p, 480p, 720p und 1080p) und die Audiospuren (z. B. Englisch, Spanisch, Französisch, Deutsch) können separat kodiert werden. Der Medienplayer wählt dann die gewünschten Video- und Audiospuren aus und bindet sie sofort, auf der Clientseite.

Sie können je nach Player-Benutzeroberfläche verschiedene Workflows implementieren. Der allgemeine Arbeitsablauf für den Primetime-Player lautet wie folgt:

1. Wenn der Endbenutzer ein Video auswählt, wird eine Liste der verfügbaren Audiospuren für dieses Medienelement gefüllt.
1. Wenn der Benutzer auf der Benutzeroberfläche auf die Schaltfläche &quot;Einstellungen&quot;tippt, werden die Optionen für die Audiospur angezeigt.
1. Wenn eine Audiospur ausgewählt ist, wird die Spur zur aktiven Audiospur.
1. Der Endbenutzer kann auf die Schaltfläche &quot;Einstellungen&quot;tippen, um zur ursprünglichen Audiospur zurückzukehren.

