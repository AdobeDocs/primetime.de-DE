---
description: Nachdem eine MediaResource erfolgreich geladen wurde, erstellt Browser TVSDK eine Instanz der MediaPlayerItem-Klasse, um Zugriff auf diese Ressource zu gewähren.
seo-description: Nachdem eine MediaResource erfolgreich geladen wurde, erstellt Browser TVSDK eine Instanz der MediaPlayerItem-Klasse, um Zugriff auf diese Ressource zu gewähren.
seo-title: Info zur MediaPlayerItem-Klasse
title: Info zur MediaPlayerItem-Klasse
uuid: 5226d3ad-2438-44fe-a8ef-bcc0da8331b8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Info zur MediaPlayerItem-Klasse{#about-the-mediaplayeritem-class}

Nachdem eine MediaResource erfolgreich geladen wurde, erstellt Browser TVSDK eine Instanz der MediaPlayerItem-Klasse, um Zugriff auf diese Ressource zu gewähren.

Das `MediaResource` stellt eine Anforderung dar, die von der Anwendungsebene an die `MediaPlayer`-Instanz gesendet wird, um Inhalte zu laden.

Das `MediaPlayer` löst die Medienressource, lädt die zugehörige Manifestdatei und analysiert das Manifest. Dies ist der asynchrone Teil des Ressourcenladevorgangs. Die `MediaPlayerItem`-Instanz wird erzeugt, nachdem die Ressource aufgelöst wurde, und diese Instanz ist eine aufgelöste Version von `MediaResource`. Browser TVSDK bietet Zugriff auf die neu erstellte `MediaPlayerItem`-Instanz über `MediaPlayer.CurrentItem`.

>[!TIP]
>
>Sie müssen warten, bis die Ressource erfolgreich geladen wurde, bevor Sie auf das Medienplayer-Element zugreifen können.

