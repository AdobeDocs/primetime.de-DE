---
description: Sie können Anzeigenverhalten anpassen oder außer Kraft setzen.
title: Einrichten der benutzerdefinierten Wiedergabe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# Einrichten der benutzerdefinierten Wiedergabe{#set-up-customized-playback}

Sie können Anzeigenverhalten anpassen oder außer Kraft setzen.

Bevor Sie Anzeigenrichtlinien anpassen oder außer Kraft setzen können, registrieren Sie die Anzeigenrichtlinieninstanz mit .
Führen Sie zum Anpassen des Anzeigenverhaltens einen der folgenden Schritte aus:

* Implementieren Sie die `AdPolicySelector`-Schnittstelle und alle zugehörigen Methoden.

   Diese Option wird empfohlen, wenn Sie **alle**-Standardanzeigeverhalten außer Kraft setzen müssen.

* Erweitern Sie die `DefaultAdPolicySelector`-Klasse und stellen Sie Implementierungen nur für die Verhaltensweisen bereit, die angepasst werden müssen.

   Diese Option wird empfohlen, wenn Sie nur **einige** der Standardverhaltensregeln außer Kraft setzen müssen.

Führen Sie für beide Optionen die folgenden Aufgaben aus:

1. Implementieren Sie Ihre eigene benutzerdefinierte Anzeigenrichtlinien-Auswahl.

   ```
   public class CustomAdPolicySelector implements AdPolicySelector { 
       // your own customization here 
   }
   ```

1. Erweitern Sie die Inhaltsfactory, um die benutzerdefinierte Anzeigenrichtlinien-Auswahl zu verwenden.

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
       /** 
        * @inheritDoc 
        */ 
       override protected function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
           return new CustomAdPolicySelector(item); 
       } 
   }
   ```

   ```
   psdkutils::PSDKSharedPointer<psdk::ContentFactory> factory; 
   psdkFactory->createDefaultContentFactory(&factory); 
   psdkutils::PSDKSharedPointer<psdk::AdPolicySelector> defaultAdPolicySelector; 
   factory->retrieveAdPolicySelector(item, &defaultAdPolicySelector);
   ```

1. Registrieren Sie die neue Inhaltsfabrik, die von TVSDK im Werbe-Workflow verwendet werden soll.

   ```
   PSDKConfig.advertisingFactory = new CustomContentFactory();
   ```

   >[!TIP]
   >
   >Wenn die Factory für benutzerdefinierten Inhalt für einen bestimmten Stream über die Klasse `MediaPlayerItemConfig` registriert wurde, wird sie gelöscht, wenn die `MediaPlayer`-Instanz dezuordnet wird. Ihre Anwendung muss sie jedes Mal registrieren, wenn eine neue Wiedergabesitzung erstellt wird.