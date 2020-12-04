---
description: Eine MediaResource stellt den Inhalt dar, der demnächst von der MediaPlayer-Instanz geladen wird.
seo-description: Eine MediaResource stellt den Inhalt dar, der demnächst von der MediaPlayer-Instanz geladen wird.
seo-title: MediaPlayer- und MediaResource-Klassen
title: MediaPlayer- und MediaResource-Klassen
uuid: 36ef75f3-08f7-4fc5-88a7-9bab9198b917
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# MediaPlayer- und MediaResource-Klassen{#mediaplayer-and-mediaresource-classes}

Eine MediaResource stellt den Inhalt dar, der demnächst von der MediaPlayer-Instanz geladen wird.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

Die TVSDK-Bibliothek bietet eine einfache Möglichkeit, Inhalte mithilfe der `replaceCurrentResource`-Methode in der `MediaPlayer`-Schnittstelle zu laden und für die Wiedergabe vorzubereiten. Diese Methode empfängt eine Instanz der Klasse `MediaResource` als einziges Eingabeargument. Die `MediaResource`-Klasse besteht aus den folgenden Informationen:

* Eine URL, die den Speicherort des Inhalts darstellt, der demnächst geladen wird.
* Ein Typ, der der Typ des Inhalts ist, der geladen werden soll.

   Dies ist eine Zeichenfolge, die die Inhaltstypen definiert, die mit `MediaPlayer` geladen werden können. Mögliche Werte sind HLS und HDS. Jeder Wert ist mit der Zeichenfolge verknüpft, die die häufig verwendeten Dateierweiterungen darstellt, &quot;m3u8&quot;für HLS und &quot;f4m&quot;für HDS.
* Einige Metadaten, die eine Instanz der Klasse `Metadata` sind.

   Diese wörterbuchähnliche Struktur kann zusätzliche Informationen über den Inhalt enthalten, der geladen werden soll, z. B. Informationen über den alternativen/Anzeigeninhalt, der im Hauptinhalt platziert werden soll.

Die Metadaten sind das Medium, über das Informationen, die sich auf alternative Inhalte beziehen, an TVSDK übergeben werden. Die `Metadata`-Schnittstelle definiert die API für einen generischen Schlüssel-Wert-Store, bei dem sowohl der Schlüssel als auch der Wert einfache Zeichenfolgen sind.
