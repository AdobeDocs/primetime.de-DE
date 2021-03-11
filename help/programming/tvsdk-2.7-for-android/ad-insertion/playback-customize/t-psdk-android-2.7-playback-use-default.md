---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
title: Verwenden des standardmäßigen Wiedergabeverhaltens
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Verwenden Sie das standardmäßige Wiedergabeverhalten {#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

1. Führen Sie eine der folgenden Aufgaben aus, um Standardverhalten zu verwenden:

   * Wenn Sie Ihre eigene `AdvertisingFactory`-Klasse implementieren, geben Sie null für `createAdPolicySelector` zurück.

   * Wenn Sie keine benutzerdefinierte Implementierung für die `AdvertisingFactory`-Klasse haben, verwendet TVSDK einen standardmäßigen Anzeigenrichtlinien-Selektor.

## Einrichten der benutzerdefinierten Wiedergabe {#set-up-customized-playback}

Sie können Anzeigenverhalten anpassen oder außer Kraft setzen.

Bevor Sie Anzeigenrichtlinien-Instanzen anpassen oder außer Kraft setzen, registrieren Sie sie bei TVSDK.

* Implementieren Sie die `AdPolicySelector`-Schnittstelle und alle zugehörigen Methoden.

   Diese Option wird empfohlen, wenn Sie **alle**-Standardanzeigeverhalten außer Kraft setzen müssen.

* Erweitern Sie die `DefaultAdPolicySelector`-Klasse und stellen Sie Implementierungen nur für die Verhaltensweisen bereit, die angepasst werden müssen.

   Diese Option wird empfohlen, wenn Sie nur **einige** der Standardverhaltensregeln außer Kraft setzen müssen.

So passen Sie Anzeigenverhalten an:

1. Implementieren Sie die `AdPolicySelector`-Schnittstelle und alle zugehörigen Methoden.
1. Weisen Sie die Richtlinieninstanz zu, die von TVSDK über die Werbefabrik verwendet werden soll.

   >[!NOTE]
   >
   >Benutzerdefinierte Anzeigenrichtlinien, die zu Beginn der Wiedergabe registriert werden, werden gelöscht, wenn die `MediaPlayer`-Instanz dezuordnet wird. Ihre Anwendung muss jedes Mal, wenn eine neue Wiedergabesitzung erstellt wird, eine Richtliniensatzinstanz registrieren.

   Beispiel:

   ```java
   class CustomContentFactory extends ContentFactory { 
       ... 
       @Override 
       public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
           return new CustomAdPolicySelector(mediaPlayerItem); 
       } 
       ... 
   } 
   
   // register the custom content factory with media player 
   MediaPlayerItemConfig config =  new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new CustomContentFactory()); 
   
   // this config will should be later passed while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config);
   ```

1. Implementieren Sie Ihre Anpassungen.