---
description: Ereignisse von TVSDK geben den Player-Status, Fehler, die auftreten, den Abschluss von angeforderten Aktionen an, z. B. die Videowiedergabe oder implizit auftretende Aktionen, z. B. das Ausfüllen einer Anzeige.
seo-description: Ereignisse von TVSDK geben den Player-Status, Fehler, die auftreten, den Abschluss von angeforderten Aktionen an, z. B. die Videowiedergabe oder implizit auftretende Aktionen, z. B. das Ausfüllen einer Anzeige.
seo-title: Primetime Player-Ereignis suchen
title: Primetime Player-Ereignis suchen
uuid: bd0a428c-fa51-41a6-950a-9d6843c6e177
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Übersicht {#listen-for-primetime-player-events-overview}

Ereignisse von TVSDK geben den Player-Status, Fehler, die auftreten, den Abschluss von angeforderten Aktionen an, z. B. die Videowiedergabe oder implizit auftretende Aktionen, z. B. das Ausfüllen einer Anzeige.

Da Ihre Anwendung auf viele dieser Ereignis reagieren muss, müssen Sie Ereignis-Handling-Routinen implementieren und diese Routinen mit TVSDK registrieren. Die Routinen rufen die relevanten TVSDK-Methoden auf, um angemessen zu reagieren.

Weitere Informationen zu Ereignissen:

* Die Echtzeit-Natur der Videowiedergabe erfordert für viele TVSDK-Vorgänge eine asynchrone (nicht blockierende) Aktivität.
* TVSDK unterstützt einen Ereignis-basierten Videoplayer.

   Es stellt Ereignis bereit, die allen wichtigen Schritten im Ablauf entsprechen. Sie registrieren diese Ereignis mit dem Ereignis-Mechanismus Ihrer Plattform und erstellen Ereignis-Handler, die aufgerufen werden, wenn diese Ereignis auftreten. *`Event Handlers`* werden auch als Callback-Routinen oder Ereignis-Listener bezeichnet. TVSDK bietet eine umfassende Palette von Methoden, die von den Ereignis-Handlern verwendet werden können.
* Ihre Anwendung initiiert im Allgemeinen Vorgänge zum Entfernen von Blockern, z. B. um anzufordern, dass ein Video-Beginn abgespielt wird.

   TVSDK kommuniziert asynchron mit Ihrer Anwendung, indem Ereignis ausgelöst werden, z. B. wenn die Beginn abgespielt werden und ein Ereignis nach Abschluss des Videos. Andere Ereignis können auf Statusänderungen in Ihrem Player und Fehlerbedingungen hinweisen. Ihre Ereignis-Handler ergreifen entsprechende Maßnahmen.