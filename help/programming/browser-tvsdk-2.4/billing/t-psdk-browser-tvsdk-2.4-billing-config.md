---
description: Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Adobe-Kundenbetreuer unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration-Klasse, um diese Parameter vor dem Initialisieren des Medienplayers einzurichten.
seo-description: Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Adobe-Kundenbetreuer unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration-Klasse, um diese Parameter vor dem Initialisieren des Medienplayers einzurichten.
seo-title: Rechnungsmetriken konfigurieren
title: Rechnungsmetriken konfigurieren
uuid: 04d3b53e-f08c-49d0-ba42-5375f1307d2e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Rechnungsmetriken konfigurieren{#configure-billing-metrics}

Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Adobe-Kundenbetreuer unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration-Klasse, um diese Parameter vor dem Initialisieren des Medienplayers einzurichten.

Die meisten Kunden sollten die Standardkonfiguration verwenden.

>[!IMPORTANT]
>
>Die von Ihnen festgelegte Konfiguration bleibt während der gesamten Laufzeit des Medienplayers gültig. Nachdem Sie den Medienplayer initialisiert haben, können Sie die Konfiguration nicht mehr ändern.

So konfigurieren Sie Rechnungsmetriken:

* Geben Sie das folgende Codebeispiel ein.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.billingMetricsConfiguration.isEnabled = true; 
   config.billingMetricsConfiguration.proVODBillableDurationMinutes = 60; 
   config.billingMetricsConfiguration.stdVODBillableDurationMinutes = 30; 
   config.billingMetricsConfiguration.liveBillableDurationMinutes = 15; 
   _player.replaceCurrentResource(_resource, config);
   ```

   wobei `_player` eine Instanz von `AdobePSDK.MediaPlayer` und `_resource` eine Instanz von ist `AdobePSDK.MediaResource`.

