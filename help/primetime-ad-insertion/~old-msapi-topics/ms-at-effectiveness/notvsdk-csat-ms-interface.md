---
description: Verwenden Sie die optionalen Parameter pttrackingmode, pttrackingversion und pttrackingposition zur Abfrage, um URLs abzurufen, an die Anzeigenverfolgungsinformationen zum aktuellen Video gesendet werden sollen. Die Antworten variieren je nach Verfolgungsversion und je nachdem, ob der Videostream live oder on-Demand (VOD) ist.
title: API für Player zur Interaktion mit dem Manifestserver
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# API für Player zur Interaktion mit dem Manifestserver {#api-for-players-to-interact-with-the-manifest-server}

Verwenden Sie die optionalen Parameter `pttrackingmode`, `pttrackingversion` und `pttrackingposition` für die Abfrage, um URLs abzurufen, an die Anzeigenverfolgungsinformationen zum aktuellen Video gesendet werden sollen. Die Antworten variieren je nach Verfolgungsversion und je nachdem, ob der Videostream live oder on-Demand (VOD) ist.

## Abfrage Parameters {#query-parameters}

**pttrackingmode**

Beispiel: `pttrackingmode=simple`
Wenn Sie einfach angeben, teilt dem Manifestserver mit, dass Sie Verfolgungsinformationen erhalten möchten.
Geben Sie es in einer Anforderung an, um das M3U8 abzurufen, bevor Sie Verfolgungsinformationen anfordern. Wenn Sie es nicht angeben, gibt der Manifestserver Verfolgungsinformationen in den #EXT-X-MARKER-Tags zurück.
Wenn Sie einen anderen gültigen Wert als einfache angeben, wird die serverseitige Verfolgung aufgerufen.

**pttrackingversion**

Beispiel: `pttrackingversion=v2`
Dieser Parameter teilt dem Manifestserver mit, welches Format zur Rückgabe von Verfolgungsinformationen verwendet werden soll (siehe [Dateiformate](/help/primetime-ad-insertion/~old-msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).
Geben Sie es bei einer Anforderung an, um das M3U8 abzurufen, bevor Sie Verfolgungsinformationen anfordern. Wenn Sie keinen Wert angeben oder einen ungültigen Wert angeben, verwendet der Manifestserver Version 1.

**pttrackingposition**

Beispiel: `pttrackingposition`
Dieser Parameter weist den Manifestserver an, Verfolgungsinformationen des Videos als JSON- oder VMAP-Objekt in der Datei M3U8 zurückzugeben. Der Manifestserver ignoriert den angegebenen Wert und sendet alle Verfolgungsinformationen, die er für diese Sitzung hat. Wenn kein Wert übergeben wird, gibt der Manifestserver die angeforderte M3U8-Datei zurück.
