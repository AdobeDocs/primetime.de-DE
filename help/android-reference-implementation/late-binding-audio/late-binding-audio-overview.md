---
description: Sie können Steuerelemente für das späte Binden von Audio aktivieren und erstellen.
title: Übersicht
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Übersicht {#overview}

Sie können Steuerelemente für das späte Binden von Audio aktivieren und erstellen.

Der HLS-Standard ermöglicht Streams mit mehreren Formaten, was bedeutet, dass wir die Audio- und Videospuren eines Streams voneinander trennen können. Die Videospur mit mehreren Ausgabeformaten (z. B. 240p, 480p, 720p und 1080p) und die Audiospuren (z. B. Englisch, Spanisch, Französisch, Deutsch) können separat kodiert werden. Der Medienplayer wählt dann die gewünschten Video- und Audiospuren aus und bindet sie spontan, clientseitig.

Je nach Player-Benutzeroberfläche können Sie verschiedene Workflows implementieren. Der allgemeine Workflow für den Primetime-Player sieht wie folgt aus:

1. Wenn der Endbenutzer ein Video auswählt, wird eine Liste der verfügbaren Audiospuren für dieses Medienelement gefüllt.
1. Wenn der Benutzer auf der Benutzeroberfläche auf die Schaltfläche Einstellungen tippt, werden die Optionen für die Audiospur angezeigt.
1. Wenn ein Audio-Track ausgewählt ist, wird der Track zum aktiven Audio-Track.
1. Der Endbenutzer kann auf die Schaltfläche Einstellungen tippen, um zum ursprünglichen Audio-Track zurückzukehren.
