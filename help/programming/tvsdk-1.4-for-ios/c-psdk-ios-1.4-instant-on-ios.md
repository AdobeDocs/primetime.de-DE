---
description: Sofortiges Vorausfüllen lädt Teile des Mediums auf einen oder mehrere Kanäle. Nachdem ein Benutzer Kanäle ausgewählt oder wechselt, wird der Inhalt früher gestartet, da einige der Pufferungen bereits abgeschlossen sind.
title: Sofort-On
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Sofort-On{#instant-on}

Sofortiges Vorausfüllen lädt Teile des Mediums auf einen oder mehrere Kanäle. Nachdem ein Benutzer Kanäle ausgewählt oder wechselt, wird der Inhalt früher gestartet, da einige der Pufferungen bereits abgeschlossen sind.

Wenn Ihr Player im `PTMediaPlayerStatusReady` Status, Aufruf `prepareToPlay` , um einen Teil des Inhalts für die spätere Wiedergabe vorab zu laden und zu verarbeiten.

>[!TIP]
>
>Wenn Sie nicht `prepareToPlay`, aufrufen `play` automatische Aufrufe `prepareToPlay` zuerst. Das Vorausfüllen und die Verarbeitung sind derzeit abgeschlossen.

TVSDK führt einige oder alle der folgenden Aufgaben für `prepareToPlay`:

* Wenn der Metadatenschlüssel `kSyncCookiesWithAVAsset` festgelegt ist, sendet TVSDK eine Anfrage an die ursprüngliche M3U8-Datei, um Cookies zu synchronisieren.
* Lädt DRM-Metadatenschlüssel.
* Erstellt und bereitet einige Strukturen, Elemente oder Assets vor, die für die Wiedergabe von Inhalten erforderlich sind.

>[!TIP]
>
>Die `PTMediaPlayer` und `PTMediaPlayerItem` `prepareToPlay` -Methoden sind gleich. So vermeiden Sie die Erstellung eines separaten `PTMediaPlayer` -Instanz für jedes Asset verwenden Sie die `PTMediaPlayerItem` -Methode.

Mit Instant-on können Sie mehrere Instanzen des Medienplayers oder des Medienplayer-Element-Laders gleichzeitig im Hintergrund starten und Videostreams in all diesen Instanzen puffern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird `play` im neuen Kanal wird die Wiedergabe früher gestartet.
