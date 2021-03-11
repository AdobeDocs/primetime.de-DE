---
description: Mit der MediaPlayerItemConfig-Klasse können Sie benutzerdefinierte Tag-Namen in einem Stream konfigurieren.
title: Methoden der Config-Klasse für Tags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Methoden der Config-Klasse für Tags{#config-class-methods-for-tags}

Mit der MediaPlayerItemConfig-Klasse können Sie benutzerdefinierte Tag-Namen in einem Stream konfigurieren.

So erstellen Sie ein neues `MediaPlayerItemConfig`:

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

Im Folgenden finden Sie einige Informationen darüber, wie die `MediaPlayerItemConfig`-Methoden zum Verwalten benutzerdefinierter Tags verwendet werden:

<table id="table_0AC0973497144DDAB05726E3F031ACD1"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>Abonnieren bestimmter benutzerdefinierter Tags</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;subscribeTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>Ruft die aktuelle Liste der abonnierten Tags ab. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;subscribeTags&nbsp;=&nbsp;["#EXT-X-PROGRAM-DATE-TIME"];mediaPlayerItemConfig.subscribeTags&nbsp;=&nbsp;subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden. </p> <p>Ihre Anwendung wird auch automatisch für alle Tags abonniert, die über <span class="codeph"> adTags </span> übertragen werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Anpassen der vom Standard-Opportunitätsdetektor verwendeten Anzeigen-Tags  </b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;adTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.adTags; 
    </code> </td> 
   <td colname="col2"> <p>Ruft die aktuelle Liste der Anzeigen-Tags ab. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;adTags&nbsp;=&nbsp;["#EXT-X-CUE"];mediaPlayerItemConfig.adTags&nbsp;=&nbsp;adTags;
    </code> </td> 
   <td colname="col2"> <p>Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunitätsgenerator verwendet werden. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie Folgendes:

* Der benutzerdefinierte Tag-Name muss das Präfix `#` enthalten.

   `#EXT-X-ASSET` ist beispielsweise ein korrekter benutzerdefinierter Tag-Name, `EXT-X-ASSET` ist jedoch nicht korrekt.

* Sie können die Konfiguration nach dem Laden des Medienstreams nicht mehr ändern.

