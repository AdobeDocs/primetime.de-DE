---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
title: Verwenden des standardmäßigen Wiedergabeverhaltens
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '58'
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