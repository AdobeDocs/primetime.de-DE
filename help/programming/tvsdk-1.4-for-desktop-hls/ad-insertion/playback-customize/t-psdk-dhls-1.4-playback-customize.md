---
description: Sie können Anzeigenverhalten anpassen oder überschreiben.
title: Einrichten der benutzerdefinierten Wiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Einrichten der benutzerdefinierten Wiedergabe{#set-up-customized-playback}

Sie können Anzeigenverhalten anpassen oder überschreiben.

Bevor Sie Anzeigenverhalten anpassen oder überschreiben können, registrieren Sie die Anzeigenrichtlinieninstanz bei .
Führen Sie einen der folgenden Schritte aus, um das Anzeigenverhalten anzupassen:

* Implementieren des `AdPolicySelector` -Schnittstelle und all ihre Methoden.

  Diese Option wird empfohlen, wenn Sie **all** Standardverhalten der Anzeige.

* Erweitern Sie die `DefaultAdPolicySelector` -Klasse und stellen Implementierungen nur für jene Verhaltensweisen bereit, die angepasst werden müssen.

  Diese Option wird empfohlen, wenn Sie nur **some** des Standardverhaltens.

Führen Sie für beide Optionen die folgenden Aufgaben aus:

1. Implementieren Sie Ihre eigene benutzerdefinierte Anzeigenrichtlinienauswahl.

   ```
   public class CustomAdPolicySelector implements AdPolicySelector { 
       // your own customization here 
   }
   ```

1. Erweitern Sie die Inhaltsfactory, um die Auswahl der benutzerdefinierten Anzeigenrichtlinien zu verwenden.

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

1. Registrieren Sie die neue Inhaltsfactory, die von TVSDK im Werbe-Workflow verwendet werden soll.

   ```
   PSDKConfig.advertisingFactory = new CustomContentFactory();
   ```

   >[!TIP]
   >
   >Wenn die benutzerdefinierte Inhaltsfactory für einen bestimmten Stream über die `MediaPlayerItemConfig` -Klasse, wird sie beim `MediaPlayer` -Instanz nicht zugewiesen wurde. Ihre Anwendung muss sie jedes Mal registrieren, wenn eine neue Wiedergabesitzung erstellt wird.
