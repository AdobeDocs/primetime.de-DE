---
description: Diese Klassen bieten Informationen, die Ihnen dabei helfen festzustellen, wie gut der Player abschneidet.
title: QoS-Klassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# QoS-Klassen{#qos-classes}

Diese Klassen bieten Informationen, die Ihnen dabei helfen festzustellen, wie gut der Player abschneidet.

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Name </th> 
   <th colname="2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDeviceInformation.html" format="html" scope="external"> PTDeviceInformation</a> </td> 
   <td colname="2">Enthält Informationen über die Plattform und das Betriebssystem, auf der das TVSDK ausgeführt wird: 
    <ul id="ul_0DE69F3B38E84964AB98DCCD11E5E123"> 
     <li id="li_19B2D1889FCA4B0F8FCB0EE8F87353B2">Version des Plattform-Betriebssystems </li> 
     <li id="li_CA35F4A48FD34555AC7D7832D5997AD4">Versionsnummer der TVSDK-Bibliothek </li> 
     <li id="li_30D38320C2A3440E92C0A477FFFBF9A0">Modellname des Geräts </li> 
     <li id="li_2D15164B987E405685B96A900EBF041D">Name des Geräteherstellers </li> 
     <li id="li_B78485CB9580444DB9694404706BA191">Geräte-UID </li> 
     <li id="li_841EA77499B44F0692192F9DE1A798E4">Breite/Höhe des Gerätebildschirms </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTPlaybackInformation.html" format="html" scope="external"> PTPlaybackInformation</a> </td> 
   <td colname="2"> Enthält Informationen zur Leistung der Wiedergabe. Dazu gehören die Framerate, die Profil-Bit-Rate, die Gesamtdauer, die mit der Pufferung verbracht wurde, die Anzahl der Pufferversuche, die Zeit, die zum Abrufen des ersten Byte vom ersten Videofragment erforderlich war, die Zeit, die zum Rendern des ersten Frames benötigt wurde, die derzeit gepufferte Länge und die Pufferzeit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTQoSProvider.html" format="html" scope="external"> PTQoSProvider</a> </td> 
   <td colname="2">
    <pre>
      Bietet wichtige QoS-Metriken für die Wiedergabe und das Gerät.
    </pre>
    <pre>
      Anbieterklasse für QOS-Informationen.
    </pre> </td> 
  </tr> 
 </tbody> 
</table>
