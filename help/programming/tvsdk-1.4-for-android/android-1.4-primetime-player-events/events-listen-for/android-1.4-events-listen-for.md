---
description: Ereignisse von TVSDK geben den Player-Status, auftretende Fehler, den Abschluss von angeforderten Aktionen an, z. B. die Videowiedergabe oder implizit auftretende Aktionen, z. B. das Ausfüllen einer Anzeige.
seo-description: Ereignisse von TVSDK geben den Player-Status, auftretende Fehler, den Abschluss von angeforderten Aktionen an, z. B. die Videowiedergabe oder implizit auftretende Aktionen, z. B. das Ausfüllen einer Anzeige.
seo-title: Primetime Player-Ereignis suchen
title: Primetime Player-Ereignis suchen
uuid: f85cf9aa-50a1-4b06-a2fe-6b20f84cff32
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Übersicht {#listen-for-primetime-player-events-overview}

Ereignisse von TVSDK geben den Player-Status, auftretende Fehler, den Abschluss von angeforderten Aktionen an, z. B. die Videowiedergabe oder implizit auftretende Aktionen, z. B. das Ausfüllen einer Anzeige.

Da Ihre Anwendung auf viele dieser Ereignis reagieren muss, müssen Sie Ereignis-Bereitstellungsroutinen implementieren und diese Routinen mit TVSDK registrieren. Die Routinen rufen die relevanten TVSDK-Methoden auf, um angemessen zu reagieren.

Im Folgenden finden Sie weitere Informationen zu Ereignissen:

* Die Echtzeit-Natur der Videowiedergabe erfordert für viele TVSDK-Vorgänge eine asynchrone (non-locking) Aktivität.
* TVSDK unterstützt einen Ereignis-basierten Videoplayer.

   Es stellt Ereignis bereit, die allen wichtigen Schritten im Ablauf entsprechen. Sie registrieren diese Ereignis mit dem Ereignis-Mechanismus Ihrer Plattform und erstellen Ereignis-Handler, die aufgerufen werden, wenn diese Ereignis auftreten. *`Event Handlers`* werden auch als Callback-Routinen oder Ereignis-Listener bezeichnet. TVSDK bietet eine umfassende Palette von Methoden, die von den Ereignis-Handlern verwendet werden können.
* Ihre Anwendung initiiert im Allgemeinen Vorgänge zum Entfernen von Blockern, z. B. um anzufordern, dass ein Video-Beginn abgespielt wird.

   TVSDK kommuniziert asynchron mit Ihrer Anwendung, indem Ereignis ausgelöst werden, z. B. wenn die Beginn abgespielt werden und ein Ereignis nach Abschluss des Videos. Andere Ereignis können auf Statusänderungen in Ihrem Player und Fehlerbedingungen hinweisen. Ihre Ereignis-Handler ergreifen entsprechende Maßnahmen.

