---
title: JSON-Objekt für Primetime-Anzeigen
description: Der Codeblock unten definiert das Details-JSON-Objekt, wenn der Typwert Primetime-Anzeigen ist.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---


# JSON-Objekt für Primetime-Anzeigen {#json-object-for-primetime-ads}

Der Codeblock unten definiert das Details-JSON-Objekt, wenn der Typwert Primetime-Anzeigen ist.

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
| domain | Die Primetime-Anzeigendomäne, die für Anzeigenanforderungen verwendet wird. |
| mediaid | Das Mediaid, das in Primetime-Anzeigen für diesen Inhalt eingerichtet wurde. |
| zoneid | Die Primetime-Anzeigenzone. Weitere Informationen finden Sie in der Dokumentation zu Primetime-Anzeigen. |
| Targeting | Ein Array mit Schlüssel/Wert-Paaren, die für das Targeting bestimmter Anzeigen für den Inhalt verwendet werden. |

Weitere Informationen zum Wert dieser Attribute finden Sie unter [com.adobe.mediacore.metadata.AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/metadata/AuditudeSettings.html).