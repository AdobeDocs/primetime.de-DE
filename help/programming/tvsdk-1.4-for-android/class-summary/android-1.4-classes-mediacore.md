---
description: Sie können die Primetime Player-API verwenden, um das Verhalten des Players anzupassen.
seo-description: Sie können die Primetime Player-API verwenden, um das Verhalten des Players anzupassen.
seo-title: Mediacore-Klassen
title: Mediacore-Klassen
uuid: 2d4e41e6-e689-4f79-9021-1ab8ce0fe40d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mediacore-Klassen {#mediacore-classes}

Sie können die Primetime Player-API verwenden, um das Verhalten des Players anzupassen.

Die vollständige API-Dokumentation für TVSDK finden Sie unter [Adobe Primetime API-Referenzen](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).

Diese Klassen beschreiben Ihren Medienplayer und seine Ressourcen.
Paket: [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html)

<table frame="all" colsep="1" rowsep="1" id="table_2801E01282A948E6917910CA2FD1E05C"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> <p>Name </p> </th> 
   <th colname="2" class="entry"> <p>Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/ABRControlParameters.html" format="html" scope="external"> ABRControlParameters</a> ABRControlParameters</span> </td> 
   <td colname="2"> Klasse, die alle Kontrollparameter für die adaptive Bitrate enthält. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/AdClientFactory.html" format="html" scope="external"> AdClientFactory</a></span> </td> 
   <td colname="2"> Schnittstelle zum Erstellen von Opportunitätsdetektoren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/AdvertisingFactory.html" format="html" scope="external"> AdvertisingFactory</a></span> </td> 
   <td colname="2"> Factory-Klasse, die die Anpassung des Ad-Entscheidungsfindungsprozesses ermöglicht. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/BufferControlParameters.html" format="html" scope="external"> BufferControlParameters</a></span> </td> 
   <td colname="2"> Klasse, die alle Puffersteuerungsparameter kapselt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/DefaultAdPolicySelector.html" format="html" scope="external"> DefaultAdPolicySelector</a></span> </td> 
   <td colname="2"> Standardimplementierung für Verhalten bei der Anzeigenwiedergabe. Schnittstelle, die es Anwendungen ermöglicht, Anzeigenverhalten anzupassen.</td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/DefaultMediaPlayer.html" format="html" scope="external"> DefaultMediaPlayer</a></span> </td> 
   <td colname="2">Implementierung der Standardklasse der <span class="codeph"> MediaPlayer</span> -Schnittstelle. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html" format="html" scope="external"> MediaPlayer</a></span> </td> 
   <td colname="2">Öffentliche Schnittstelle für die <span class="codeph"> DefaultMediaPlayer</span> -Klasse. Umfasst Auflistungen für Ereignis, PlayerState und Sichtbarkeit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html" format="html" scope="external"> MediaPlayer.AdPlaybackEventListener</a></span> </td> 
   <td colname="2"> Schnittstellendefinition eines Satzes von Rückrufen, die während der Wiedergabe der Anzeige aufgerufen werden sollen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.DRMEventListener.html" format="html" scope="external"> MediaPlayer.DRMEventListener</a></span> </td> 
   <td colname="2"> Schnittstellendefinition eines Rückrufs, der aufgerufen wird, wenn geschützte Metadaten verfügbar werden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.EventListener.html" format="html" scope="external"> MediaPlayer.EventListener</a></span> </td> 
   <td colname="2"> Marker-Oberfläche zur Vereinheitlichung der Ereignis-Listener-Registrierung. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html" format="html" scope="external"> MediaPlayer.PlaybackEventListener</a></span> </td>
   <td colname="2"> Schnittstellendefinition eines Satzes von Callback, der während der Wiedergabe aufgerufen werden soll. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html" format="html" scope="external"> MediaPlayer.QOSEventListener</a></span> </td> 
   <td colname="2"> Schnittstellendefinition eines Satzes von Callback, der während der Servicequalität aufgerufen werden soll. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html" format="html" scope="external"> MediaPlayerItem</a></span> </td> 
   <td colname="2"> Schnittstelle, die Audio-Video-Medien darstellt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html" format="html" scope="external"> MediaPlayerItemLoader</a></span> </td> 
   <td colname="2"> Klasse, die eine Medienplayer-Ressource lädt und das entsprechende MediaPlayerItem-Objekt erstellt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html" format="html" scope="external"> MediaPlayerItemLoader.LoaderListener</a></span> </td> 
   <td colname="2"> Schnittstelle, die die mit dem MediaPlayerItemLoader-Objekt verknüpften Listener-Methoden definiert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerView.html" format="html" scope="external"> MediaPlayerView</a></span> </td> 
   <td colname="2"> Klasse für die Ansicht, die vom MediaPlayer für die Videowiedergabe verwendet wird. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaResource.html" format="html" scope="external"> MediaResource</a></span> </td> 
   <td colname="2"> Klasse, die alle Informationen zu einer Medienressource einbezieht. Beinhaltet Auflistung für den Medientyp. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/PlacementOpportunityDetector.html" format="html" scope="external"> PlacementOpportunityDetector</a></span> </td> 
   <td colname="2"> Schnittstelle zur Verarbeitung von In-Manifest-Hinweisen, die als Platzierungen für die Anzeigenentscheidung verwendet werden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/PSDKConfig.html" format="html" scope="external"> PSDKConfig</a></span> </td> 
   <td colname="2"> Klasse, die zusätzlich zu den Standard-Cue-Tags die vom Medienplayer beim Durchführen der Anzeigenplatzierung verwendeten benutzerdefinierten Tags enthält. Es enthält auch die Tag-Namen, über die die Anwendung benachrichtigt werden soll. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/TextFormat.html" format="html" scope="external"> TextFormat</a></span> </td> 
   <td colname="2"> Schnittstelle, die verschiedene Attribute enthält, die einen Textstil beschreiben (z. B. den Stil für geschlossene Beschriftungen). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/TextFormatBuilder.html" format="html" scope="external"> TextFormatBuilder</a></span> </td> 
   <td colname="2"> Klassenmethoden zum Festlegen der Formatierung von Text. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/Version.html" format="html" scope="external"> Version</a></span> </td> 
   <td colname="2"> Klasse, die die TVSDK-Version und -Beschreibung bereitstellt. </td> 
  </tr> 
 </tbody> 
</table>
