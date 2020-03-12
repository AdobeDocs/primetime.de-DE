---
description: Das MediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein MediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.
seo-description: Das MediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein MediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.
seo-title: Info zur MediaPlayerItem-Klasse
title: Info zur MediaPlayerItem-Klasse
uuid: 531dd1a6-d72c-4ae3-9c3f-2f1d854245c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Info zur MediaPlayerItem-Klasse{#about-the-mediaplayeritem-class}

Das MediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein MediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.

<!--<a id="section_01BC89E5C5A94D0A95EF9D29FBCE758A"></a>-->

Nachdem eine Medienressource erfolgreich geladen wurde, erstellt TVSDK eine Instanz der `MediaPlayerItem` Klasse, um Zugriff auf diese Ressource zu gewähren.

Die `MediaResource` stellt eine Anforderung dar, die von der Anwendungsebene an die `MediaPlayer` Instanz zum Laden von Inhalten gesendet wird.

Das `MediaPlayer` Programm löst die Medienressource, lädt die zugehörige Manifestdatei und analysiert das Manifest. Dies ist der asynchrone Teil des Ressourcenladevorgangs. Die `MediaPlayerItem` Instanz wird erstellt, nachdem die Ressource aufgelöst wurde, und diese Instanz ist eine aufgelöste Version eines `MediaResource`. TVSDK bietet Zugriff auf die neu erstellte `MediaPlayerItem` Instanz über `MediaPlayer.currentItem`.

>[!TIP]
>
>Sie müssen warten, bis die Ressource erfolgreich geladen wurde, bevor Sie auf das Medienplayer-Element zugreifen können.

