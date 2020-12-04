---
description: Um Benachrichtigungen über Tags im Manifest zu erhalten, müssen Sie die entsprechenden Ereignis-Listener implementieren.
seo-description: Um Benachrichtigungen über Tags im Manifest zu erhalten, müssen Sie die entsprechenden Ereignis-Listener implementieren.
seo-title: hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
title: hinzufügen Listener für zeitgesteuerte Metadaten-Benachrichtigungen
uuid: bb996b4a-282e-4321-a9e9-513f0df45b70
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# hinzufügen Listener für zeitgesteuerte Metadatenbenachrichtigungen {#add-listeners-for-timed-metadata-notifications}

Um Benachrichtigungen über Tags im Manifest zu erhalten, müssen Sie die entsprechenden Ereignis-Listener implementieren.

Sie können zeitgesteuerte Metadaten überwachen, indem Sie nach `onTimedMetadata` suchen, die Ihre Anwendung über die entsprechende Aktivität informieren. Jedes Mal, wenn während der Analyse des Inhalts ein eindeutiges abonniertes Tag identifiziert wird, bereitet TVSDK ein neues `TimedMetadata`-Objekt vor und löst dieses Ereignis aus. Das Objekt enthält den Namen des Tags, für das Sie ein Abonnement abgeschlossen haben, die lokale Zeit in der Wiedergabe, in der dieses Tag angezeigt wird, und andere Daten.

Hör auf Ereignisse!

```java
private final TimedMetadataEventListener timedMetadataEventListener = new TimedMetadataEventListener() { 
    @Override 
    public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { 
        TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata(); 
 
        TimedMetadata.Type type = timedMetadata.getType(); 
        if (type.equals(TimedMetadata.Type.ID3)){ 
            Metadata metadata = timedMetadata.getMetadata(); 
            Set<String> keys = metadata.keySet(); 
            for (String key : keys) { 
                String value = metadata.getValue(key); 
            } 
        } else if (_mediaPlayer.getPlaybackRange() != null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
            displayRanges(); 
        } 
    } 
}; 
```

ID3-Metadaten verwenden denselben `onTimedMetadata`-Listener, um das Vorhandensein eines ID3-Tags anzugeben. Dies sollte jedoch keine Verwirrung stiften, da Sie mit der `TimedMetadata` `type`-Eigenschaft zwischen TAG und ID3 unterscheiden können. Weitere Informationen zu ID3-Tags finden Sie unter [ID3-Tags](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-id3-metadata-retrieve.md).