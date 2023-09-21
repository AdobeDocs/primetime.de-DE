---
description: Diese Klassen bieten Informationen, die Ihnen dabei helfen festzustellen, wie gut der Player abschneidet.
title: QoS-Klassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# QoS-Klassen {#qos-classes}

Diese Klassen bieten Informationen, die Ihnen dabei helfen festzustellen, wie gut der Player abschneidet.

Package: [com.adobe.mediacore.qos](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/package-summary.html)  Package: [com.adobe.mediacore.qos.metrics](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/package-summary.html)

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Name </th> 
   <th colname="2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">Metriken.<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/BufferingMetrics.html" format="html" scope="external"> BufferingMetrics</a></span></td> 
   <td colname="2"> Enthält Informationen darüber, wie viel Zeit der Player während der Pufferung verbracht hat und wie oft ein Pufferereignis aufgetreten ist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/DeviceInformation.html" format="html" scope="external"> DeviceInformation</a> </span></td> 
   <td colname="2">Bietet Informationen über die Plattform und das Betriebssystem, auf der die Wortgruppe ausgeführt wird: 
    <ul id="ul_0DE69F3B38E84964AB98DCCD11E5E123"> 
     <li id="li_19B2D1889FCA4B0F8FCB0EE8F87353B2">Version des Plattform-Betriebssystems </li> 
     <li id="li_CA35F4A48FD34555AC7D7832D5997AD4">Versionsnummer der Phrase-Bibliothek </li> 
     <li id="li_30D38320C2A3440E92C0A477FFFBF9A0">Modellname des Geräts </li> 
     <li id="li_2D15164B987E405685B96A900EBF041D">Name des Geräteherstellers </li> 
     <li id="li_B78485CB9580444DB9694404706BA191">Geräte-UID </li> 
     <li id="li_841EA77499B44F0692192F9DE1A798E4">Breite/Höhe des Gerätebildschirms </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/LoadInfo.html" format="html" scope="external"> LoadInfo</a></span> </td> 
   <td colname="2"> Enthält verschiedene QoS-Informationen zum Laden verschiedener Ressourcen (Dateien, Manifest oder Wiedergabeliste, Fragmente/Segmente, Tracks usw.). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/PlaybackInformation.html" format="html" scope="external"> PlaybackInformation</a></span> </td> 
   <td colname="2"> Enthält Informationen zur Leistung der Wiedergabe. Dazu gehören die Framerate, die Profil-Bit-Rate, die Gesamtdauer, die mit der Pufferung verbracht wurde, die Anzahl der Pufferversuche, die Zeit, die zum Abrufen des ersten Byte vom ersten Videofragment erforderlich war, die Zeit, die zum Rendern des ersten Frames benötigt wurde, die derzeit gepufferte Länge und die Pufferzeit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">Metriken.<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackLoadMetrics.html" format="html" scope="external"> PlaybackLoadMetrics</a></span> </td> 
   <td colname="2"> Bietet Informationen dazu, wie lange es gedauert hat, bis das Medium geladen wurde, wie lange es gedauert hat, bis der Player den ersten Frame gerendert hat oder im Fall eines Fehlers fehlschlug. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">Metriken.<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackLoadMetrics.html" format="html" scope="external"> PlaybackMetrics</a> </span></td> 
   <td colname="2"> Enthält Informationen zum Verhalten der Wiedergabe. Dies umfasst die Framerate, Bitrate, Pufferlänge usw. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">Metriken.<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackSessionMetrics.html" format="html" scope="external"> PlaybackSessionMetrics</a></span> </td> 
   <td colname="2"> Enthält Informationen darüber, wie viele Sekunden der Player während der tatsächlichen Wiedergabe verbracht hat und wie lange das Video tatsächlich auf dem Bildschirm war. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/QOSProvider.html" format="html" scope="external"> QOSProvider</a></span></td> 
   <td colname="2">Bietet wichtige QoS-Metriken für die Wiedergabe und das Gerät. Anbieterklasse für QOS-Informationen.</td> 
  </tr> 
 </tbody> 
</table>
