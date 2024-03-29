---
description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der MediaPlayerItemConfig -Klasse oder stream-basiert mit der MediaPlayerItemConfig -Klasse konfigurieren.
title: Konfigurationsklassenmethoden für Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Konfigurationsklassenmethoden für Tags{#config-class-methods-for-tags}

Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der MediaPlayerItemConfig -Klasse oder stream-basiert mit der MediaPlayerItemConfig -Klasse konfigurieren.

TVSDK wendet die globale Konfiguration automatisch auf alle Medien-Streams an, die keine Stream-spezifische Konfiguration angeben.

Beide `PSDKConfig` und `MediaPlayerItemConfig` diese Methoden zum Verwalten der benutzerdefinierten Tags verfügbar machen:

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="1"><b>Abonnieren bestimmter benutzerdefinierter Tags</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get subscribeTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Ruft die aktuelle Liste der abonnierten Tags ab. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set subscribeTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2">Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden. <p>Ihre Anwendung wird auch automatisch für alle Tags angemeldet, die über <span class="codeph"> adTags</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1"><b>Anpassen der Anzeigen-Tags, die vom standardmäßigen Opportunity-Detektor verwendet werden </b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> öffentliche Funktion get adTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Ruft die aktuelle Liste der Anzeigen-Tags ab. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set adTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunity-Generator verwendet werden. </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie Folgendes:

* Die Setter-Methoden erlauben nicht, dass der Tag-Parameter Nullwerte enthält.

  Wenn festgestellt, gibt TVSDK eine `IllegalArgumentException`.
* Der benutzerdefinierte Tag-Name muss das #-Präfix enthalten.

  Beispiel: `#EXT-X-ASSET` ist ein korrekter benutzerdefinierter Tag-Name, aber `EXT-X-ASSET` ist falsch.
* Sie können die Konfiguration nach dem Laden des Medien-Streams nicht mehr ändern.
