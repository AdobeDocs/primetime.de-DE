---
description: Sie können Zeitbereiche in VOD-Streams mit unterschiedlichen Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten markieren, löschen und ersetzen. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.
title: Auswirkungen auf Kombinationen aus Anzeigeneinfügung und -löschung im Anzeigensignalisierungsmodus und Anzeigenmetadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Auswirkungen auf das Einfügen und Löschen von Anzeigen im Anzeigensignalisierungsmodus und auf Kombinationen von Anzeigenmetadaten {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Sie können Zeitbereiche in VOD-Streams mit unterschiedlichen Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten markieren, löschen und ersetzen. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.

>[!TIP]
>
>Bei einem Konflikt zwischen Zeitbereichen und Anzeigensignalisierungsmodi gibt TVSDK den Zeitbereichen Priorität.

Die folgende Tabelle enthält Details zum Verhalten der Kombination aus Signalmodus und Metadaten:

**Serverzuordnung**

| **Anzeigenmetadaten** | **Erstellte Auflösungen** | **`PlacementInformations`erstellt** | **Ergebnis** |
|--- |--- |--- |--- |
|  | Löschen | Löschen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Bereiche gelöscht |
| Löschen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE),` <br>`PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Bereiche gelöscht, Anzeigen eingefügt |
| Zielgruppe | Zielgruppe | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Eingefügte Anzeigen |
| Ersetzen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Ersetzte Bereiche |
| Markierung | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
| Mark, Auditude | CustomAd, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche, keine eingefügten Anzeigen |

**Manifestfarben**

| Anzeigenmetadaten | Erstellte Auflösungen | `PlacementInformations` erstellt | Ergebnis |
|--- |--- |--- |--- |
| Zielgruppe | Zielgruppe | `PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Eingefügte Anzeigen |
| Löschen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)`<br>`PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Bereiche gelöscht, Anzeigen eingefügt |
| Mark, Auditude | Mark, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche, keine eingefügten Anzeigen |
| Löschen | Löschen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Bereiche gelöscht |
| Markierung | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
| Ersetzen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Ersetzte Bereiche |

**Benutzerdefinierter Zeitraum**

| Anzeigenmetadaten | Erstellte Auflösungen | `PlacementInformations` erstellt | Ergebnis |
|--- |--- |--- |--- |
| Löschen | Löschen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Bereiche gelöscht |
| Löschen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Bereiche gelöscht, keine Anzeigen eingefügt |
| Zielgruppe | Zielgruppe | Keines | Keine Anzeigen eingefügt |
| Ersetzen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Bereiche durch Anzeigen ersetzt |
| Markierung | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
| Mark, Auditude | Benutzerspezifische Anzeige, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche, keine eingefügten Anzeigen |

**Nicht festgelegt (Standard)**

| Anzeigenmetadaten | Erstellte Auflösungen | `PlacementInformations` erstellt | Ergebnis |
|--- |--- |--- |--- |
| Löschen | Löschen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Bereiche gelöscht |
| Löschen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Bereiche gelöscht, Anzeigen eingefügt |
| Zielgruppe | Zielgruppe | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Eingefügte Anzeigen |
| Ersetzen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Bereiche durch Anzeigen ersetzt |
| Markierung | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
| Mark, Auditude | CustomAd, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |