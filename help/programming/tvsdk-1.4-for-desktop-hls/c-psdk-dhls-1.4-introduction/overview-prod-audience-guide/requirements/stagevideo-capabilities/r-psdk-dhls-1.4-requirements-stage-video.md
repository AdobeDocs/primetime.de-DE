---
description: Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos direkt auf der Gerätehardware zu verarbeiten.
title: Mindestanforderungen für StageVideo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Mindestanforderungen für StageVideo{#stagevideo-minimum-requirements}

Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos direkt auf der Gerätehardware zu verarbeiten.

<!--<a id="section_64DDAA8DB215493E8A7CA6636819D350"></a>-->

Eine Kombination verschiedener Faktoren bestimmt, wann und wie Sie `StageVideo` verwenden können. Die folgende Tabelle enthält eine Momentaufnahme einiger Anforderungen und Einschränkungen, die mit der Verwendung von StageVideo verbunden sind. Diese Anforderungen und Einschränkungen können sich ändern.

<table id="table_882F4462A5AE47E28A60A39D112164A7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Plattform </th> 
   <th colname="col2" class="entry"> Windows und Mac OS </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Flash-Player </td> 
   <td colname="col2"> 
    <ul id="ul_s42_lm2_jp"> 
     <li id="li_308FA9EC206B437A9EE04C29F9480B73">Mindestens Flash 10.1 oder höher </li> 
     <li id="li_5898EDB0D12A43389076BCC7F4A27A0A">Für den Fallback zur Softwarefunktion, Flash 15 und höher </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Browser- und <span class="codeph"> wmode</span>-Einstellungen </td> 
   <td colname="col2"> <p><b>Stellen Sie in Flash 15</b>  <span class="codeph"> wmode=</span> opaqueso HTML-Überlagerungen ein. </p> <p>Die folgenden Browser unterstützen derzeit keine Hardwarebeschleunigung: 
     <ul id="ul_frv_ykf_jp"> 
      <li id="li_3D407A61FEE042A9B85A6EFACA6D7719">Mozilla Firefox unter Microsoft Windows </li> 
      <li id="li_39B85AC352564DA8B86EA826638F1F4B">Google Chrome vor 26 und jede Version von Chrome unter Windows XP und Vista </li> 
      <li id="li_0042BA6070C849E6B7C4B4BF4333F712">Microsoft Internet Explorer (alle Versionen) </li> 
     </ul>Andere Browser-/Betriebssystemkombinationen können den Zugriff auf die Hardwarebeschleunigung verhindern. In diesen Szenarien greift <span class="codeph"> StageVideo</span> auf Software zurück, was sich negativ auf die Leistung auswirkt. </p> <p><b>Wenn der Browser die Hardwarebeschleunigung nicht unterstützt, kann der Flash-Player auf Flash 14 und früher</b> direkt an die GPU gerendert werden. Sie können jedoch  <span class="codeph"> wmode=</span> directe festlegen, um dieses Rendering zu aktivieren. <p>Tipp:  GPU-Treiber, die älter als 2009 sind, müssen möglicherweise aktualisiert werden, da diese Treiber die Hardwarebeschleunigung möglicherweise nicht unterstützen. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> NetStream-Objekt </td> 
   <td colname="col2">Das Ereignis <span class="codeph"> StageVideoEvent.RENDER_STATE</span> wird nur ausgelöst, wenn Sie ein <span class="codeph"> NetStream</span>-Objekt an das <span class="codeph">-Objekt StageVideo</span> anhängen. </td> 
  </tr> 
 </tbody> 
</table>

