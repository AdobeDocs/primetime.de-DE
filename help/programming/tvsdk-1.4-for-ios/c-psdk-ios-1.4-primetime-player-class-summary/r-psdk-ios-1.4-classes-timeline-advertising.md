---
description: Diese Klassen liefern Informationen über Anzeigen, die innerhalb einer Timeline auftreten.
title: Zeitleistenanzeigenklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Zeitleistenanzeigenklassen{#timeline-advertising-classes}

Diese Klassen liefern Informationen über Anzeigen, die innerhalb einer Timeline auftreten.

<table frame="all" colsep="1" rowsep="1" id="table_1A59E777BA99466793D586286F19E933"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Name </th> 
   <th colname="2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAd.html" format="html" scope="external"> PTAd</a> </td> 
   <td colname="2">Klasse, die die Anzeigenabstraktion definiert und alle Anzeigeninformationen enthält. Sie wird durch eine eindeutige ID, eine Dauer und eine MediaResource definiert. Die MediaResource enthält die URL, in der sich der tatsächliche Anzeigeninhalt befindet. 
    <pre>
      Stellt ein in den Inhalt aufgeteilt lineares primäres Asset dar. Sie kann optional ein Array von begleitenden Assets enthalten, die zusammen mit dem linearen Asset angezeigt werden müssen.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdAsset.html" format="html" scope="external"> PTAdAsset</a> </td> 
   <td colname="2">Klasse, die ein anzuzeigendes Asset darstellt. 
    <pre>
      Stellt ein anzuzeigendes Asset dar.
    </pre> 
    <pre>
      Klasse, die ein Anzeigen-Asset darstellt.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBannerView.html" format="html" scope="external"> PTAdBannerView</a> </td> 
   <td colname="2">
    <pre>
      Zeigt ein Banner-Asset an. Ihre Anwendung muss eine neue Instanz dieser Dienstprogrammklasse erstellen, das Banner-Asset festlegen und einer Ansicht hinzufügen. Das Impression- und Klick-Tracking für das Banner wird intern von dieser Klasse verwaltet.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBreak.html" format="html" scope="external"> PTAdBreak</a> </td> 
   <td colname="2">Klasse, die eine einheitliche Ansicht für mehrere Anzeigen bietet, die irgendwann während der Wiedergabe wiedergegeben werden. 
    <pre>
      Stellt eine kontinuierliche Abfolge von Anzeigen dar, die in den Inhalt aufgeteilt sind.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdClick.html" format="html" scope="external"> PTAdClick</a> </td> 
   <td colname="2">Klasse, die eine mit einem Asset verknüpfte Klickinstanz darstellt. Diese Instanz enthält Informationen zur Clickthrough-URL und zum Titel, die verwendet werden können, um dem Benutzer zusätzliche Informationen bereitzustellen. 
    <pre>
      Stellt eine mit einem Asset verknüpfte Klickinstanz dar. Diese Instanz enthält Informationen zur Clickthrough-URL und zum Titel, die verwendet werden können, um dem Benutzer zusätzliche Informationen bereitzustellen.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdPolicyInfo.html" format="html" scope="external"> PTAdPolicyInfo</a> </td> 
   <td colname="2"> Protokoll, das Eigenschaften für AdPolicySelector-API-Aufrufe definiert. Diese Eigenschaften bieten den Kontext für die Erzwingung jedes Anzeigenverhaltens. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PTAdPolicySelector</td> 
   <td colname="2"> Ein Anzeigenrichtlinienselektorprotokoll zum Erzwingen von Anzeigenverhalten. Anwendungen können diesem Protokoll entsprechen, indem sie alle erforderlichen Methoden implementieren oder die vorhandene Standard-Richtlinienauswahlklasse erweitern, um bestimmte Verhaltensweisen anzupassen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> PTAdTimeline</td> 
   <td colname="2"> Klasse, die die Zeitleiste der Pausen innerhalb des Inhalts darstellt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 
    <pre>
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTContentResolver.html" format="html" scope="external"> PTContentResolver</a> -Klasse, 
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolver.html" format="html" scope="external"> PTContentResolver</a> protocol
    </pre> </td> 
   <td colname="2"> Klasse, die den Teil zur Anzeigenauflösung im Adobe Primetime-Prozess für Anzeigenentscheidungen verarbeitet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolverDelegate.html" format="html" scope="external"> PTContentResolverDelegate</a> </td> 
   <td colname="2"> Protokoll, das die Methoden beschreibt, mit denen der benutzerdefinierte Content Resolver ( <span class="codeph"> PTContentResolver</span> ) sollte verwendet werden, um dem Delegate den Status der Auflösung von Inhalten mitzuteilen. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Constants/PTPlacementType.html" format="html" scope="external"> PTPlacementType</a> </td> 
   <td colname="2">Klasse, die eine Platzierungsinformationen-Anfrage abstrahiert. An jede aufgelöste Anzeige muss eine Platzierungsinformationen angehängt sein. Die Platzierungsinformationen beschreiben, wo die Anzeige in der Timeline platziert werden soll. Er enthält Informationen wie: 
    <ul id="ul_A9105A78F0C24488BCD5E3F2EE62A3EE"> 
     <li id="li_01E968A4330D4B40BA1EB6F4A6000FFD">Platzierung (in ms) </li> 
     <li id="li_A3DC9498BEE14FBA9E7A5D26874F3984">Platzierungstyp (Pre-Roll, Mid-Roll oder Post-Roll) </li> 
     <li id="li_4B9094DD318B4792854A377CC6064232">Dauer des Hauptinhaltsabschnitts, der ersetzt werden soll </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
