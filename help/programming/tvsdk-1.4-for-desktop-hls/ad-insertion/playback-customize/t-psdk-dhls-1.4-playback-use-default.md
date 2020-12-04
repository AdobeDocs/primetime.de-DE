---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
seo-description: Sie können das standardmäßige Anzeigenverhalten verwenden.
seo-title: Verwenden des standardmäßigen Wiedergabeverhaltens
title: Verwenden des standardmäßigen Wiedergabeverhaltens
uuid: 7139384c-167a-4cab-816a-c02fb723a5cb
translation-type: tm+mt
source-git-commit: 1985694f99c548284aad6e6b4e070bece230bdf4
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# Verwenden Sie das standardmäßige Wiedergabeverhalten{#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

So verwenden Sie Standardverhalten:

* Wenn Sie Ihre eigene `ContentFactory`-Klasse implementieren, geben Sie eine neue Instanz von `DefaultAdPolicySelector` in Ihrer Implementierung von `doRetrieveAdPolicySelector` zurück.

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

* Wenn Sie keine benutzerdefinierte Implementierung für die `ContentFactory`-Klasse haben, verwendet TVSDK `DefaultAdPolicySelector`.