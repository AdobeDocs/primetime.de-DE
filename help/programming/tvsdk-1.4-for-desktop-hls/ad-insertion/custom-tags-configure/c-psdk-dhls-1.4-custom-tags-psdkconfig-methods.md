---
description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der MediaPlayerItemConfig-Klasse oder stream-basiert mit der MediaPlayerItemConfig-Klasse konfigurieren.
seo-description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der MediaPlayerItemConfig-Klasse oder stream-basiert mit der MediaPlayerItemConfig-Klasse konfigurieren.
seo-title: Methoden der Config-Klasse für Tags
title: Methoden der Config-Klasse für Tags
uuid: 3317fc8b-c13c-4e7d-8334-aa8cdf40fa05
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# Methoden der Config-Klasse für Tags{#config-class-methods-for-tags}

Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der MediaPlayerItemConfig-Klasse oder stream-basiert mit der MediaPlayerItemConfig-Klasse konfigurieren.

TVSDK wendet die globale Konfiguration automatisch auf jeden Medienstream an, der keine Stream-spezifische Konfiguration angibt.

Sowohl `PSDKConfig` als auch `MediaPlayerItemConfig` stellen diese Methoden zur Verwaltung der benutzerdefinierten Tags bereit:

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="1"><b>Abonnieren bestimmter benutzerdefinierter Tags</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get subscribeTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2"> Ruft die aktuelle Liste der abonnierten Tags ab. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set subscribeTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2">Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden. <p>Ihre Anwendung wird auch automatisch für alle Tags abonniert, die über <span class="codeph"> adTags</span> übertragen werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1"><b>Anpassen der vom Standard-Opportunitätsdetektor verwendeten Anzeigen-Tags  </b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get adTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2"> Ruft die aktuelle Liste der Anzeigen-Tags ab. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set adTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2"> Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunitätsgenerator verwendet werden. </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie Folgendes:

* Die set-Methoden lassen nicht zu, dass der Parameter tags Null-Werte enthält.

   Wenn TVSDK gefunden, wird ein `IllegalArgumentException` ausgegeben.
* Der benutzerdefinierte Tag-Name muss das #-Präfix enthalten.

   `#EXT-X-ASSET` ist beispielsweise ein korrekter benutzerdefinierter Tag-Name, `EXT-X-ASSET` ist jedoch nicht korrekt.
* Sie können die Konfiguration nach dem Laden des Medienstreams nicht mehr ändern.

