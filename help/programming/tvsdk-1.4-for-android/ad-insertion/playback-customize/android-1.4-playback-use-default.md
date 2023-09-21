---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
title: Verwenden des standardmäßigen Wiedergabe-Verhaltens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# Verwenden des standardmäßigen Wiedergabe-Verhaltens {#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

So verwenden Sie Standardverhalten:

    * Wenn Sie Ihre eigene Klasse &quot;AdvertisingFactory&quot;implementieren, geben Sie null für &quot;createAdPolicySelector&quot;zurück.
    
    * Wenn Sie keine benutzerdefinierte Implementierung für die Klasse &quot;AdvertisingFactory&quot;haben, verwendet TVSDK einen standardmäßigen Anzeigenrichtlinienselektor .
