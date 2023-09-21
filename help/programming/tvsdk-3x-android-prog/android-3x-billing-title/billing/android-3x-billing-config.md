---
description: Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Adobe-Aktivierungsbeauftragten verschiedene Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration -Klasse, um diese Parameter einzurichten, bevor Sie den Medienplayer initialisieren.
title: Rechnungsmetriken konfigurieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Rechnungsmetriken konfigurieren {#configure-billing-metrics}

Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Adobe-Aktivierungsbeauftragten verschiedene Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration -Klasse, um diese Parameter einzurichten, bevor Sie den Medienplayer initialisieren.

>[!TIP]
>
>Die meisten Kunden sollten die Standardkonfiguration verwenden.

>[!IMPORTANT]
>
>Die von Ihnen festgelegte Konfiguration bleibt für die Lebensdauer des Medienplayers in Kraft. Nachdem Sie den Medienplayer initialisiert haben, können Sie die Konfiguration nicht mehr ändern.

So konfigurieren Sie Rechnungsmetriken:

Geben Sie das folgende Codebeispiel ein.

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
