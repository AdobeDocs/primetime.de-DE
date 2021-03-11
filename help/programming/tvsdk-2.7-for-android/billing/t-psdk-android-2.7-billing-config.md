---
description: Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts weiter tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Kundenbetreuer für die Aktivierung der Adobe unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration-Klasse, um diese Parameter vor dem Initialisieren des Medienplayers festzulegen.
title: Rechnungsmetriken konfigurieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Rechnungsmetriken {#configure-billing-metrics} konfigurieren

Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts weiter tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Kundenbetreuer für die Aktivierung der Adobe unterschiedliche Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration-Klasse, um diese Parameter vor dem Initialisieren des Medienplayers festzulegen.

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

