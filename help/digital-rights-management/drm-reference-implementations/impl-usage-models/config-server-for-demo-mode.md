---
title: Demo-Modus des Gebrauchsmodells konfigurieren
description: Demo-Modus des Gebrauchsmodells konfigurieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Demo-Modus des Gebrauchsmodells konfigurieren{#configure-usage-model-demo-mode}

Bevor der Referenz-Implementierungsserver Lizenzen für die Demo zum Verwendungsmodell ausstellen kann, müssen Sie den Server so konfigurieren, dass festgelegt wird, wie Lizenzen für jedes der vier Nutzungsmodelle generiert werden. Dies bedeutet, dass Sie für jedes Nutzungsmodell eine DRM-Richtlinie angeben müssen. Die Referenzimplementierung enthält die folgenden DRM-Beispielrichtlinien im Ordner [!DNL Reference Implementation/Server/Reference Implementation Server/resources/]:

* `dto-policy.pol` - (Download-To-Own)
* `vod-policy.pol` - (Miete/Video-On-Demand)
* `sub-policy.pol` - (Abonnement)
* `ad-policy.pol` - (Ad-finanziert)

>[!NOTE]
>
>Sie können diese Beispielrichtlinien durch Ihre eigenen DRM-Richtlinien ersetzen.

1. Legen Sie diese Eigenschaften in [!DNL flashaccess-refimpl.properties] fest, um die DRM-Richtlinie anzugeben, die Sie für jedes Nutzungsmodell anwenden möchten:

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

1. Kopieren Sie die Beispielrichtliniendateien in den Ordner, den Sie in der `config.resourcesDirectory`-Eigenschaft in [!DNL flashaccess-refimpl.properties] angeben.
