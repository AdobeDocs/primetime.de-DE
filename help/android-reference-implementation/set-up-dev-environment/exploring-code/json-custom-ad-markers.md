---
title: JSON-Objekt für benutzerdefinierte Anzeigenmarken
description: JSON-Objekt für benutzerdefinierte Anzeigenmarken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# JSON-Objekt für benutzerdefinierte Anzeigenmarken {#json-object-for-custom-ad-markers}

Der unten stehende Codeblock definiert das JSON-Objekt &quot;details&quot;, wenn der Typ benutzerdefinierte Anzeigenmarken ist.

Der von IFeedItemAdapter:getStreamMetadata() zurückgegebene MetadataNode enthält 2 Einträge:
1. ein Eintrag mit dem Schlüssel des Typs `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` und dem Wert einer Instanz des MetadataNode, die von `TimeRangeCollection.toMetadata()` zurückgegeben wird.
1. Der zweite Eintrag hat einen Schlüssel vom Typ `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` mit dem Wert des unten stehenden Attributs *adapt-search-position*.

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
| time-ranges.begin | Der Wert in ms gibt die Beginn-Zeit der Anzeigenmarke an. |
| time-ranges.end | Wert in ms, der die Endzeit der Anzeigenmarke angibt. |

Weitere Informationen zur Funktionsweise von benutzerdefinierten Anzeigenmarken finden Sie in der TVSDK-Dokumentation.
