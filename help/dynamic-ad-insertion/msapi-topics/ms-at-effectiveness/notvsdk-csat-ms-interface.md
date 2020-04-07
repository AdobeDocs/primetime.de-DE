---
description: Verwenden Sie die optionalen Parameter pttrackingmode, pttrackingversion und pttrackingposition zur Abfrage, um URLs abzurufen, an die Anzeigenverfolgungsinformationen zum aktuellen Video gesendet werden sollen. Die Antworten variieren je nach Verfolgungsversion und je nachdem, ob der Videostream live oder on-Demand (VOD) ist.
seo-description: Verwenden Sie die optionalen Parameter pttrackingmode, pttrackingversion und pttrackingposition zur Abfrage, um URLs abzurufen, an die Anzeigenverfolgungsinformationen zum aktuellen Video gesendet werden sollen. Die Antworten variieren je nach Verfolgungsversion und je nachdem, ob der Videostream live oder on-Demand (VOD) ist.
seo-title: API für Player zur Interaktion mit dem Manifestserver
title: API für Player zur Interaktion mit dem Manifestserver
uuid: ab7a19e7-6c28-4960-a56b-3b33c525e6b3
translation-type: tm+mt
source-git-commit: 32a7901e3061cca03f1f1fa5ab06f5bb950d248a

---


# API für Player zur Interaktion mit dem Manifestserver {#api-for-players-to-interact-with-the-manifest-server}

Verwenden Sie die optionalen Parameter `pttrackingmode`, `pttrackingversion`und `pttrackingposition` Abfrage, um URLs abzurufen, an die Sie die Anzeigenverfolgungsinformationen zum aktuellen Video senden können. Die Antworten variieren je nach Verfolgungsversion und je nachdem, ob der Videostream live oder on-Demand (VOD) ist.

## Abfrage-Parameter {#query-parameters}

**pttrackingmode**-Beispiel: pttrackingmode=simpleAngeben von simple teilt dem Manifestserver mit, dass Sie Verfolgungsinformationen haben möchten.
Geben Sie es in einer Anforderung an, um das M3U8 abzurufen, bevor Sie Verfolgungsinformationen anfordern. Wenn Sie es nicht angeben, gibt der Manifestserver Verfolgungsinformationen in den #EXT-X-MARKER-Tags zurück.
Wenn Sie einen anderen gültigen Wert als einfache angeben, wird die serverseitige Verfolgung aufgerufen.

**pttrackingversion**-Beispiel: pttrackingversion=v2Dieser Parameter teilt dem Manifestserver mit, welches Format zur Rückgabe von Verfolgungsinformationen verwendet werden soll (siehe [Dateiformate](../../msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).
Geben Sie es bei einer Anforderung an, um das M3U8 abzurufen, bevor Sie Verfolgungsinformationen anfordern. Wenn Sie keinen Wert angeben oder einen ungültigen Wert angeben, verwendet der Manifestserver Version 1.

**pttrackingposition**-Beispiel: pttrackingpositionDieser Parameter weist den Manifestserver an, Verfolgungsinformationen des Videos als JSON- oder VMAP-Objekt in der Datei M3U8 zurückzugeben. Der Manifestserver ignoriert den angegebenen Wert und sendet alle Verfolgungsinformationen, die er für diese Sitzung hat. Wenn kein Wert übergeben wird, gibt der Manifestserver die angeforderte M3U8-Datei zurück.
