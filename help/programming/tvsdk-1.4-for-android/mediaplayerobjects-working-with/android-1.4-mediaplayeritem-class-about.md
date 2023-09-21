---
description: Das MediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein MediaPlayerItem steht für Audio oder Video auf Ihrem Player.
title: Über die MediaPlayerItem-Klasse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Über die MediaPlayerItem-Klasse{#about-the-mediaplayeritem-class}

Das MediaPlayer-Objekt stellt Ihren Medienplayer dar. Ein MediaPlayerItem steht für Audio oder Video auf Ihrem Player.

Nachdem eine Medienressource erfolgreich geladen wurde, erstellt TVSDK eine Instanz der `MediaPlayerItem` -Klasse, um Zugriff auf diese Ressource zu gewähren.

Die `MediaResource` stellt eine Anfrage dar, die von der Anwendungsschicht an die `MediaPlayer` -Instanz, um Inhalte zu laden.

Die `MediaPlayer` löst die Medienressource auf, lädt die zugehörige Manifestdatei und analysiert das Manifest. Dies ist der asynchrone Teil des Ressourcenladevorgangs. Die `MediaPlayerItem` -Instanz wird erzeugt, nachdem die Ressource aufgelöst wurde. Diese Instanz ist eine aufgelöste Version eines `MediaResource`. TVSDK bietet Zugriff auf die neu erstellten `MediaPlayerItem` Instanz über `MediaPlayer.CurrentItem`

>[!TIP]
>
>Sie müssen warten, bis die Ressource erfolgreich geladen wurde, bevor Sie auf das Medienplayer-Element zugreifen.
