---
seo-title: JSON-Objekt für benutzerdefinierte Anzeigenmarken
title: JSON-Objekt für benutzerdefinierte Anzeigenmarken
uuid: 2c05d9ce-a22f-4829-bfea-9dcf0dc7cd6d
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# JSON-Objekt für benutzerdefinierte Anzeigenmarken {#json-object-for-custom-ad-markers}

Der unten stehende Codeblock definiert das JSON-Objekt &quot;details&quot;, wenn der Typ benutzerdefinierte Anzeigenmarken ist.

Der von IFeedItemAdapter:getStreamMetadata() zurückgegebene MetadataNode enthält 2 Einträge:
1. ein Eintrag mit Schlüssel vom Typ `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` und Wert einer Instanz des MetadataNode zurückgegeben von `TimeRangeCollection.toMetadata()`.
1. Der zweite Eintrag hat einen Schlüssel vom Typ `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` mit dem Wert des Attributs *adapt-search-position* unten.

```
“metadata”: {
    “ad” :  {
        “type”: “custom ad markers”,
        “details”: {
            "adjust-seek-position": true,
            "time-ranges": [
                {
                    "begin": 5000,
                    "end":15000
                },
                {
                    "begin": 120000,
                    "end":135000
                }
            ]
        }
    }
}
```

| Eigenschaft | Beschreibung |
|---|---|
| adapt-search-position | true oder false, verwendet, um den Wert des Schlüssels com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED im MetadataNode festzulegen. |
| Zeitbereiche | Ein Array von JSON-Objekten, das den Zeitraum für jede Anzeigenmarke angibt. Jeder JSON-Objekteintrag wird einer Instanz von com.adobe.mediacore.utils.TimeRange zugeordnet. |
| time-range.begin | Der Wert in ms gibt die Beginn-Zeit der Anzeigenmarke an. |
| time-range.end | Wert in ms, der die Endzeit der Anzeigenmarke angibt. |

Weitere Informationen zur Funktionsweise von benutzerdefinierten Anzeigenmarken finden Sie in der TVSDK-Dokumentation.
