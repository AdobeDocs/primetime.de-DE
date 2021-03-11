---
description: Die Funktion für das Einfügen von Werbeunterbrechungen (Partial Ad Break Insertion, PABI) imitiert ein TV-ähnliches Erlebnis, bei dem der Benutzer, wenn er einem Live-Stream in einer Mid-Roll-Unterbrechung beitritt, Mid-Roll-Anzeigen anstelle einer Pre-Roll-Anzeige oder einer Tonschiefer angezeigt wird.
title: Einfügen eines Teilformulars mit Werbeunterbrechung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Einfügen eines Werbeunterbrechungssatzes {#partial-ad-break-insertion}

Die Funktion für das Einfügen von Werbeunterbrechungen (Partial Ad Break Insertion, PABI) imitiert ein TV-ähnliches Erlebnis, bei dem der Benutzer, wenn er einem Live-Stream in einer Mid-Roll-Unterbrechung beitritt, Mid-Roll-Anzeigen anstelle einer Pre-Roll-Anzeige oder einer Tonschiefer angezeigt wird.

Wenn der Anzeigenserver Pre-Roll-Anzeigen für einen Live-Stream zurückgibt, injiziert der Manifestserver die Pre-Roll-Werbeunterbrechung vor dem Live-Point und fügt das EXT-X-BEGINN-Tag mit dem TIMEOFFSET-Wert ein, der auf den Beginn der Pre-Roll-Werbeunterbrechung verweist. Dieses Standardverhalten stellt sicher, dass die gesamte Pre-Roll-Werbeunterbrechung vor dem Inhalt am Live-Point wiedergegeben wird. Wenn ein Benutzer einem Stream beitritt, wenn sich der Live-Point in der Nähe einer Mid-Roll-Werbeunterbrechung befindet, wird dem Benutzer die Pre-Roll-Werbeunterbrechung vor der Mid-Roll-Werbeunterbrechung am Live-Point angezeigt.

Die PABI-Funktion weist den Manifestserver an, die Pre-Roll-Werbeunterbrechung zu ignorieren und den Wert EXT-X-BEGINN:TIMEOFFSET auf den Anfang der Mid-Roll-Anzeige am Live-Point festzulegen. Dadurch wird sichergestellt, dass der Benutzer die gesamte derzeit am Live-Point wiedergegebene Mid-Roll-Anzeige sieht, ohne dass die Pre-Roll-Werbeunterbrechung Ansicht werden muss.

>[!NOTE]
>
>Diese Funktion ist nur für Live-Streams verfügbar. Der Manifestserver fügt die Pre-Roll-Werbeunterbrechung standardmäßig an der VOD-Wiedergabeliste ein.

>[!NOTE]
>
>Um PABI zu aktivieren, müssen Sie die [Abfrage_params](/help/primetime-ad-insertion/~old-msapi-topics/ms-getting-started/ms-api-query-params.md) in der Bootstrap-URL angeben.

>[!NOTE]
>
>Der [EXT-X-BEGINN](https://tools.ietf.org/html/rfc8216#section-4.3.5.2) ist ein Standard-HLS-Tag, das einen bevorzugten Startpunkt in der Wiedergabeliste angibt.

## Recommendations {#section_4CF0733B14504F2A99690310B9F3B130}

* Verwenden Sie die clientseitige Verfolgung, da der Client mehr Kontrolle über das Auslösen von Tracking-Beacons hat.
* Teilweise Werbeunterbrechungen sollten nur mit dem serverseitigen Verfolgungsmodus verwendet werden, wenn der Player EXT-X-BEGINN unterstützt.