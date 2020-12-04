---
description: Ereignis aus Browser TVSDK geben den Player-Status, Fehler, die auftreten, den Abschluss von angeforderten Aktionen an, wie z. B. die Videowiedergabe oder implizit auftretende Aktionen, wie z. B. das Abschließen einer Anzeige.
seo-description: Ereignis aus Browser TVSDK geben den Player-Status, Fehler, die auftreten, den Abschluss von angeforderten Aktionen an, wie z. B. die Videowiedergabe oder implizit auftretende Aktionen, wie z. B. das Abschließen einer Anzeige.
seo-title: Primetime Player-Ereignis suchen
title: Primetime Player-Ereignis suchen
uuid: 7b7c28ac-22ae-46a3-bbeb-bef1b04baeb3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Übersicht {#listen-for-primetime-player-events-overview}

Ereignis aus Browser TVSDK geben den Player-Status, Fehler, die auftreten, den Abschluss von angeforderten Aktionen an, wie z. B. die Videowiedergabe oder implizit auftretende Aktionen, wie z. B. das Abschließen einer Anzeige.

Da Ihre Anwendung auf viele dieser Ereignis reagieren muss, müssen Sie Ereignis-Bereitstellungsroutinen implementieren und diese Routinen mit Browser TVSDK registrieren. Die Routinen rufen die entsprechenden Browser TVSDK-Methoden auf, um angemessen zu reagieren.

Im Folgenden finden Sie weitere Informationen zu Ereignissen:

* Die Echtzeit-Natur der Videowiedergabe erfordert für viele Browser TVSDK-Vorgänge eine asynchrone Aktivität (ohne Blockierung).
* Browser TVSDK unterstützt einen Ereignis-basierten Videoplayer.

   Es stellt Ereignis bereit, die allen wichtigen Schritten im Ablauf entsprechen. Sie registrieren diese Ereignis mit dem Ereignis-Mechanismus Ihrer Plattform und erstellen Ereignis-Handler, die aufgerufen werden, wenn diese Ereignis auftreten. *`Event Handlers`* werden auch als Callback-Routinen oder Ereignis-Listener bezeichnet. Browser TVSDK bietet eine komplette Palette von Methoden, die von den Ereignis-Handlern verwendet werden können.
* Ihre Anwendung initiiert im Allgemeinen Vorgänge zum Entfernen von Blockern, z. B. um anzufordern, dass ein Video-Beginn abgespielt wird.

   Browser TVSDK kommuniziert asynchron mit Ihrer Anwendung, indem Ereignis ausgelöst werden, z. B. wenn die Videowiedergabe Beginn und ein Ereignis nach Abschluss des Videos sind. Andere Ereignis können auf Statusänderungen in Ihrem Player und Fehlerbedingungen hinweisen. Ihre Ereignis-Handler ergreifen entsprechende Maßnahmen.

