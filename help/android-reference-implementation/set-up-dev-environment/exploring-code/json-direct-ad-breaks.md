---
seo-title: JSON-Objekt für direkte Werbeunterbrechungen
title: JSON-Objekt für direkte Werbeunterbrechungen
uuid: ffb901f4-0a8b-40fe-b6ba-5ffebc324cf2
description: Details zum JSON-Objekt, wenn der Typwert "Direktwerbung"lautet
seo-description: Details zum JSON-Objekt, wenn der Typwert "Direktwerbung"lautet
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# JSON-Objekt für direkte Werbeunterbrechungen{#json-object-for-direct-ad-breaks}

Der folgende Codeblock definiert das Details-JSON-Objekt, wenn der Typwert direkte Werbeunterbrechungen ist.

Die `MetadataNode` zurückgegebene `IFeedItemAdapter:getStreamMetadata()` Datei enthält einen Eintrag mit Schlüssel vom Typ `com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY` und Wert einer Zeichenfolgen-Darstellung der Details JSON-Objektwert unten.

```
“metadata”: { 
    “ad” :  { 
        “type”: “direct ad breaks”, 
        “details”: { 
            "ad-breaks": [ 
                { 
                    "tag": "break-001", 
                    "time": 0, 
                    "replace": 0, 
                    "ad-list": [ 
                        { 
                        }, 
                        { 
                        } 
                    ] 
                }, 
                { 
                    "tag": "break-002", 
                    "time": 300000, 
                    "replace": 0, 
                    "ad-list": [ 
                        { 
                        } 
                    ] 
                } 
            ] 
        } 
    } 
} 
```

| Eigenschaft | Beschreibung |
|---|---|
| `tag` | Eine Zeichenfolge, die dem Tag-Feld in `com.adobe.mediacore.timeline.advertising.AdBreak`zugeordnet wird. |
| `time` | Gibt die Beginn-Zeit für den Werbeunterbrechungsvorgang an und ordnet sie dem Zeitfeld in `com.adobe.mediacore.timeline.advertising.AdBreak`zu. Der Wert 0 bedeutet eine Pre-Roll-Anzeige. |
| `replace` | Gibt die Dauer des Anzeigenumbruchs an, die dem `replaceDuration` Feld in zugeordnet wird `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `ad-list` | Eine Liste von Anzeigen, die während der Werbeunterbrechung abgespielt werden sollen, wird dem `List<Ad>` Feld in zugeordnet `com.adobe.mediacore.timeline.advertising.AdBreak`. |

Der folgende Codeblock definiert das JSON-Objekt für das Array &quot;ads-Liste&quot;.

```
"ad-list": [ 
    { 
        "url": "https://cdn.auditude.com/player/downloads/data/espn/ads/csx/prog_index.m3u8", 
        "duration": 15000, 
        "tag": "1st break - 1st ad" 
    }, 
    { 
        "url": "https://cdn.auditude.com/player/downloads/data/espn/ads/csx/prog_index.m3u8", 
        "duration": 30000, 
        "tag": "1st break - 2nd ad" 
    } 
], 
```

| Eigenschaft | Beschreibung |
|---|---|
| `url` | Die URL zum Anzeigeninhalt ordnet dem URL-Feld in `com.adobe.mediacore.timeline.advertising.Ad`zu. |
| `duration` | Die Dauer der Anzeige wird dem Feld für die Dauer zugeordnet `com.adobe.mediacore.timeline.advertising.Ad`. |
| `tag` | Eine Beschreibungszeichenfolge. |

