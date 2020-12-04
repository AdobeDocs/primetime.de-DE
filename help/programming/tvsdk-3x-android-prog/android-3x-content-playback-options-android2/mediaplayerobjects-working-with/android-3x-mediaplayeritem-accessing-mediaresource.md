---
description: Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.
seo-description: Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.
seo-title: MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen
title: MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen
uuid: 46845583-0a76-4411-a8bc-0a16ebfe8e6e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Mit den Methoden in der MediaPlayerItem-Klasse können Sie Informationen über den Inhaltsstream abrufen, der von einer geladenen MediaResource dargestellt wird.

| Methode | Beschreibung |
|--- |--- |
| **Anzeigen-Tags** |  |
| Liste`<String>` getAdTags() | Stellt die Liste der Anzeigen-Tags bereit, die für den Anzeigenplatzierungsprozess verwendet werden. |
| **Live-Stream** |  |
| boolean isLive(); | True, wenn der Stream live ist; false, wenn es VOD ist. |
| **DRM-geschützt** |  |
| boolean isProtected(); | True, wenn der Stream DRM-geschützt ist. |
| Liste`<DRMMetadataInfo>` getDRMMetadataInfos(); | Liste aller DRM-Metadatenobjekte, die im Manifest gefunden werden. |
| **Untertitel** |  |
| boolean hasClosedCaptions(); | True, wenn Untertitel-Tracks verfügbar sind. |
| Liste`<ClosedCaptionsTrack>` getClosedCationsTracks(); | Bietet eine Liste der verfügbaren Untertitelspuren. |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | Ruft die mit SelectClosedCaptionsTrack ausgewählte aktuelle Untertitelspur ab. |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack closeCaptionsTrack) | Legt eine Untertitelspur als aktuelle Untertitelspur fest. |
| **Alternative Audiospuren** |  |
| boolean hasAlternateAudio(); | True, wenn der Stream über alternative Audiospuren verfügt. Hinweis:  Die Haupt- (Standard-)Audiospur ist ebenfalls Teil der alternativen Liste der Audiospur.  TVSDK für Android betrachtet die Hauptaudiospur als eines der Elemente in der alternativen Audiospur-Liste. Aus diesem Grund gibt MediaPlayerItem.hasAlternateAudio nur dann den Wert &quot;false&quot;zurück, wenn der Stream überhaupt keinen Ton enthält. Wenn der Inhalt nur eine Audiospur enthält, gibt diese Methode true zurück und `MediaPlayerItem.getAudioTracks` gibt eine Liste mit einem einzelnen Element (die Standard-Audiospur) zurück. |
| Liste`<AudioTrack>` getAudioTracks(); | Bietet eine Liste der verfügbaren alternativen Audiospuren. |
| AudioTrack getSelectedAudioTrack(); | Ruft die mit selectAudioTrack ausgewählte Audiospur ab. |
| selectAudioTrack ( AudioTrack audioTrack ) | Wählt eine Audiospur als aktuelle Audiospur aus. |
| **Zeitgesteuerte Metadaten** |  |
| boolean hasTimedMetadata(); | True, wenn dem Stream Zeitmetadaten zugeordnet sind. |
| Liste`<TimedMetadata>` getTimedMetadata(); | Bietet eine Liste der zeitgesteuerten Metadatenobjekte, die mit dem Stream verknüpft sind. |
| **Mehrere Profil (Bitraten)** |
| boolean isDynamic(); | True, wenn der Stream ein MBR-Stream (multiple bit rate) ist. |
| Liste`<Profile>` getProfiles(); | Bietet eine Liste der zugehörigen Profile zur Bitrate. Für jedes Profil können Sie die Bitrate sowie die Höhe und Breite des Profils abrufen. |
| Profil getSelectedProfile() | Ruft das aktuell ausgewählte Profil ab. |
| **Trick Play** |  |
| boolean isTrickPlaySupported(); | &quot;True&quot;, wenn der Player schnelle Vorwärts-, Zurückspulen- und Wiederaufnahme unterstützt. |
| Liste`< Float>` getAvailablePlaybackRates() | Bietet die Liste der verfügbaren Wiedergaberaten im Kontext der Funktion &quot;Trick-play&quot;. |
| Float getSelectedPlaybackRate() | Ruft die derzeit ausgewählte Wiedergabegeschwindigkeit ab. |
| MediaPlayerItemConfig getConfig() | Gibt die mit diesem Element verknüpfte MediaPlayerItemConfig-Instanz zurück. |
| **Medienressource** |  |
| MediaResource getResource(); | Gibt die mit diesem Element verknüpfte Medienressource zurück. |
| int getResourceId() | Gibt die mit diesem Element verknüpfte Medienkennung zurück. Diese ID wird festgelegt, wenn das Element mit MediaPlayerItemLoader.load geladen wird. |