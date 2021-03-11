---
description: Nachdem eine MediaResource erfolgreich geladen wurde, erstellt Browser TVSDK eine Instanz der MediaPlayerItem-Klasse, um Zugriff auf diese Ressource zu gewähren.
title: Info zur MediaPlayerItem-Klasse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Info zur MediaPlayerItem-Klasse{#about-the-mediaplayeritem-class}

Nachdem eine MediaResource erfolgreich geladen wurde, erstellt Browser TVSDK eine Instanz der MediaPlayerItem-Klasse, um Zugriff auf diese Ressource zu gewähren.

Das `MediaResource` stellt eine Anforderung dar, die von der Anwendungsebene an die `MediaPlayer`-Instanz gesendet wird, um Inhalte zu laden.

Das `MediaPlayer` löst die Medienressource, lädt die zugehörige Manifestdatei und analysiert das Manifest. Dies ist der asynchrone Teil des Ressourcenladevorgangs. Die `MediaPlayerItem`-Instanz wird erzeugt, nachdem die Ressource aufgelöst wurde, und diese Instanz ist eine aufgelöste Version von `MediaResource`. Browser TVSDK bietet Zugriff auf die neu erstellte `MediaPlayerItem`-Instanz über `MediaPlayer.CurrentItem`.

>[!TIP]
>
>Sie müssen warten, bis die Ressource erfolgreich geladen wurde, bevor Sie auf das Medienplayer-Element zugreifen können.

