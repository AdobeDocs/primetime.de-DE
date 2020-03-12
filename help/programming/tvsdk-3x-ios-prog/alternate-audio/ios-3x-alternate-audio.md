---
seo-title: Alternativaudio
title: Alternativaudio
uuid: cc38ded2-45b7-4be4-8f46-a919fdaf79cf
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Alternativaudio {#alternate-audio}

Mit alternativem oder spätgebundenem Audio können Sie zwischen den verfügbaren Audiospuren für eine Videospur wechseln. Auf diese Weise können Benutzer beim Abspielen des Videos eine Sprachspur auswählen.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Wenn TVSDK die `MediaPlayerItem` Instanz für das aktuelle Video erstellt, wird für jede verfügbare Audiospur ein `AudioTrack` Element erstellt. Das Element enthält eine `name` Eigenschaft, eine Zeichenfolge, die in der Regel eine benutzererkennbare Beschreibung der Sprache dieser Verfolgung enthält. Das Element enthält auch Informationen darüber, ob diese Verfolgung standardmäßig verwendet werden soll.

Wenn es Zeit ist, das Video abzuspielen, können Sie nach einer Liste der verfügbaren Audiospuren fragen, optional eine Audiospur auswählen und das Video mit der ausgewählten Spur abspielen lassen.

Obwohl dies selten der Fall ist, löst TVSDK ein `MediaPlayerItem``MediaPlayerItem.AUDIO_UPDATED` Ereignis aus, wenn eine zusätzliche Audiospur verfügbar ist, nachdem sie erstellt wurde.

## APIs hinzugefügt {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

Die folgenden APIs wurden hinzugefügt, um alternative Audio zu unterstützen:

**hasAlternateAudio**

Wenn das angegebene Medium über eine andere Audiospur als die Standardspur verfügt, gibt diese boolesche Funktion zurück `true`. Wenn keine alternative Audiospur vorhanden ist, gibt die Funktion zurück `false`.

```
bool MediaPlayerItemImpl::hasAlternateAudio() const { 
    return _hasAlternateAudio; 
}
```

**getAudioTracks**

Diese Funktion gibt die Liste aller aktuell verfügbaren Audiospuren in einem angegebenen Medium zurück.

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

**getSelectedAudioTrack**

Diese Funktion gibt die derzeit ausgewählte alternative Audiospur und Eigenschaften wie Sprache zurück. Die automatische Auswahl der Spur kann ebenfalls extrahiert werden.

```
PSDKErrorCode MediaPlayerItemImpl::getSelectedAudioTrack(AudioTrack &out) const { 
    out = _currentAudioTrack; 
    return kECSuccess; 
}
```

**selectAudioTrack**

Diese Funktion wählt eine alternative Audiospur für die Wiedergabe aus.

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
