---
description: Diese Klassen beschreiben Ihren Medienplayer und seine Ressourcen.
title: Media Player-Klassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Media Player-Klassen {#media-player-classes}

Sie können die Objective-C-API des Primetime-Players verwenden, um das Verhalten des Players anzupassen.

Diese Klassen beschreiben Ihren Medienplayer und seine Ressourcen.

<table frame="all" colsep="1" rowsep="1" id="table_bm2_wl2_2m"> 
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Klasse</b> </td> 
   <td colname="2"><b>Beschreibung</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTABRControlParameters.html" format="html" scope="external"> PTABRControlParameters</a></span> </td> 
   <td colname="2">Umfasst alle Kontrollparameter für die adaptive Bit-Rate. Folgende Parameter werden unterstützt: 
    <ul id="ul_pnh_hm2_2m"> 
     <li id="li_46572FE1EB514AFF8C9F731E44DAF30B"><span class="codeph"> minBitRate</span> </li> 
     <li id="li_A10C75C9A5234241A5B84A4139F4D143"><span class="codeph"> maxBitRate</span> </li> 
     <li id="li_4E77E367A2E848D2B3E1A9C52209A7B2"><span class="codeph"> initialBitRate</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDefaultMediaPlayerClientFactory.html" format="html" scope="external"> PTDefaultMediaPlayerClientFactory</a></span> </td> 
   <td colname="2"> Standardimplementierung <span class="codeph"> PTMediaPlayerClientFactory</span> im TVSDK. Sie bietet die verfügbaren <span class="codeph"> PTOportunityResolver</span>, <span class="codeph"> PTContentResolver</span>, und <span class="codeph"> PTAdPolicySelector</span> Instanzen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html" format="html" scope="external"> PTMediaPlayer</a></span> </td> 
   <td colname="2">Definiert die Stammkomponente für das Primetime Player-Framework. <p>Anwendungen erstellen eine Instanz dieser Klasse, um ein Medium wiederzugeben. Diese Komponente sendet Benachrichtigungen, um Ihrer Anwendung den Status des Players jederzeit mitteilen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTMediaPlayerClientFactory.html" format="html" scope="external"> PTMediaPlayerClientFactory</a></span> </td> 
   <td colname="2"> Protokoll, das die Methoden beschreibt, die eine benutzerdefinierte Medienplayer-Client-Factory implementieren sollte, um die verfügbaren <span class="codeph"> PTOportunityResolver</span> , <span class="codeph"> PTContentResolver</span> und <span class="codeph"> PTAdPolicySelector</span> Instanzen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerItem.html" format="html" scope="external"> PTMediaPlayerItem</a></span> </td> 
   <td colname="2"> Stellt ein bestimmtes Audio-Video-Medium dar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerView.html" format="html" scope="external"> PTMediaPlayerView</a></span> </td> 
   <td colname="2"> Verwaltet die Ansichtskomponente des Primetime Player-Frameworks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaProfile.html" format="html" scope="external"> PTMediaProfile</a></span> </td> 
   <td colname="2"> Stellt das Profil eines einzelnen Streams in der Wiedergabeliste dar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaSelectionOption.html" format="html" scope="external"> PTMediaSelectionOption</a></span> </td> 
   <td colname="2">Stellt eine audiovisuelle Medienressource dar, die verschiedene Sprachvoreinstellungen, Barrierefreiheitsanforderungen oder benutzerdefinierte Anwendungskonfigurationen unterstützt. Gültige Optionstypen: 
    <ul id="ul_p2q_gn2_2m"> 
     <li id="li_46BE5AE49732481FB6D336FFF896E5AD">Untertitel (<span class="codeph"> PTMediaSelectionOptionTypeSubtitle</span>) </li> 
     <li id="li_6CEADCA12D4A48B7AE4A539985F32119">Alternatives Audio (<span class="codeph"> PTMediaSelectionOptionTypeAudio</span>) </li> 
     <li id="li_248D3D997F8A4B6E9B48869F84060D1F"> <p>Unbestimmt (<span class="codeph"> PTMediaSelectionOptionTypeUndefined</span>) </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTOpportunityResolver.html" format="html" scope="external"> PTOportunityResolver</a> </span> -Klasse, <span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTOpportunityResolver.html" format="html" scope="external"> PTOportunityResolver</a> protocol</span> </td> 
   <td colname="2"> Klasse, die für die Verarbeitung von In-Manifest-Hinweisen verwendet wird, die als Platzierungen für den Adobe Primetime-Anzeigenentscheidungsprozess verwendet werden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTOpportunityResolverDelegate.html" format="html" scope="external"> PTOportunityResolverDelegate</a></span> </td> 
   <td colname="2"> Protokoll, das die Methoden beschreibt, die der benutzerspezifische Opportunity-Resolver ( <span class="codeph"> PTOportunityResolver</span> ) sollte verwendet werden, um dem Delegaten den Status der Lösung der Chance zu kommunizieren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTSDK.html" format="html" scope="external"> PTSDK</a></span> </td> 
   <td colname="2"> Beschreibt die Version des TVSDK und seine Funktionen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTSDKConfig.html" format="html" scope="external"> PTSDKConfig</a></span> </td> 
   <td colname="2"> Stellt globale TVSDK-Einstellungen bereit und ermöglicht es einer Anwendung, benutzerdefinierte HLS-Tags zu abonnieren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTTextStyleRule.html" format="html" scope="external"> PTTextStyleRule</a></span> </td> 
   <td colname="2"> Definiert Konstanten, die Attributschlüssel des Textstils darstellen, die das Wörterbuch der Regeln bilden. </td> 
  </tr> 
 </tbody> 
</table>
