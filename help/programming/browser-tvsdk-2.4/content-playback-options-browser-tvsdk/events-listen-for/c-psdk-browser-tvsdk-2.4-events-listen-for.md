---
description: Ereignisse aus Browser TVSDK geben den Status des Players, aufgetretene Fehler, den Abschluss von angeforderten Aktionen an, z. B. einen Videobeginn oder implizit auftretende Aktionen wie das Abschließen einer Anzeige.
title: Primetime-Player-Ereignisse überwachen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Übersicht {#listen-for-primetime-player-events-overview}

Ereignisse aus Browser TVSDK geben den Status des Players, aufgetretene Fehler, den Abschluss von angeforderten Aktionen an, z. B. einen Videobeginn oder implizit auftretende Aktionen wie das Abschließen einer Anzeige.

Da Ihre Anwendung auf viele dieser Ereignisse reagieren muss, müssen Sie Ereignisverarbeitungsroutinen implementieren und diese Routinen mit Browser TVSDK registrieren. Die Routinen rufen die relevanten Browser TVSDK-Methoden auf, um angemessen zu reagieren.

Im Folgenden finden Sie einige zusätzliche Informationen zu Ereignissen:

* Die Echtzeit-Wiedergabe von Videos erfordert für viele Browser TVSDK-Vorgänge eine asynchrone (nicht blockierende) Aktivität.
* Browser TVSDK unterstützt einen ereignisgesteuerten Video-Player.

  Es stellt Ereignisse bereit, die allen wichtigen Schritten im Wiedergabeprozess entsprechen. Sie registrieren diese Ereignisse beim Ereignismechanismus Ihrer Plattform und erstellen Ereignishandler, die aufgerufen werden, wenn diese Ereignisse auftreten. *`Event Handlers`* werden auch als Callback-Routinen oder Ereignis-Listener bezeichnet. Browser TVSDK bietet eine vollständige Palette von Methoden, die von den Ereignishandlern verwendet werden können.
* Ihre Anwendung initiiert im Allgemeinen nicht-blockierende Vorgänge, z. B. die Anforderung, die Videowiedergabe zu starten.

  Browser TVSDK kommuniziert asynchron mit Ihrer Anwendung, indem Ereignisse ausgelöst werden, z. B. wenn die Videowiedergabe beginnt, und ein Ereignis, wenn das Video abgeschlossen ist. Andere Ereignisse können auf Statusänderungen in Ihrem Player und Fehlerbedingungen hinweisen. Ihre Ereignishandler ergreifen die entsprechenden Aktionen.
