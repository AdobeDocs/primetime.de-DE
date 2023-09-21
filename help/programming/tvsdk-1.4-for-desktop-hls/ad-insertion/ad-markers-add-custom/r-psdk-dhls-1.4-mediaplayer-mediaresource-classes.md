---
description: Eine MediaResource stellt den Inhalt dar, der in Kürze von der MediaPlayer-Instanz geladen wird.
title: MediaPlayer- und MediaResource-Klassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# MediaPlayer- und MediaResource-Klassen{#mediaplayer-and-mediaresource-classes}

Eine MediaResource stellt den Inhalt dar, der in Kürze von der MediaPlayer-Instanz geladen wird.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

Die TVSDK-Bibliothek bietet eine einfache Möglichkeit, Inhalte mithilfe der `replaceCurrentResource` -Methode in `MediaPlayer` -Schnittstelle. Diese Methode erhält eine Instanz der `MediaResource` -Klasse als einziges Eingabeargument. Die `MediaResource` -Klasse setzt sich aus den folgenden Informationen zusammen:

* Eine URL, die den Speicherort des Inhalts darstellt, der geladen werden soll.
* Ein Typ, der den Inhaltstyp ist, der geladen werden soll.

  Dies ist eine Zeichenfolge, die die Inhaltstypen definiert, die von der `MediaPlayer`. Mögliche Werte sind HLS und HDS. Jeder Wert ist mit der Zeichenfolge verknüpft, die die häufig verwendeten Dateierweiterungen darstellt: &quot;m3u8&quot;für HLS und &quot;f4m&quot;für HDS.
* Einige Metadaten, die eine Instanz der `Metadata` -Klasse.

  Diese wörterbuchähnliche Struktur kann zusätzliche Informationen über den Inhalt enthalten, der geladen werden soll, z. B. Informationen über den alternativen/Anzeigeninhalt, der im Hauptinhalt platziert werden soll.

Die Metadaten sind das Medium, über das Informationen, die sich auf alternative Inhalte beziehen, an TVSDK weitergegeben werden. Die `Metadata` -Schnittstelle definiert die API für einen generischen Schlüssel-Wert-Store, bei dem sowohl der Schlüssel als auch der Wert einfache Zeichenfolgen sind.
