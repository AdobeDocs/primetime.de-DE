---
description: Sie können Anzeigenverhalten anpassen oder überschreiben.
title: Einrichten der benutzerdefinierten Wiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Benutzerdefinierte Wiedergabe einrichten {#cset-up-customized-playback}

Sie können das Anzeigenverhalten anpassen oder überschreiben, indem Sie die Anzeigenrichtlinieninstanz mit TVSDK registrieren.

Führen Sie einen der folgenden Schritte aus, um das Anzeigenverhalten anzupassen:

* Implementieren des `AdPolicySelector` -Schnittstelle und all ihre Methoden.
Diese Option wird empfohlen, wenn Sie alle standardmäßigen Anzeigenverhaltensweisen außer Kraft setzen müssen.

* Erweitern Sie die `DefaultAdPolicySelector` -Klasse und stellen Implementierungen nur für jene Verhaltensweisen bereit, die angepasst werden müssen.
Diese Option wird empfohlen, wenn Sie nur einige der Standardverhaltensweisen überschreiben müssen.

Führen Sie für beide Optionen die folgenden Aufgaben aus:

So passen Sie das Anzeigenverhalten an:

1. Implementieren Sie die AdPolicySelector-Schnittstelle und alle zugehörigen Methoden.

1. Weisen Sie die Richtlinieninstanz zu, die von TVSDK über die Werbefactory verwendet werden soll.

>[!IMPORTANT]
>
>Benutzerdefinierte Anzeigenrichtlinien, die zu Beginn von &quot;Wiedergabe&quot;registriert werden, werden gelöscht, wenn die MediaPlayer-Instanz >nicht zugeordnet ist. Ihre Anwendung muss bei jeder Erstellung einer neuen Wiedergabesitzung eine Richtlinie >Selektorinstanz registrieren.

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
