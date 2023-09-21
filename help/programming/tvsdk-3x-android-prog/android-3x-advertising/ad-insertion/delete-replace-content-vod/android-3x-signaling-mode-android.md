---
description: Sie können Zeitbereiche in VOD-Streams markieren, löschen und ersetzen, indem Sie verschiedene Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten verwenden. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.
title: Auswirkungen auf Anzeigeneinfügung und -löschung im Anzeigenanzeigemodus und auf Anzeigenmetadaten-Kombinationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Auswirkungen auf Anzeigeneinfügung und -löschung im Anzeigenanzeigemodus und auf Anzeigenmetadaten-Kombinationen {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Sie können Zeitbereiche in VOD-Streams markieren, löschen und ersetzen, indem Sie verschiedene Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten verwenden. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.

>[!TIP]
>
>Wenn es einen Konflikt zwischen Zeitbereichen und Anzeigenanzeigemodi gibt, gibt TVSDK den Zeitbereichen Priorität.

Die folgende Tabelle enthält Details zum Verhalten der Signalmethode und der Metadaten-Kombination:

**Serverzuordnung**

| **Anzeigenmetadaten** | **Erstellte Resolver** | **`PlacementInformations`created** | **Resultierendes Verhalten** |
|--- |--- |--- |--- |
|  | Löschen | Löschen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Gelöschte Bereiche |
| Löschen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE),` <br>`PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Gelöschte Bereiche, eingefügte Anzeigen |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Hinzugefügte Anzeigen |
| Ersetzen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Ersetzte Bereiche |
| Mark | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
| Mark, Auditude | CustomAd, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Bereiche markiert, keine Anzeigen eingefügt |

**Manifestfälle**

| Anzeigenmetadaten | Erstellte Resolver | `PlacementInformations` created | Resultierendes Verhalten |
|--- |--- |--- |--- |
| Auditude | Auditude | `PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Hinzugefügte Anzeigen |
| Löschen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)`<br>`PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Entfernte Bereiche, eingefügte Anzeigen |
| Mark, Auditude | Mark, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Bereiche markiert, keine Anzeigen eingefügt |
| Löschen | Löschen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Gelöschte Bereiche |
| Mark | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
| Ersetzen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Ersetzte Bereiche |

**Benutzerdefinierter Zeitraum**

| Anzeigenmetadaten | Erstellte Resolver | `PlacementInformations` created | Resultierendes Verhalten |
|--- |--- |--- |--- |
| Löschen | Löschen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Gelöschte Bereiche |
| Löschen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Gelöschte Bereiche, keine Anzeigen eingefügt |
| Auditude | Auditude | Keines | Keine Anzeigen eingefügt |
| Ersetzen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Durch Anzeigen ersetzte Bereiche |
| Mark | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
| Mark, Auditude | Benutzerspezifische Anzeige, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Bereiche markiert, keine Anzeigen eingefügt |

**Nicht festgelegt (Standard)**

| Anzeigenmetadaten | Erstellte Resolver | `PlacementInformations` created | Resultierendes Verhalten |
|--- |--- |--- |--- |
| Löschen | Löschen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Gelöschte Bereiche |
| Löschen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Entfernte Bereiche, eingefügte Anzeigen |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Hinzugefügte Anzeigen |
| Ersetzen, Auditude | Löschen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Durch Anzeigen ersetzte Bereiche |
| Mark | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
| Mark, Auditude | CustomAd, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Markierte Bereiche |
