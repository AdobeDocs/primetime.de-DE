---
description: Die Anzeigenzeitleiste, die für eine Wiedergabe von VOD-Inhalten geeignet ist, ist möglicherweise für spätere Wiedergaben ungeeignet. Sie können eine VOD-Zeitleiste ersetzen, ohne den Inhalt zu ändern.
title: Änderungen an VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Änderungen an VOD {#changes-to-vod}

Die Anzeigenzeitleiste, die für eine Wiedergabe von VOD-Inhalten geeignet ist, ist möglicherweise für spätere Wiedergaben ungeeignet. Sie können eine VOD-Zeitleiste ersetzen, ohne den Inhalt zu ändern.

Zu den Situationen, in denen Sie eine VOD-Zeitschiene ersetzen möchten, gehören:

* Ersetzen Sie lokale Anzeigen, aber lassen Sie nationale Anzeigen während eines C3-Fensters.
* Ersetzen Sie verbrannte Anzeigen, nachdem das C3-Fenster geschlossen wurde.
* Ersetzen Sie alte C3-Anzeigen dynamisch durch neuere Anzeigen mit höherer Dauer.
* Fügen Sie weniger oder gar keine Anzeigen ein.

Sie können die Anzeigenzeitschiene ersetzen, indem Sie eine neue Anzeigeneinfügeanforderung mit der ursprünglichen M3U8-Datei und einem anderen Wert des Parameters `pttimeline` Abfrage senden.