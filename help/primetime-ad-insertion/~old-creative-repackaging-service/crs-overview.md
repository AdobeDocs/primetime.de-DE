---
description: Der Kreativ-Umpackungsdienst (CRS) stellt sicher, dass ein Nicht-HLS-Anzeigenkreativ in HLS-Streams ordnungsgemäß wiedergegeben werden kann. Der Manifestserver ruft CRS auf, wenn eine Nicht-HLS-Anzeige auftritt.
seo-description: Der Kreativ-Umpackungsdienst (CRS) stellt sicher, dass ein Nicht-HLS-Anzeigenkreativ in HLS-Streams ordnungsgemäß wiedergegeben werden kann. Der Manifestserver ruft CRS auf, wenn eine Nicht-HLS-Anzeige auftritt.
seo-title: Übersicht über CRS
title: Übersicht über CRS
uuid: 3ae75fa7-397f-47ba-8e3d-50543ca25458
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# Übersicht über CRS {#overview-of-crs}

Der Kreativ-Umpackungsdienst (CRS) stellt sicher, dass ein Nicht-HLS-Anzeigenkreativ in HLS-Streams ordnungsgemäß wiedergegeben werden kann. Der Manifestserver ruft CRS auf, wenn eine Nicht-HLS-Anzeige auftritt.

>[!NOTE]
>
>CRS ist standardmäßig deaktiviert. Wenden Sie sich an Ihren Kundenbetreuer, um CRS für Ihr Adobe zu aktivieren.
>
>Informationen zum Aktivieren von CRS in TVSDK-Apps finden Sie im Thema *Aktivieren von CRS in TVSDK-Anwendungen* im Programmierhandbuch für Ihre Plattform. Beispiel für Android 3.4 finden Sie unter [Aktivieren von CRS in TVSDK-Anwendungen](../../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-transcoding/android-3x-ad-transcoding.md)

CRS bereitet das HTTP Live Streaming (HLS) und seine kreativen Elemente für den Inhaltsstream vor und fügt ID3-Pakete für die clientseitige Anzeigenverfolgung ein. Es transkodiert MP4-, FLV- und WebM-Dateien, die von Werbeservern, Werbenetzwerken und Agenturservern von Drittanbietern empfangen wurden, in das HLS-Format.

Wenn beim Einfügen von Adobe Primetime-Anzeigen ein Nicht-HLS-Anzeigenkreativ auftritt, wird es zur Neuverpackung an CRS gesendet, was in der Regel nicht länger als drei Minuten dauert. CRS sendet das transkodierte Werbekreativelement zur zukünftigen Verwendung an den CDN-Server. Dies heißt **`just-in-time (JIT) repackaging`**. Sie können Werbeinhalte auch vor Bedarf mit der [Neu verpacken-API](../../primetime-ad-insertion/~old-creative-repackaging-service/api-repackage.md) transkodieren. Dies heißt *`asynchronous repackaging`*.

Ihr technischer Kundenbetreuer für Adoben kann auch einige Standardverhalten von CRS ändern, wenn ein anderes Verhalten besser für Ihre Anwendung geeignet ist. Diese sind:

* Priorität von Werbeformaten.

   Der Abschnitt `MediaFiles` einer VAST/VMAP-Antwort kann kreative Elemente mit verschiedenen `MediaFile`-Typen enthalten. Standardmäßig wählt der Manifestserver eine Auswahl gemäß einem festen Satz von Prioritäten ( `application/x-mpegURL`, `application/vnd.apple.mpegURL`, `video/mp4`, `video/x-flv,video/webm`). Adobe kann die Prioritäten für Ihr Konto ändern.
* Dauer der Zielgruppe der Anzeige.

   Der Manifestserver erkennt die Zielgruppen- und Anzeigedauer aus der Inhaltswiedergabeliste und sendet sie an das CRS. Adobe kann dieses Verhalten ändern, sodass CRS immer eine feste Dauer verwendet, die Sie für Ihr Konto angeben.
