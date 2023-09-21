---
description: Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.
title: MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MediaPlayerItem-Methoden für den Zugriff auf MediaResource-Informationen {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Die Methoden in der MediaPlayerItem-Klasse ermöglichen es Ihnen, Informationen über den Inhalts-Stream abzurufen, der durch eine geladene MediaResource dargestellt wird.

| Methode | Beschreibung |
|--- |--- |
| **Anzeigen-Tags** |  |
| Liste`<String>` getAdTags() | Stellt die Liste der Anzeigen-Tags bereit, die für den Anzeigenplatzierungsprozess verwendet werden. |
| **Live-Stream** |  |
| boolean isLive(); | True , wenn der Stream live ist, false , wenn es VOD ist. |
| **DRM-geschützt** |  |
| boolean isProtected(); | True , wenn der Stream DRM-geschützt ist. |
| Liste`<DRMMetadataInfo>` getDRMMetadataInfos(); | Listet alle DRM-Metadatenobjekte auf, die im Manifest gefunden wurden. |
| **Geschlossene Untertitel** |  |
| boolean hasClosedCaptions(); | True , wenn geschlossene Untertitelspuren verfügbar sind. |
| Liste`<ClosedCaptionsTrack>` getClosedCationsTracks(); | Bietet eine Liste der verfügbaren Tracks mit geschlossenen Untertiteln. |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | Ruft die aktuelle mit SelectClosedCaptionsTrack ausgewählte Untertitelspur ab. |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) | Legt fest, dass eine Untertitelspur die aktuelle Untertitelspur ist. |
| **Alternative Audiospuren** |  |
| boolean hasAlternateAudio(); | True , wenn der Stream alternative Audiospuren hat. Hinweis: Der Haupt-Audio-Track (Standard) ist ebenfalls Teil der alternativen Audio-Track-Liste.  TVSDK für Android betrachtet den Haupt-Audio-Track als eines der Elemente in der alternativen Audio-Track-Liste. Aus diesem Grund gibt MediaPlayerItem.hasAlternateAudio nur dann &quot;false&quot;zurück, wenn der Stream überhaupt keine Audioinformationen enthält. Wenn der Inhalt nur eine Audiospur enthält, gibt diese Methode &quot;true&quot;zurück und  `MediaPlayerItem.getAudioTracks`  gibt eine Liste mit einem einzelnen Element (dem standardmäßigen Audio-Track) zurück. |
| Liste`<AudioTrack>` getAudioTracks(); | Bietet eine Liste der verfügbaren alternativen Audiospuren. |
| AudioTrack getSelectedAudioTrack(); | Ruft den mit selectAudioTrack ausgewählten Audio-Track ab. |
| selectAudioTrack ( AudioTrack audioTrack ) | Wählt einen Audio-Track als aktuellen Audio-Track aus. |
| **Zeitgesteuerte Metadaten** |  |
| boolean hasTimedMetadata(); | True , wenn dem Stream zeitgesteuerte Metadaten zugeordnet sind. |
| Liste`<TimedMetadata>` getTimedMetadata(); | Stellt eine Liste der zeitgesteuerten Metadatenobjekte bereit, die mit dem Stream verknüpft sind. |
| **Mehrere Profile (Bitraten)** |
| boolean isDynamic(); | True , wenn es sich bei dem Stream um einen MBR-Stream (multiple bit rate) handelt. |
| Liste`<Profile>` getProfiles(); | Enthält eine Liste der zugehörigen Bitratenprofile. Für jedes Profil können Sie dessen Bitrate sowie Höhe und Breite abrufen. |
| Profil getSelectedProfile() | Ruft das aktuell ausgewählte Profil ab. |
| **Trick play** |  |
| boolean isTrickPlaySupported(); | True , wenn der Player die schnelle Weiterleitung, Zurückspulen und Wiederaufnehmen unterstützt. |
| Liste`< Float>` getAvailablePlaybackRates() | Bietet die Liste der verfügbaren Wiedergaberaten im Kontext der Funktion &quot;Trick-Play&quot;. |
| Float getSelectedPlaybackRate() | Ruft die aktuell ausgewählte Wiedergaberate ab. |
| MediaPlayerItemConfig getConfig() | Gibt die mit diesem Element verknüpfte MediaPlayerItemConfig -Instanz zurück. |
| **Medienressource** |  |
| MediaResource getResource(); | Gibt die diesem Element zugeordnete Medienressource zurück. |
| int getResourceId() | Gibt die mit diesem Element verknüpfte Medienkennung zurück. Diese ID wird festgelegt, wenn das Element mit MediaPlayerItemLoader.load geladen wird. |
