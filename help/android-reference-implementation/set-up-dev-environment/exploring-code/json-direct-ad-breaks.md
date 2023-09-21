---
title: JSON-Objekt für direkte Werbeunterbrechungen
description: Details zum JSON-Objekt, wenn der Typwert eine direkte Anzeige umbricht
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# JSON-Objekt für direkte Werbeunterbrechungen{#json-object-for-direct-ad-breaks}

Der folgende Codeblock definiert das Details-JSON-Objekt, wenn der Typwert direkte Werbeunterbrechungen ist.

Die `MetadataNode` zurückgegeben `IFeedItemAdapter:getStreamMetadata()` enthält einen Eintrag mit Schlüssel vom Typ `com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY` und -Wert einer Zeichenfolgendarstellung des JSON-Objektwerts für Details unten.

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
| `tag` | Eine Zeichenfolge, die dem Tag-Feld in `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `time` | Gibt die Startzeit der Werbeunterbrechung an, die dem Zeitfeld unter `com.adobe.mediacore.timeline.advertising.AdBreak`. Der Wert 0 zeigt eine Pre-Roll-Anzeige an. |
| `replace` | Gibt die Dauer der Anzeigenunterbrechung an, die dem `replaceDuration` -Feld in `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `ad-list` | Eine Liste der Anzeigen, die während der Werbeunterbrechung abgespielt werden sollen, wird der `List<Ad>` -Feld in `com.adobe.mediacore.timeline.advertising.AdBreak`. |

Der folgende Codeblock definiert das JSON-Objekt für das Ad-List-Array.

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
| `url` | Die URL zum Anzeigeninhalt, wird dem URL-Feld in zugeordnet. `com.adobe.mediacore.timeline.advertising.Ad`. |
| `duration` | Die Dauer der Anzeige wird dem Feld Dauer in zugeordnet. `com.adobe.mediacore.timeline.advertising.Ad`. |
| `tag` | Eine Beschreibungszeichenfolge. |
