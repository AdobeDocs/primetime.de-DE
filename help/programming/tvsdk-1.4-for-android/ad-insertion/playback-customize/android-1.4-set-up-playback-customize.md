---
description: Sie können Anzeigenverhalten anpassen oder außer Kraft setzen.
seo-description: Sie können Anzeigenverhalten anpassen oder außer Kraft setzen.
seo-title: Einrichten der benutzerdefinierten Wiedergabe
title: Einrichten der benutzerdefinierten Wiedergabe
uuid: 9cbf0bcf-7932-409e-a690-e79f284eaf74
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---


# Einrichten der benutzerdefinierten Wiedergabe {#cset-up-customized-playback}

Sie können das Anzeigenverhalten anpassen oder überschreiben, indem Sie die Anzeigenrichtlinieninstanz mit TVSDK registrieren.

Führen Sie zum Anpassen des Anzeigenverhaltens einen der folgenden Schritte aus:

* Implementieren Sie die `AdPolicySelector`-Schnittstelle und alle zugehörigen Methoden.
Diese Option wird empfohlen, wenn Sie alle standardmäßigen Anzeigenverhalten außer Kraft setzen müssen.

* Erweitern Sie die `DefaultAdPolicySelector`-Klasse und stellen Sie Implementierungen nur für die Verhaltensweisen bereit, die
Anpassung.
Diese Option wird empfohlen, wenn Sie nur einige der Standardverhalten außer Kraft setzen müssen.

Führen Sie für beide Optionen die folgenden Aufgaben aus:

So passen Sie Anzeigenverhalten an:

1. Implementieren Sie die AdPolicySelector-Schnittstelle und alle zugehörigen Methoden.

1. Weisen Sie die Richtlinieninstanz zu, die von TVSDK über die Werbefabrik verwendet werden soll.

>[!IMPORTANT]
>
>Benutzerdefinierte Anzeigenrichtlinien, die am Anfang von >Wiedergabe registriert werden, werden geleert, wenn die MediaPlayer-Instanz >nicht zugeordnet ist. Ihre Anwendung muss jedes Mal, wenn eine neue Wiedergabesitzung erstellt wird, eine Richtlinie > Selektorinstanz registrieren.

Beispiel:

```
    class CustomContentFactory extends ContentFactory {
     ...
    @Override
    public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem mediaPlayerItem) {
    return new CustomAdPolicySelector(mediaPlayerItem);
    }
     ...
    }
    TVSDK 1.4 for Android Programmer's Guide 46
    // register the custom content factory with media player
    MediaPlayerItemConfig config = new MediaPlayerItemConfig();
    config.setAdvertisingFactory(new CustomContentFactory());
    // this config will should be later passed while loading the resource
    mediaPlayer.replaceCurrentResource(resource, config);
```

1. Implementieren Sie Ihre Anpassungen.