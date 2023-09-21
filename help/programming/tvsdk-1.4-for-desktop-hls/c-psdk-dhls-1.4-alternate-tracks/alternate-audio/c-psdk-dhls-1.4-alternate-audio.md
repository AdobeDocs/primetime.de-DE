---
description: Mit alternativem oder spätbindendem Audio können Sie zwischen verfügbaren Audiospuren für einen Videospur wechseln. Auf diese Weise können Benutzer eine Sprachspur auswählen, wenn das Video wiedergegeben wird.
title: Alternativaudio
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Alternativaudio{#alternate-audio}

Mit alternativem oder spätbindendem Audio können Sie zwischen verfügbaren Audiospuren für einen Videospur wechseln. Auf diese Weise können Benutzer eine Sprachspur auswählen, wenn das Video wiedergegeben wird.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Wenn TVSDK die `MediaPlayerItem` -Instanz für das aktuelle Video erstellt sie eine `AudioTrack` -Element für jeden verfügbaren Audio-Track. Das Element enthält eine `name` -Eigenschaft, eine Zeichenfolge, die normalerweise eine benutzererkennbare Beschreibung der Sprache dieser Verfolgung enthält. Das Element enthält auch Informationen darüber, ob diese Verfolgung standardmäßig verwendet werden soll.

Wenn es Zeit ist, das Video abzuspielen, können Sie nach einer Liste der verfügbaren Audiospuren fragen, den Benutzer optional eine auswählen und das Video mit dem ausgewählten Track abspielen lassen.

Obwohl selten, wenn ein zusätzlicher Audio-Track verfügbar wird, nachdem er die `MediaPlayerItem`, gibt TVSDK eine `MediaPlayerItem.AUDIO_UPDATED` -Ereignis.

## APIs hinzugefügt {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

Die folgenden APIs wurden hinzugefügt, um alternative Audio zu unterstützen:

`hasAlternateAudio`

Wenn das angegebene Medium über eine andere Audiospur als die Standardspur verfügt, gibt diese boolesche Funktion `true`. Wenn kein alternativer Audio-Track vorhanden ist, gibt die Funktion `false`.

```
bool MediaPlayerItemImpl::hasAlternateAudio() const { 
    return _hasAlternateAudio; 
}
```

** `getAudioTracks`**

Diese Funktion gibt eine Liste aller derzeit verfügbaren Audiospuren in einem angegebenen Medium zurück.

```
virtual PSDKErrorCode getAudioTracks(PSDKImmutableArray<AudioTrack>*& out) const { 
    if (_audioTracks) { 
        out = _audioTracks; 
        out->addRef(); 
        return kECSuccess; 
    } 
    return kECDataNotAvailable; 
} 
```

`getSelectedAudioTrack`

Diese Funktion gibt die derzeit ausgewählte alternative Audiospur und Eigenschaften wie Sprache zurück. Auch die automatische Auswahl von Track kann extrahiert werden.

```
PSDKErrorCode MediaPlayerItemImpl::getSelectedAudioTrack(AudioTrack &out) const { 
    out = _currentAudioTrack; 
    return kECSuccess; 
}
```

`selectAudioTrack`

Diese Funktion wählt einen alternativen Audiotrack zur Wiedergabe aus.

```
PSDKErrorCode MediaPlayerItemImpl::selectAudioTrack(const AudioTrack &audioTrack) { 
    _lastPlayedAudioTrack = _currentAudioTrack; 
    if(_mediaPlayer && _mediaPlayer->_trickPlay) 
        return kECUnsupportedOperation; 
    _currentAudioTrack = audioTrack; 
    PSDKErrorCode result = kECSuccess; 
    if (_currentAudioTrack) { 
        media::TimeLine* timeline = NULL; 
        if (_mediaPlayer->_fragHttpStreamer) 
            _mediaPlayer->_fragHttpStreamer->GetTimeLine(&timeline); 
        if (timeline) { 
            for (int32_t i = timeline->GetFirstPeriodIndex(); i <= timeline->GetLastPeriodIndex(); i++){ 
                media::ErrorCode error = selectTrack(timeline,_mediaPlayer->_fragHttpStreamer, i, audioTrack.getName(), media::kSTTAudioIndex); 
                return _mediaPlayer->convertToPSDKError(error); 
            } 
        } 
    }   
    return result; 
}
```
