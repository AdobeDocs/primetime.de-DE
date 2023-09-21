---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
title: Verwenden des standardmäßigen Wiedergabe-Verhaltens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Verwenden des standardmäßigen Wiedergabe-Verhaltens  {#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

1. Führen Sie eine der folgenden Aufgaben aus, um Standardverhalten zu verwenden:

   * Wenn Sie Ihre eigene `AdvertisingFactory` class, return null for `createAdPolicySelector`.

   * Wenn Sie keine benutzerdefinierte Implementierung für die `AdvertisingFactory` -Klasse verwendet TVSDK einen standardmäßigen Anzeigenrichtlinienselektor.

## Einrichten der benutzerdefinierten Wiedergabe {#set-up-customized-playback}

Sie können Anzeigenverhalten anpassen oder überschreiben.

Bevor Sie Anzeigenverhalten anpassen oder überschreiben, registrieren Sie die Anzeigenrichtlinieninstanz bei TVSDK.

* Implementieren des `AdPolicySelector` -Schnittstelle und all ihre Methoden.

  Diese Option wird empfohlen, wenn Sie **all** Standardverhalten der Anzeige.

* Erweitern Sie die `DefaultAdPolicySelector` -Klasse und stellen Implementierungen nur für jene Verhaltensweisen bereit, die angepasst werden müssen.

  Diese Option wird empfohlen, wenn Sie nur **some** des Standardverhaltens.

So passen Sie das Anzeigenverhalten an:

1. Implementieren des `AdPolicySelector` -Schnittstelle und all ihrer Methoden.
1. Weisen Sie die Richtlinieninstanz zu, die von TVSDK über die Werbefactory verwendet werden soll.

   >[!NOTE]
   >
   >Benutzerdefinierte Anzeigenrichtlinien, die zu Beginn der Wiedergabe registriert werden, werden gelöscht, wenn die Variable `MediaPlayer` -Instanz nicht zugewiesen wurde. Ihre Anwendung muss bei jeder Erstellung einer neuen Wiedergabesitzung eine Richtlinienselektorinstanz registrieren.

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
