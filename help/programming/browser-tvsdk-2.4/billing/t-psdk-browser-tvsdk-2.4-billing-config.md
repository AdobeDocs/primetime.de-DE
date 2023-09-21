---
description: Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Adobe-Aktivierungsbeauftragten verschiedene Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration -Klasse, um diese Parameter einzurichten, bevor Sie den Medienplayer initialisieren.
title: Rechnungsmetriken konfigurieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Rechnungsmetriken konfigurieren{#configure-billing-metrics}

Wenn Sie die Standardkonfiguration verwenden, müssen Sie nichts anderes tun, um die Rechnungsstellung zu aktivieren oder zu konfigurieren. Wenn Sie von Ihrem Adobe-Aktivierungsbeauftragten verschiedene Konfigurationsparameter erhalten haben, verwenden Sie die BillingMetricsConfiguration -Klasse, um diese Parameter einzurichten, bevor Sie den Medienplayer initialisieren.

Die meisten Kunden sollten die Standardkonfiguration verwenden.

>[!IMPORTANT]
>
>Die von Ihnen festgelegte Konfiguration bleibt für die Lebensdauer des Medienplayers in Kraft. Nachdem Sie den Medienplayer initialisiert haben, können Sie die Konfiguration nicht mehr ändern.

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

  where `_player` ist eine Instanz von `AdobePSDK.MediaPlayer` und `_resource` ist eine Instanz von `AdobePSDK.MediaResource`.
