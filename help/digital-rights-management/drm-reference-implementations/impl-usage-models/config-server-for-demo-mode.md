---
title: Demomodus des Nutzungsmodells konfigurieren
description: Demomodus des Nutzungsmodells konfigurieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Demomodus des Nutzungsmodells konfigurieren{#configure-usage-model-demo-mode}

Bevor der Referenz-Implementierungsserver Lizenzen für die Demo des Nutzungsmodells ausgeben kann, müssen Sie den Server so konfigurieren, dass angegeben wird, wie Lizenzen für jedes der vier Nutzungsmodelle generiert werden. Das bedeutet, dass Sie für jedes Nutzungsmodell eine DRM-Richtlinie angeben müssen. Die Referenzimplementierung umfasst die folgenden DRM-Beispielrichtlinien im [!DNL Reference Implementation/Server/Reference Implementation Server/resources/] directory:

* `dto-policy.pol` - (Download-To-Own)
* `vod-policy.pol` - (Vermietung/Video-On-Demand)
* `sub-policy.pol` - (Anmeldung)
* `ad-policy.pol` - (Anzeigenfinanziert)

>[!NOTE]
>
>Sie können diese Beispielrichtlinien durch Ihre eigenen DRM-Richtlinien ersetzen.

1. Legen Sie diese Eigenschaften in fest. [!DNL flashaccess-refimpl.properties] um die DRM-Richtlinie anzugeben, die Sie für jedes Nutzungsmodell anwenden möchten:

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

1. Kopieren Sie die Beispielrichtliniendateien in den Ordner, den Sie im `config.resourcesDirectory` -Eigenschaft in [!DNL flashaccess-refimpl.properties].
