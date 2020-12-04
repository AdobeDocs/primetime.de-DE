---
description: Das MediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein MediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.
seo-description: Das MediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein MediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.
seo-title: Info zur MediaPlayerItem-Klasse
title: Info zur MediaPlayerItem-Klasse
uuid: d7f65edf-4693-4b1e-bae0-46fadce98751
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Info zur MediaPlayerItem-Klasse{#about-the-mediaplayeritem-class}

Das MediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein MediaPlayerItem-Element stellt Audio- oder Videodateien auf Ihrem Player dar.

Nachdem eine Medienressource erfolgreich geladen wurde, erstellt TVSDK eine Instanz der Klasse `MediaPlayerItem`, um Zugriff auf diese Ressource zu gewähren.

Das `MediaResource` stellt eine Anforderung dar, die von der Anwendungsebene an die `MediaPlayer`-Instanz gesendet wird, um Inhalte zu laden.

Das `MediaPlayer` löst die Medienressource, lädt die zugehörige Manifestdatei und analysiert das Manifest. Dies ist der asynchrone Teil des Ressourcenladevorgangs. Die `MediaPlayerItem`-Instanz wird erzeugt, nachdem die Ressource aufgelöst wurde, und diese Instanz ist eine aufgelöste Version von `MediaResource`. TVSDK bietet Zugriff auf die neu erstellte `MediaPlayerItem`-Instanz über `MediaPlayer.CurrentItem`

>[!TIP]
>
>Sie müssen warten, bis die Ressource erfolgreich geladen wurde, bevor Sie auf das Medienplayer-Element zugreifen können.

