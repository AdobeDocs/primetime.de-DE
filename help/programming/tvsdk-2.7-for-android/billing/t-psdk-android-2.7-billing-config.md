---
description: Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Kundenbetreuer für die Aktivierung der Adobe unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration-Klasse, um diese Parameter vor dem Initialisieren des Medienplayers festzulegen.
seo-description: Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Kundenbetreuer für die Aktivierung der Adobe unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration-Klasse, um diese Parameter vor dem Initialisieren des Medienplayers festzulegen.
seo-title: Rechnungsmetriken konfigurieren
title: Rechnungsmetriken konfigurieren
uuid: d8656ab2-fdd8-4fe4-8578-a6c8ecd378e2
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# Rechnungsmetriken {#configure-billing-metrics} konfigurieren

Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Kundenbetreuer für die Aktivierung der Adobe unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration-Klasse, um diese Parameter vor dem Initialisieren des Medienplayers festzulegen.

>[!TIP]
>
>Die meisten Kunden sollten die Standardkonfiguration verwenden.

>[!IMPORTANT]
>
>Die von Ihnen festgelegte Konfiguration bleibt während der gesamten Laufzeit des Medienplayers gültig. Nachdem Sie den Medienplayer initialisiert haben, können Sie die Konfiguration nicht mehr ändern.

So konfigurieren Sie Rechnungsmetriken:

1. Geben Sie das folgende Codebeispiel ein.

   ```java
   MediaPlayerItemConfig config = new MediaPlayerItemConfig(); 
   BillingMetricsConfiguration billingConfig = new BillingMetricsConfiguration(); 
   billingConfig.setEnabled(true); 
   billingConfig.setProVODBillableDurationMinutes(60); 
   billingConfig.setStdVODBillableDurationMinutes(30); 
   billingConfig.setLiveBillableDurationMinutes(15); 
   config.setBillingMetricsConfiguration(billingConfig); 
   mediaPlayer.replaceCurrentResource(mediaResource, config);
   ```

