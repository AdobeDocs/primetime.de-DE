---
description: TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und nach dem Ende der linearen Anzeige oft auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.
title: Banneranzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# Begleitbanneranzeigen {#companion-banner-ads}

TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und nach dem Ende der linearen Anzeige oft auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.

Befolgen Sie bei der Anzeige von Begleithandanzeigen die folgenden Empfehlungen:

* Versuchen Sie, so viele Banneranzeigen wie möglich im Layout Ihres Players anzuzeigen.
* Bieten Sie ein begleitendes Banner nur dann an, wenn Sie eine Position haben, die exakt der angegebenen Höhe und Breite entspricht.

   >[!TIP]
   >
   >Ändern Sie die Größe des Banners nicht.

* Präsentieren Sie die begleitenden Banner so bald wie möglich nach Beginn der Anzeige.
* Überlagern Sie den Haupt-Anzeigen-/Video-Container nicht mit begleitenden Bannern.
* Anzeigen von Begleit-Bannern nach Ende der Anzeige fortsetzen.

   Der Standard besteht darin, jedes Begleitbanner anzuzeigen, bis Sie einen Ersatz für dieses Banner haben.

## Begleitbannerdaten {#companion-banner-data}

Der Inhalt eines PTAdAsset beschreibt ein begleitendes Banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Die `PTMediaPlayerAdStartedNotification`-Benachrichtigung gibt eine `PTAd`-Instanz zurück, die eine `companionAssets`-Eigenschaft enthält (Array von `PtAdAsset`).
Jedes `PtAdAsset` stellt Informationen zum Anzeigen des Assets bereit.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Verfügbare Informationen </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Breite des Begleitbanners in Pixel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Höhe des Begleitbanners in Pixel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ressourcentyp </td> 
   <td colname="col2">Der Ressourcentyp für dieses begleitende Banner: 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html: Die Daten sind im HTML-Code enthalten. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe: Die Daten sind eine iframe-URL (src). </li> 
     <li id="li_76B945007CE842158B5125422765E0B2">statisch: Bei den Daten handelt es sich um eine statische URL, bei der es sich um eine direkte URL zu einem Bild handelt. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> data </td> 
   <td colname="col2"> Die Daten des Typs, der von <span class="codeph"> resourceType</span> für dieses begleitende Banner angegeben wird. </td> 
  </tr> 
 </tbody> 
</table>

## Anzeigen von Banneranzeigen {#display-banner-ads}

Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und TVSDK erlauben, auf anzeigenbezogene Ereignis zu hören.

TVSDK stellt eine Liste begleitender Banneranzeigen bereit, die über das `PTMediaPlayerAdPlayStartedNotification`-BenachrichtigungsEreignis mit einer linearen Anzeige verknüpft sind.

Manifeste können begleitende Banneranzeigen wie folgt angeben:

* Ein HTML-Snippet
* Die URL einer iFrame-Seite
* Die URL einer statischen Bilddatei oder einer Flash-SWF-Datei einer Adobe

Für jede Begleitanzeige gibt TVSDK an, welche Typen für Ihre Anwendung verfügbar sind.

1. Erstellen Sie eine `PTAdBannerView`-Instanz für jeden begleitenden Anzeigensteckplatz auf Ihrer Seite.

       Stellen Sie sicher, dass folgende Informationen bereitgestellt wurden:
   
   * Damit keine begleitenden Anzeigen unterschiedlicher Größe abgerufen werden können, muss eine Bannerinstanz die Breite und Höhe angeben.
   * Standardmäßige Bannergrößen.

1. hinzufügen Sie einen Beobachter für das `PTMediaPlayerAdStartedNotification`, der Folgendes ausführt:
   1. Löscht vorhandene Anzeigen in der Bannerinstanz.
   1. Ruft die Liste der begleitenden Anzeigen von `Ad.getCompanionAssets` `PTAd.companionAssets` ab.
   1. Wenn die Liste der begleitenden Anzeigen nicht leer ist, müssen Sie die Liste für Bannerinstanzen durchlaufen.

      Jede Bannerinstanz ( &lt; a0/>) enthält Informationen wie Breite, Höhe, Ressourcentyp (html, iframe oder statisch) und Daten, die zum Anzeigen des begleitenden Banners erforderlich sind.`PTAdAsset`
   1. Wenn bei einer Videoanzeige keine begleitenden Anzeigen gebucht wurden, enthält die Liste der begleitenden Assets keine Daten für diese Videoanzeige.

      Um eine eigenständige Anzeige anzuzeigen, fügen Sie die Logik zu Ihrem Skript hinzu, um ein normales DFP (DoubleClick for Publishers)-Display-Tag in der entsprechenden Bannerinstanz auszuführen.
   1. Sendet die Bannerinformationen an eine Funktion auf Ihrer Seite, die die Banner an einer geeigneten Position anzeigt.

      Dies ist normalerweise ein `div` und Ihre Funktion verwendet das `div ID`, um das Banner anzuzeigen. Beispiel:

      ```
      - (void) onMediaPlayerAdPlayStarted:(NSNotification *) notification { 
          _currentAd  = [notification.userInfo  objectForKey:PTMediaPlayerAdKey];  
          if (_currentAd != nil) { 
              [self removeAllBanners]; // remove any existing PTAdBannerView views 
      
              // banners 
              if (_currentAd.companionAssets && _currentAd.companionAssets.count > 0) { 
                  PTAdAsset *bannerAsset = [_currentAd.companionAssets objectAtIndex:0]; 
      
                  PTAdBannerView *bannerView = [[PTAdBannerView alloc] initWithAsset:bannerAsset];  
                  bannerView.player = self.player; 
                  bannerView.delegate = self; 
      
                  bannerView.frame = CGRectMake(0.0, 0.0, bannerAsset.width, bannerAsset.height);  
                  [_adBannerView.bannerView addSubview:bannerView]; 
              } 
          } 
      }
      ```
