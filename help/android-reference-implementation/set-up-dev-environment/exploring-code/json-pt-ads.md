---
title: JSON-Objekt für Primetime-Anzeigen
description: Der nachstehende Codeblock definiert das JSON-Detailobjekt, wenn der Typwert Primetime-Anzeigen ist.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# JSON-Objekt für Primetime-Anzeigen {#json-object-for-primetime-ads}

Der nachstehende Codeblock definiert das JSON-Detailobjekt, wenn der Typwert Primetime-Anzeigen ist.

```
“metadata”: {
    “ad” :  {
        “type”: “Primetime ads”,
        “details”: {
            "domain": "sandbox2.auditude.com",
            "mediaid": "rom_asset_case_1",
            "zoneid": "109754",
            "targeting": [
                {
                    "key": "osmfKeyMulAdsAvail12346",
                    "value": "MulAdsAvail12346"
                }
            ]
        }
    }
}
```

| Eigenschaft | Beschreibung |
|---|---|
| domain | Die Primetime-Anzeigendomäne, die für Anzeigenanfragen verwendet werden soll. |
| mediaid | Das Mediaid, das in Primetime-Anzeigen für diesen Inhalt eingerichtet wurde. |
| zoneid | Primetime weist zoneid an. Weitere Informationen finden Sie in der Dokumentation zu Primetime-Anzeigen . |
| Targeting | Ein Array von Schlüssel/Wert-Paaren, die für das Targeting bestimmter Anzeigen für den Inhalt verwendet werden. |

Siehe [com.adobe.mediacore.metadata.AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/metadata/AuditudeSettings.html) für weitere Informationen zum Wert dieser Attribute.
