---
description: Diese Klassen bieten Informationen zu Anzeigen, die innerhalb einer Zeitleiste auftreten.
seo-description: Diese Klassen bieten Informationen zu Anzeigen, die innerhalb einer Zeitleiste auftreten.
seo-title: Zeitschienenwerbungskurse
title: Zeitschienenwerbungskurse
uuid: df970e8f-4bf8-4367-9d70-42ebcb11c025
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---


# Zeitschienenwerbungsklassen {#timeline-advertising-classes}

Diese Klassen bieten Informationen zu Anzeigen, die innerhalb einer Zeitleiste auftreten.

<table frame="all" colsep="1" rowsep="1" id="table_1A59E777BA99466793D586286F19E933"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Name</b></th> 
   <th colname="2" class="entry"><b>Beschreibung</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAd.html" format="html" scope="external"> PTAd</a> </td> 
   <td colname="2">Klasse, die die Abstraktion der Anzeige definiert und alle Anzeigeninformationen enthält. Er wird durch eine eindeutige ID, eine Dauer und eine MediaResource definiert. Die MediaResource enthält die URL, unter der sich der eigentliche Anzeigeninhalt befindet. 
    <pre>
      Stellt ein in den Inhalt aufgeteiltes primärer linearer Asset dar. Er kann optional ein Array mit begleitenden Assets enthalten, die zusammen mit dem linearen Asset angezeigt werden müssen.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdAsset.html" format="html" scope="external"> PTAdAsset</a> </td> 
   <td colname="2">Klasse, die ein anzuzeigendes Asset darstellt. 
    <pre>
      Stellt ein anzuzeigendes Asset dar.
    </pre> 
    <pre>
      Klasse, die ein Anzeigenasset darstellt.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBannerView.html" format="html" scope="external"> PTAdBannerView</a> </td> 
   <td colname="2">
    <pre>
      Zeigt ein Banner-Asset an. Ihre Anwendung muss eine neue Instanz dieser Dienstprogrammklasse erstellen, das Banner-Asset festlegen und es einer Ansicht hinzufügen. Die Impressions- und Klickverfolgung für das Banner wird intern von dieser Klasse verwaltet.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBreak.html" format="html" scope="external"> PTAdBreak</a> </td> 
   <td colname="2">Klasse, die eine einheitliche Ansicht für mehrere Anzeigen bietet, die zu einem bestimmten Zeitpunkt während der Wiedergabe wiedergegeben werden. 
    <pre>
      Stellt eine kontinuierliche Folge von Anzeigen dar, die in den Inhalt aufgeteilt werden.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdClick.html" format="html" scope="external"> PTAdClick</a> </td> 
   <td colname="2">Klasse, die eine mit einem Asset verknüpfte Klickinstanz darstellt. Diese Instanz enthält Informationen zur Clickthrough-URL und zum Titel, mit denen dem Benutzer zusätzliche Informationen bereitgestellt werden können. 
    <pre>
      Stellt eine mit einem Asset verknüpfte Klickinstanz dar. Diese Instanz enthält Informationen zur Clickthrough-URL und zum Titel, mit denen dem Benutzer zusätzliche Informationen bereitgestellt werden können.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdPolicyInfo.html" format="html" scope="external"> PTAdPolicyInfo</a> </td> 
   <td colname="2"> Protokoll, das Eigenschaften für AdPolicySelector-API-Aufrufe definiert. Diese Eigenschaften bieten den Kontext zum Erzwingen jedes Anzeigenverhaltens. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTAdPolicySelector.html" format="html" scope="external">PTAdPolicySelector</a></td> 
   <td colname="2"> Ein Admin Policy Selektor-Protokoll zum Erzwingen von Anzeigenverhalten. Anwendungen können diesem Protokoll entsprechen, indem sie alle erforderlichen Methoden implementieren oder die vorhandene Standard-Richtliniensatzklasse erweitern, um bestimmte Verhaltensweisen anzupassen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdTimeline.html" format="html" scope="external">PTAdTimeline</a></td> 
   <td colname="2"> Klasse, die die Zeitschiene der Umbrüche im Inhalt darstellt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 
    <pre>
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTContentResolver.html" format="html" scope="external"> </a> PTContentResolverclass,  
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolver.html" format="html" scope="external"> </a> PTContentResolverprotocol
    </pre> </td> 
   <td colname="2"> Klasse, die den Teil mit der Anzeigenauflösung im Adobe Primetime-Anzeigenentscheidungsprozess verarbeitet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolverDelegate.html" format="html" scope="external"> PTContentResolverDelegate</a> </td> 
   <td colname="2"> Protokoll, das die Methoden beschreibt, die der benutzerdefinierte Inhaltsauflöser ( <span class="codeph"> PTContentResolver</span>) verwenden sollte, um dem Delegaten den Status der Inhaltsauflösung zu kommunizieren. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Constants/PTPlacementType.html" format="html" scope="external"> PTPlacementType</a> </td> 
   <td colname="2">Klasse, die eine Platzierungsinformationen-Anforderung abstrahiert. Jeder aufgelösten Anzeige muss eine Platzierungsinformationen beigefügt sein. Die Platzierungsinformationen beschreiben, wo die Anzeige auf der Zeitschiene platziert werden soll. Er enthält Informationen wie: 
    <ul id="ul_A9105A78F0C24488BCD5E3F2EE62A3EE"> 
     <li id="li_01E968A4330D4B40BA1EB6F4A6000FFD">Platzierungsposition (in ms) </li> 
     <li id="li_A3DC9498BEE14FBA9E7A5D26874F3984">Platzierungstyp (Pre-Roll, Mid-Roll oder Post-Roll) </li> 
     <li id="li_4B9094DD318B4792854A377CC6064232">Dauer des Hauptinhaltsblocks, der ersetzt werden soll </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>