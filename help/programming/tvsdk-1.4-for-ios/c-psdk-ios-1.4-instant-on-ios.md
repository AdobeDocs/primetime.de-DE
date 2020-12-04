---
description: Sofortiges Vorausladen von Medienteilen auf einem oder mehreren Kanälen. Nachdem ein Benutzer Kanal ausgewählt oder gewechselt hat, wird der Inhalt früher Beginn, da ein Teil der Pufferung bereits abgeschlossen ist.
seo-description: Sofortiges Vorausladen von Medienteilen auf einem oder mehreren Kanälen. Nachdem ein Benutzer Kanal ausgewählt oder gewechselt hat, wird der Inhalt früher Beginn, da ein Teil der Pufferung bereits abgeschlossen ist.
seo-title: Sofort-on
title: Sofort-on
uuid: 23864919-9045-4223-9e47-464e38ebe5ef
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Instant-on{#instant-on}

Sofortiges Vorausladen von Medienteilen auf einem oder mehreren Kanälen. Nachdem ein Benutzer Kanal ausgewählt oder gewechselt hat, wird der Inhalt früher Beginn, da ein Teil der Pufferung bereits abgeschlossen ist.

Wenn sich Ihr Player im Status `PTMediaPlayerStatusReady` befindet, rufen Sie `prepareToPlay` auf, um einen Teil des Inhalts für die spätere Wiedergabe vorab zu laden und zu verarbeiten.

>[!TIP]
>
>Wenn Sie `prepareToPlay` nicht aufrufen, wird `play` beim Aufrufen von `prepareToPlay` automatisch zuerst aufgerufen. Das Vorausladen und die Verarbeitung sind derzeit abgeschlossen.

TVSDK führt einige oder alle der folgenden Aufgaben für `prepareToPlay` aus:

* Wenn der Metadatenschlüssel `kSyncCookiesWithAVAsset` festgelegt ist, stellt TVSDK eine Anforderung an die ursprüngliche M3U8-Datei zur Synchronisierung von Cookies.
* Lädt DRM-Metadatenschlüssel.
* Erstellt und bereitet einige Strukturen, Elemente oder Assets vor, die für die Wiedergabe von Inhalten erforderlich sind.

>[!TIP]
>
>Die Methoden `PTMediaPlayer` und `PTMediaPlayerItem` `prepareToPlay` sind gleich. Um zu vermeiden, dass für jedes Asset eine separate `PTMediaPlayer`-Instanz erstellt wird, verwenden Sie die `PTMediaPlayerItem`-Methode.

Mit Instant-On können Sie mehrere Instanzen des Medienplayers oder Instanzen des Medienplayer-Elementladers gleichzeitig im Hintergrund starten und Video-Streams in allen diesen Instanzen puffern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird bei einem Aufruf von `play` auf dem neuen Kanal die Wiedergabe früher Beginn.
