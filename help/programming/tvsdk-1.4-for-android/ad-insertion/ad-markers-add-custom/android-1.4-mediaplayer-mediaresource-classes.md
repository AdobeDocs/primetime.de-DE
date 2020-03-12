---
description: Eine MediaResource stellt den Inhalt dar, der demnächst von der MediaPlayer-Instanz geladen wird.
seo-description: Eine MediaResource stellt den Inhalt dar, der demnächst von der MediaPlayer-Instanz geladen wird.
seo-title: MediaPlayer- und MediaResource-Klassen
title: MediaPlayer- und MediaResource-Klassen
uuid: 7393c320-7dbb-4580-9425-a735f9d03ef5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayer- und MediaResource-Klassen{#mediaplayer-and-mediaresource-classes}

Eine MediaResource stellt den Inhalt dar, der demnächst von der MediaPlayer-Instanz geladen wird.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

Die TVSDK-Bibliothek bietet eine einfache Möglichkeit, Inhalte mithilfe der `replaceCurrentItem` Methode in der MediaPlayer-Schnittstelle zu laden und für die Wiedergabe vorzubereiten. Diese Methode empfängt eine Instanz der MediaResource-Klasse als einziges Eingabeargument. Die MediaResource-Klasse besteht aus den folgenden Informationen:

* Eine URL, die den Speicherort des Inhalts darstellt, der demnächst geladen wird.
* Ein Typ, der der Typ des Inhalts ist, der geladen werden soll.

   Dies ist eine einfache Auflistung in der `MediaResource` Klasse, die die Inhaltstypen definiert, die vom MediaPlayer geladen werden können. Mögliche Werte sind HLS und HDS. Jeder Wert ist mit der Zeichenfolge verknüpft, die die häufig verwendeten Dateierweiterungen `m3u8` für HLS und `f4m` für HDS darstellt.
* Einige Metadaten, die eine Instanz der `Metadata` Klasse sind.

   Diese wörterbuchähnliche Struktur kann zusätzliche Informationen über den Inhalt enthalten, der geladen werden soll, z. B. Informationen über den alternativen/Anzeigeninhalt, der im Hauptinhalt platziert werden soll.

Die Metadaten sind das Medium, über das Informationen, die sich auf alternative Inhalte beziehen, an TVSDK übergeben werden. Die `Metadata` Schnittstelle definiert die API für einen generischen Schlüssel-Wert-Store, bei dem sowohl der Schlüssel als auch der Wert einfache Zeichenfolgen sind.
