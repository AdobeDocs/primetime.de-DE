---
description: TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und häufig nach dem Ende der linearen Anzeige auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.
title: Companion-Banneranzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Companion-Banneranzeigen {#companion-banner-ads}

TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und häufig nach dem Ende der linearen Anzeige auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.

Befolgen Sie beim Anzeigen von begleitenden Anzeigen die folgenden Empfehlungen:

* Versuchen Sie, so viele begleitende Banneranzeigen einer Videoanzeige wie im Layout Ihres Players verfügbar zu machen.
* Zeigen Sie ein begleitendes Banner nur dann an, wenn Sie eine Position haben, die genau der angegebenen Höhe und Breite entspricht.

  >[!TIP]
  >
  >Ändern Sie die Größe des Banners nicht.

* Präsentieren Sie die begleitenden Banner so bald wie möglich nach Beginn der Anzeige.
* Überlagern Sie den Haupt-Anzeigen-/Video-Container nicht mit begleitenden Bannern.
* Anzeigen von begleitenden Bannern nach Ende der Anzeige

  Die Standardeinstellung besteht darin, jedes begleitende Banner anzuzeigen, bis Sie einen Ersatz für dieses Banner haben.

## Companion-Bannerdaten {#companion-banner-data}

Der Inhalt eines PTAdAsset beschreibt ein begleitendes Banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Die `PTMediaPlayerAdStartedNotification` Eine Benachrichtigung gibt eine `PTAd` -Instanz, die `companionAssets` Eigenschaft (Array von `PtAdAsset`).
Jeder `PtAdAsset` enthält Informationen zum Anzeigen des Assets.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Verfügbare Informationen</b></th> 
   <th colname="col2" class="entry"><b>Beschreibung</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Breite des begleitenden Banners in Pixel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Höhe des begleitenden Banners in Pixel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ressourcentyp </td> 
   <td colname="col2">Der Ressourcentyp für dieses begleitende Banner: 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html: Die Daten befinden sich im HTML-Code. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe: Die Daten sind eine iFrame-URL (src). </li> 
     <li id="li_76B945007CE842158B5125422765E0B2">static: Die Daten sind statische URL, die direkt zu einem Bild URL ist. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> data </td> 
   <td colname="col2"> Die Daten des Typs, der durch <span class="codeph">resourceType</span> für dieses begleitende Banner. </td> 
  </tr> 
 </tbody> 
</table>

## Anzeigen von Banneranzeigen {#display-banner-ads}

Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass TVSDK auf anzeigenbezogene Ereignisse überwacht.

TVSDK bietet eine Liste mit begleitenden Banneranzeigen, die über die `PTMediaPlayerAdPlayStartedNotification` Benachrichtigungsereignis.

Manifeste können begleitende Banneranzeigen wie folgt spezifizieren:

* Ein HTML-Snippet
* Die URL einer iFrame-Seite
* Die URL eines statischen Bildes oder einer Adobe-Flash-SWF-Datei

TVSDK gibt für jede begleitende Anzeige an, welche Typen für Ihre Anwendung verfügbar sind.

1. Erstellen Sie eine `PTAdBannerView`  -Instanz für jeden begleitenden Anzeigenplatz auf Ihrer Seite.

       Stellen Sie sicher, dass die folgenden Informationen bereitgestellt wurden:
   
   * Um das Abrufen von begleitenden Anzeigen unterschiedlicher Größe zu verhindern, eine Bannerinstanz, die die Breite und Höhe angibt.
   * Standardmäßige Bannergrößen.

1. Fügen Sie einen Beobachter für die `PTMediaPlayerAdStartedNotification` das Folgendes bewirkt:
   1. Löscht vorhandene Anzeigen in der Bannerinstanz.
   1. Ruft die Liste der begleitenden Anzeigen von ab `Ad.getCompanionAssets` `PTAd.companionAssets`.
   1. Wenn die Liste der begleitenden Anzeigen nicht leer ist, navigieren Sie für Bannerinstanzen über die Liste.

      Jede Bannerinstanz ( `PTAdAsset`) Informationen wie Breite, Höhe, Ressourcentyp (HTML, iframe oder statisch) sowie Daten enthält, die zum Anzeigen des begleitenden Banners erforderlich sind.
   1. Wenn für eine Videoanzeige keine begleitenden Anzeigen gebucht wurden, enthält die Liste der begleitenden Assets keine Daten für diese Videoanzeige.

      Um eine eigenständige Display-Anzeige anzuzeigen, fügen Sie die Logik zu Ihrem Skript hinzu, um ein normales DFP-Display-Anzeigen-Tag (DoubleClick for Publishers) in der entsprechenden Bannerinstanz auszuführen.
   1. Sendet die Bannerinformationen an eine Funktion auf Ihrer Seite, die die Banner an einer geeigneten Stelle anzeigt.

      Dies ist normalerweise ein `div`und Ihre -Funktion verwendet die `div ID` , um das Banner anzuzeigen. Beispiel:

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
