---
description: Mit der MediaPlayerItemConfig-Klasse können Sie benutzerdefinierte Tag-Namen in TVSDK global konfigurieren.
seo-description: Mit der MediaPlayerItemConfig-Klasse können Sie benutzerdefinierte Tag-Namen in TVSDK global konfigurieren.
seo-title: Methoden der Config-Klasse für Tags
title: Methoden der Config-Klasse für Tags
uuid: f2758085-8e49-4eaf-82bb-4a2e4dd8accb
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Methoden der Config-Klasse für Tags{#config-class-methods-for-tags}

Mit der MediaPlayerItemConfig-Klasse können Sie benutzerdefinierte Tag-Namen in TVSDK global konfigurieren.

TVSDK wendet die globale Konfiguration automatisch auf jeden Medienstream an, der keine Stream-spezifische Konfiguration angibt.

`MediaPlayerItemConfig` stellt die folgenden Methoden zur Verwaltung der benutzerdefinierten Tags bereit:

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>Abonnieren bestimmter benutzerdefinierter Tags</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getSubscribedTags() </span> </td> 
   <td colname="col2"> Ruft die aktuelle Liste der abonnierten Tags ab. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setSubscribedTags(String[] tags); </span> </td> 
   <td colname="col2"> Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden. <p>Ihre Anwendung wird auch automatisch für alle Tags abonniert, die über <span class="codeph"> setAdTags übertragen werden </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Anpassen der vom Standard-Opportunitätsdetektor verwendeten Anzeigen-Tags</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getAdTags(); </span> </td> 
   <td colname="col2"> Ruft die aktuelle Liste der Anzeigen-Tags ab. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setAdTags(String[] tags); </span> </td> 
   <td colname="col2"> Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunitätsgenerator verwendet werden. </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie Folgendes:

* Die set-Methoden lassen nicht zu, dass der Parameter tags Null-Werte enthält.

   Wenn ein TVSDK gefunden wird, wird ein `IllegalArgumentException`geworfen.
* Der benutzerdefinierte Tag-Name muss das #-Präfix enthalten.

   Beispielsweise `#EXT-X-ASSET` ist ein korrekter benutzerdefinierter Tag-Name, aber `EXT-X-ASSET` falsch.
* Sie können die Konfiguration nach dem Laden des Medienstreams nicht mehr ändern.

