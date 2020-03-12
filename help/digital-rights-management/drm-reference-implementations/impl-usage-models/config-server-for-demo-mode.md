---
description: 'null'
seo-description: 'null'
seo-title: Demo-Modus des Gebrauchsmodells konfigurieren
title: Demo-Modus des Gebrauchsmodells konfigurieren
uuid: f818c7fc-e88f-4fa4-926e-08a1337b28d3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Demo-Modus des Gebrauchsmodells konfigurieren{#configure-usage-model-demo-mode}

Bevor der Referenz-Implementierungsserver Lizenzen für die Demo zum Verwendungsmodell ausstellen kann, müssen Sie den Server so konfigurieren, dass festgelegt wird, wie Lizenzen für jedes der vier Nutzungsmodelle generiert werden. Dies bedeutet, dass Sie für jedes Nutzungsmodell eine DRM-Richtlinie angeben müssen. Die Referenzimplementierung enthält die folgenden DRM-Beispielrichtlinien im [!DNL Reference Implementation/Server/Reference Implementation Server/resources/] Ordner:

* `dto-policy.pol` - (Download-To-Own)
* `vod-policy.pol` - (Miete/Video-On-Demand)
* `sub-policy.pol` - (Abonnement)
* `ad-policy.pol` - (Ad-finanziert)

>[!NOTE]
>
>Sie können diese Beispielrichtlinien durch Ihre eigenen DRM-Richtlinien ersetzen.

1. Legen Sie diese Eigenschaften in fest, [!DNL flashaccess-refimpl.properties] um die DRM-Richtlinie anzugeben, die Sie für jedes Nutzungsmodell anwenden möchten:

   ```
   # DRM Policy file name for Download To Own usage 
   RefImpl.UsageModelDemo.Policy.DTO=dto-policy.pol 
   # DRM Policy file name for Rental usage 
   RefImpl.UsageModelDemo.Policy.VOD=vod-policy.pol 
   # DRM Policy file name for Subscription usage 
   RefImpl.UsageModelDemo.Policy.Subscribe=sub-policy.pol 
   # DRM Policy file name for Ad Supported (free) usage 
   RefImpl.UsageModelDemo.Policy.Free=ad-policy.pol
   ```

1. Kopieren Sie die Beispielrichtliniendateien in den Ordner, den Sie in der `config.resourcesDirectory` Eigenschaft angeben [!DNL flashaccess-refimpl.properties].
