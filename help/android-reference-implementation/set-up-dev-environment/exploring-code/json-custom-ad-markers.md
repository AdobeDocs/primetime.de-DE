---
title: JSON-Objekt für benutzerdefinierte Anzeigenmarken
description: JSON-Objekt für benutzerdefinierte Anzeigenmarken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# JSON-Objekt für benutzerdefinierte Anzeigenmarken {#json-object-for-custom-ad-markers}

Der folgende Codeblock definiert das JSON-Objekt &quot;Details&quot;, wenn es sich bei dem Typ um benutzerdefinierte Anzeigenmarken handelt.

Der von IFeedItemAdapter:getStreamMetadata() zurückgegebene MetadataNode enthält 2 Einträge:
1. einen Eintrag mit Schlüssel vom Typ `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` und Wert einer Instanz des MetadataNode, die von `TimeRangeCollection.toMetadata()`.
1. Der zweite Eintrag hat einen Schlüssel vom Typ `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` mit dem Wert der *adapt-search-position* -Attribut.

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
| adapt-search-position | true oder false, wird verwendet, um den Wert des Schlüssels com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED im MetadataNode festzulegen. |
| Zeitbereiche | Ein Array von JSON-Objekten, die den Zeitraum für jede Anzeigenmarke angeben. Jeder JSON-Objekteintrag wird einer Instanz von com.adobe.mediacore.utils.TimeRange zugeordnet. |
| time-ranges.begin | Wert in ms, der die Startzeit der Anzeigenmarkierung angibt. |
| time-ranges.end | Wert in ms, der die Endzeit der Anzeigenmarkierung angibt. |

Weitere Informationen zur Funktionsweise von benutzerdefinierten Anzeigenmarken finden Sie in der TVSDK-Dokumentation .
