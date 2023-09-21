---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
title: Verwenden des standardmäßigen Wiedergabe-Verhaltens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# Verwenden des standardmäßigen Wiedergabe-Verhaltens{#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

So verwenden Sie Standardverhalten:

* Wenn Sie Ihre eigene `ContentFactory` -Klasse, geben Sie eine neue Instanz von `DefaultAdPolicySelector` in Ihrer Implementierung von `doRetrieveAdPolicySelector`.

  ```
  public class CustomContentFactory extends ContentFactory { 
  
      //... 
      // your custom code for advertising classes 
      //... 
  
      /** 
       * @inheritDoc 
       */ 
      override protected function  
        doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
          return new DefaultAdPolicySelector(item); 
      } 
  }
  ```

* Wenn Sie keine benutzerdefinierte Implementierung für die `ContentFactory` -Klasse, TVSDK verwendet `DefaultAdPolicySelector`.
