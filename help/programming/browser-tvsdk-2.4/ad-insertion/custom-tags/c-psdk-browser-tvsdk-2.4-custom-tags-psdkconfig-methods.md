---
description: Sie können benutzerdefinierte Tag-Namen in einem Stream mit der MediaPlayerItemConfig -Klasse konfigurieren.
title: Konfigurationsklassenmethoden für Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Konfigurationsklassenmethoden für Tags{#config-class-methods-for-tags}

Sie können benutzerdefinierte Tag-Namen in einem Stream mit der MediaPlayerItemConfig -Klasse konfigurieren.

So erstellen Sie eine neue `MediaPlayerItemConfig`:

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

Im Folgenden finden Sie einige Informationen darüber, wie die `MediaPlayerItemConfig` -Methoden werden verwendet, um benutzerdefinierte Tags zu verwalten:

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
   <td colname="col2"> <p>Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden. </p> <p>Ihre Anwendung wird auch automatisch für alle Tags angemeldet, die über übertragen werden <span class="codeph"> adTags </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Anpassen der Anzeigen-Tags, die vom standardmäßigen Opportunity-Detektor verwendet werden </b> </td> 
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
   <td colname="col2"> <p>Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunity-Generator verwendet werden sollen. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie Folgendes:

* Der benutzerdefinierte Tag-Name muss die Variable `#` -Präfix.

  Beispiel: `#EXT-X-ASSET` ist ein korrekter benutzerdefinierter Tag-Name, aber `EXT-X-ASSET` ist falsch.

* Sie können die Konfiguration nach dem Laden des Medien-Streams nicht mehr ändern.
