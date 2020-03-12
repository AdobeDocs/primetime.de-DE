---
description: Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos direkt auf der Gerätehardware zu verarbeiten.
seo-description: Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos direkt auf der Gerätehardware zu verarbeiten.
seo-title: Mindestanforderungen für StageVideo
title: Mindestanforderungen für StageVideo
uuid: 8916dbac-33e0-4efd-8105-9ddbc85f0a3f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mindestanforderungen für StageVideo{#stagevideo-minimum-requirements}

Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos direkt auf der Gerätehardware zu verarbeiten.

<!--<a id="section_64DDAA8DB215493E8A7CA6636819D350"></a>-->

Eine Kombination verschiedener Faktoren bestimmt, wann und wie Sie es verwenden können `StageVideo`. Die folgende Tabelle enthält eine Momentaufnahme einiger Anforderungen und Einschränkungen, die mit der Verwendung von StageVideo verbunden sind. Diese Anforderungen und Einschränkungen können sich ändern.

<table id="table_882F4462A5AE47E28A60A39D112164A7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Plattform </th> 
   <th colname="col2" class="entry"> Windows und Mac OS </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Flash Player </td> 
   <td colname="col2"> 
    <ul id="ul_s42_lm2_jp"> 
     <li id="li_308FA9EC206B437A9EE04C29F9480B73">Mindestens Flash 10.1 oder höher </li> 
     <li id="li_5898EDB0D12A43389076BCC7F4A27A0A">Für die Ausweichmöglichkeit der Softwarefunktion Flash 15 und höher </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Browser- und <span class="codeph"> wmode</span> -Einstellungen </td> 
   <td colname="col2"> <p><b>Legen Sie in Flash 15</b><span class="codeph"> wmode=opaque</span> fest, damit Sie HTML-Überlagerungen verwenden können. </p> <p>Die folgenden Browser unterstützen derzeit keine Hardwarebeschleunigung: 
     <ul id="ul_frv_ykf_jp"> 
      <li id="li_3D407A61FEE042A9B85A6EFACA6D7719">Mozilla Firefox unter Microsoft Windows </li> 
      <li id="li_39B85AC352564DA8B86EA826638F1F4B">Google Chrome vor 26 und jede Version von Chrome unter Windows XP und Vista </li> 
      <li id="li_0042BA6070C849E6B7C4B4BF4333F712">Microsoft Internet Explorer (alle Versionen) </li> 
     </ul>Andere Browser-/Betriebssystemkombinationen können den Zugriff auf die Hardwarebeschleunigung verhindern. In diesen Szenarien greift <span class="codeph"> StageVideo</span> auf Software zurück, die sich negativ auf die Leistung auswirkt. </p> <p><b>Wenn der Browser die Hardwarebeschleunigung in Flash 14 und früher</b>nicht unterstützt, kann der Flash-Player direkt auf die GPU gerendert werden, aber <span class="codeph"> wmode=direct</span> einstellen, um dieses Rendering zu aktivieren. <p>Tipp:  GPU-Treiber, die älter als 2009 sind, müssen möglicherweise aktualisiert werden, da diese Treiber die Hardwarebeschleunigung möglicherweise nicht unterstützen. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> NetStream-Objekt </td> 
   <td colname="col2">Das <span class="codeph"> StageVideoEvent.RENDER_STATE</span> -Ereignis wird nur ausgelöst, wenn Sie ein <span class="codeph"> NetStream</span> -Objekt an das StageVideo <span class="codeph"> -</span> Objekt anhängen. </td> 
  </tr> 
 </tbody> 
</table>

