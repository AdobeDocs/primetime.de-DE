---
description: Diese Klassen bieten Informationen, mit deren Hilfe Sie feststellen können, wie gut der Player abschneidet.
seo-description: Diese Klassen bieten Informationen, mit deren Hilfe Sie feststellen können, wie gut der Player abschneidet.
seo-title: QoS-Klassen
title: QoS-Klassen
uuid: f145b744-6385-40df-aaee-ae9430d85895
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# QoS-Klassen {#qos-classes}

Diese Klassen bieten Informationen, mit deren Hilfe Sie feststellen können, wie gut der Player abschneidet.

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Name</b></th> 
   <th colname="2" class="entry"><b>Beschreibung</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDeviceInformation.html" format="html" scope="external"> PTDeviceInformation</a> </td> 
   <td colname="2">Bietet Informationen zur Plattform und zum Betriebssystem, auf der das TVSDK ausgeführt wird: 
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
   <td colname="2"> Zeigt Informationen zur Leistung der Wiedergabe an. Dazu gehören die Bildrate, die Bitrate des Profils, die Gesamtdauer der Pufferung, die Anzahl der Pufferung, die Zeit, die zum Abrufen des ersten Bytes aus dem ersten Videofragment erforderlich war, die Zeit zum Rendern des ersten Frames, die aktuell gepufferte Länge und die Pufferzeit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTQoSProvider.html" format="html" scope="external"> PTQoSProvider</a> </td> 
   <td colname="2">
    <pre>
      Bietet wichtige QoS-Metriken für die Wiedergabe und das Gerät.
    </pre>
    <pre>
      Dienstklasse des QOS-Informationsanbieters.
    </pre> </td> 
  </tr> 
 </tbody> 
</table>