---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
seo-description: Sie können das standardmäßige Anzeigenverhalten verwenden.
seo-title: Verwenden des standardmäßigen Wiedergabeverhaltens
title: Verwenden des standardmäßigen Wiedergabeverhaltens
uuid: 7139384c-167a-4cab-816a-c02fb723a5cb
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Verwenden des standardmäßigen Wiedergabeverhaltens{#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

So verwenden Sie Standardverhalten:

    * Wenn Sie Ihre eigene Klasse &quot;ContentFactory&quot;implementieren, geben Sie eine neue Instanz von &quot;DefaultAdPolicySelector&quot;in Ihrer Implementierung von &quot;doRetrieveAdPolicySelector&quot;zurück.
    
    &quot;Die
    öffentliche Klasse CustomContentFactory erweitert ContentFactory {
    
    //...
    // Ihr benutzerspezifischer Code für Werbeklassen
    //...
    
    /**
    * @inheritDoc
    */
    override protected
    function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector {
    return new DefaultAdPolicySelector(item);
    }
    }
    &quot;
    
    * Wenn Sie keine benutzerdefinierte Implementierung für die Klasse &quot;ContentSDFactory&quot;haben, TVT K verwendet &quot;DefaultAdPolicySelector&quot;.