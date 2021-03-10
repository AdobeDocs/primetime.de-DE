---
title: Browser TVSDK 2.4 - Versionshinweise
description: Browser TVSDK 2.4 Versionshinweise beschreiben die neuen, unterstützten und nicht unterstützten Funktionen und die bekannten Probleme in Browser TVSDK 2.4.
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '6812'
ht-degree: 0%

---


# Browser TVSDK 2.4 - Versionshinweise {#browser-tvsdk-release-notes}

Browser TVSDK 2.4 Versionshinweise beschreiben die neuen, unterstützten und nicht unterstützten Funktionen und die bekannten Probleme in Browser TVSDK 2.4.

## Einführung {#introduction}

Browser TVSDK ist ein Toolkit, mit dem Sie Ihren Browser-basierten Video-Player-Anwendungen erweiterte Funktionen zur Videowiedergabe, zum Inhaltsschutz und zur Werbung hinzufügen können.

Browser TVSDK 2.4 bietet JavaScript-APIs zum Erstellen browserbasierter Videoanwendungen und unterstützt die Wiedergabe in den folgenden Modi:

* Nur HTML5
* HTML5 mit automatischem Flash-Fallback
* Flash immer

Diese Version enthält die folgenden Informationen:

・ [Browser TVSDK API-Dokumentation](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

・ [Browser TVSDK Programmleitfaden](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_browser-tvsdk.pdf).

・ [TVSDK for 1.4 DHLS to Browser TVSDK 2.4 Migration Guide](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

・ [Konvertieren von Browser TVSDK 2.4.6 in Version 2.4.7](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-246-to-247-for-javascript.html).

・ Eine Referenzimplementierung, die im Build enthalten ist.

>[!NOTE]
>
>*Eine vollständige Liste der Sicherheitserwägungen für diese Version finden Sie unter Sicherheitserwägungen.

## Neue und unterstützte Funktionen {#what-s-new-and-supported-features}

Diese Version von Browser TVSDK bietet neue Funktionen, mit denen Sie Ihre Videoanwendungen verbessern können.

**Neu in 2.4.12 Update (Build 204)**

Die folgende Ergänzung ist als Teil des Browser TVSDK 2.4.12-Updates (Build 204) verfügbar:

* Die Implementierung der Volume-API von AdobePSDK.MediaPlayer wurde geändert, um die automatische Wiedergabe unter iOS beim Stummschalten der Wiedergabe zu ermöglichen.

・ Eine neue API, `auditudeSettings.ignoreVPAIDAds`, wird hinzugefügt, damit VPAID-Anzeigen, die vom Auditude-Server empfangen wurden, ignoriert werden können. Die API funktioniert nicht bei Flash Fallback.

**Version 2.4.11**

Die folgenden Erweiterungen und Ergänzungen sind als Teil der Browser TVSDK 2.4.11-Version verfügbar:

・ HLS Live-Segmentfailover wird für MSE- und Flash-Fallback-Modi unterstützt.

・ Unterstützung für `AuditudeSettings.creativeRepackagingDomain` API ist jetzt auch für MSE verfügbar. Es wurde bisher nur im Ausweichmodus des Flashs unterstützt.

・ Das Release enthält Fehlerbehebungen bei kritischen Kundenproblemen. Siehe *Behobene Probleme* eine Liste.

**Version 2.4.10**

Die folgenden Erweiterungen und Ergänzungen sind als Teil der Browser TVSDK 2.4.10-Version verfügbar:

・ TVSDK stellt enableLogging() bereit, um die Protokollierung zu aktivieren oder zu deaktivieren. Weitere Informationen finden Sie in der [API-Dokumentation](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)zur Verwendung.

・ TVSDK unterstützt bei Verwendung von Adobe Analytics keine Standardkapitel mehr. Definieren und verwalten Sie Kapitel mit Ihrer Anwendung.

・ Das Release enthält Fehlerbehebungen bei kritischen Kundenproblemen. Siehe *Behobene Probleme *eine Liste.

**Version 2.4.9**

Die folgenden Erweiterungen und Ergänzungen sind als Teil der Browser TVSDK 2.4.9-Version verfügbar:

・ HLS VOD- und Live-Streams mit Zeitabweichung, aber ohne Diskontinuitätsmarkierungen werden unterstützt.

・ ID3-Frames der Version 2.4.0 werden mit dem Safari-Video-Tag für HLS VOD- und Live-Streams unterstützt.

・ Die Implementierung des sicheren Ladens von Anzeigen stellt sicher, dass Ad-Server-Aufrufe auf Basis der API-Konfiguration aktualisiert werden, um sicheres HTTP zu gewährleisten. Weitere Informationen finden Sie unter AdobePSDK.AdvertisingMetadata und AdobePSDK.ForceHttpsAdConfiguration-Klassen. Diese Funktion wird im Ausweichmodus des Flashs nicht unterstützt.

・ Ad-ID-Informationen und Erweiterungsinformationen, die mit VAST 3.0-Antworten verknüpft sind, werden nun von TVSDK zur Verfügung gestellt und können zur Implementierung der Moat-Integration für Anzeigenmessungen verwendet werden. Weitere Informationen finden Sie unter AdobePSDK.NetworkAdInfo-API. Dies wird im Ausweichmodus des Flashs nicht unterstützt.

・ Die AdobePSDK.ForceHttpsConfiguration-Klasse ist nicht mehr verfügbar. Sie wird durch

AdobePSDK.ForceHttpsAdConfiguration-Klasse.

・ Eine neue API, AdobePSDK.optimizeFlashCalls, ist jetzt verfügbar, um die Aufrufe zu optimieren und die Wiedergabe von HLS im Flash-Fallback-Modus zu verbessern. Dies ist standardmäßig deaktiviert.

**Neu in 2.4.8 Update (Build 6002)**

Dieses Update enthält Fehlerbehebungen bei kritischen Kundenproblemen. Siehe *Behobene Probleme* für die Liste.

**Version 2.4.8**

Die folgenden Erweiterungen und Ergänzungen sind im Rahmen der Browser TVSDK 2.4.8-Version verfügbar:

・ Das SDK ist nun mit dem Chrome-EME kompatibel und die Best Practices ändern sich ab Chrome v58. Weitere Informationen finden Sie unter [https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf](https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf)**

・ Das UI-Framework unterstützt jetzt den Arbeitsablauf für HLS-Zugriff auf DRM auf Flash, Nur Anzeige und Targeting-Info.

・ Die setDRMAuthenticateData-API wird dem UI-Framework hinzugefügt. Um mit Adobe Access DRM geschützte Streams wiederzugeben, rufen Sie diese API auf. Alternativ kann das Attribut drmAuthenticateData im Player angegeben werden. Weitere Informationen finden Sie unter [AdobePSDK.videoBehavior ](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/VideoBehavior.html).

**Version 2.4.7**

Die folgenden Funktionen sind in Version 2.4.7 neu:

・ Zusatz des UI-Konfigurators im UI-Framework

Sie können den Player auf eine der folgenden Arten konfigurieren:

・ Verwenden eines JSON-Objekts

・ Verwenden von APIs

Um das JSON-Objekt zu generieren, stellt Browser TVSDK ein **UI Configurator **Tool bereit.

In diesem Tool können Sie verschiedene Einstellungen auswählen, auf **Test Configuration **klicken, um die Einstellungen zu überprüfen, und auf **Download Configuration **klicken, um die Einstellungen herunterzuladen. Nach dem Herunterladen der Datei können Sie den Inhalt dieser Datei als JSON-Objekt an die API ptp.videoPlayer weiterleiten.

・ Hinzufügen der MediaPlayerItemConfig-API zum UI Framework

Mit MediaPlayerItemConfig können verschiedene Funktionen konfiguriert werden, wie z. B. werbungs-Metadaten, advertisingFactory, adSignalingMode, networkConfiguration, customRangeMetadata, useHardwareDecoder, subscribeTags, adTags, thumbnailScrubber, billingMetricsConfiguration. Weitere Informationen finden Sie in der Dokumentation zu AdobePSDK.MediaPlayerItemConfig in der [Browser TVSDK API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)* * [Dokumentation](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

Im UI-Framework wurde die Methode zum Übergeben von Netzwerkkonfigurationen über die Player-Konfiguration geändert.

**Version 2.4.6**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`networkConfiguration: <network configuration object>`

`}`

`};`

**Version 2.4.7**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`mediaPlayerItemConfig: {`

`networkConfiguration: <network configuration object>`

`}`

`}`

`};`

* Unterstützung für DRM- und Analytics-Workflows im UI-Framework

DRM-Konfigurationen und Analytics-Verfolgung können über das UI-Framework aktiviert werden.

* Zusatz der API `AdobePSDK.embedSWFinFullScreenDiv`

Diese neue API bietet Flexibilität bei der Auswahl der div-Datei, in die die Datei &quot;FlashFallback.swf&quot;eingebettet werden kann.

* `getVersion`API aus `AdobePSDK.MediaPlayer`-Klasse durch `AdobePSDK.Version`-Klasse für TVSDK-Versionsinformationen ersetzt. Weitere Informationen finden Sie unter `AdobePSDK.Version` API [hier](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.Version.html).

**Version 2.4.6**

Die folgenden Funktionen sind in Version 2.4.6 neu:

* **Unterstützung durchsuchen**

Mit &quot;Browserify&quot;können Sie die Stilmodule &quot;node.js&quot;im Browser verwenden. Sie können die Abhängigkeiten definieren und mit Browserify alles in einer JavaScript-Datei zusammenfasst.

* **Rechnungsstellung**

Mithilfe der Rechnungsstellung kann Browser TVSDK Player-Nutzungsmetriken erfassen, um Primetime-Kunden eine Rechnung zu machen.

>[!NOTE]
>
>Die veralteten Enum MediaPlayer.Ereignisses- und nicht mehr unterstützten Konstanten in Enum PSDKErrorCode wurden in Version 2.4.6 entfernt. Weitere Informationen finden Sie unter [Konvertieren von Browser TVSDK 2.4.5 in Version 2.4.6](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-245-to-246-for-javascript.html).

**Version 2.4.5**

Die folgenden Funktionen sind in Version 2.4.5 neu:

* **Wiederholungen und Anzeigen vollständiger Ereignisse**

   HLS Full Ereignis Replay (FER)-Streams unterstützen jetzt Anzeigenauflösung und Anzeigenverhalten. Um diese Unterstützung zu aktivieren, stellen Sie beim Erstellen des Objekts `MediaPlayerItemConfig` den Anzeigensignalisierungsmodus auf `MANIFEST_CUES` ein.

* **MediaPlayerView ScalePolicy-Unterstützung**

   Anwendungsentwickler können jetzt mithilfe der MediaView-Eigenschaft scalePolicy eine andere scalePolicy für die Ansicht angeben.

* **Unterstützung für anamorphe Inhalte**

   Die Wiedergabe von anamorphen Inhalten wird jetzt bei der Verwendung von MSE und der Wiedergabe von Flashs unterstützt.

* **Selektive Anwendung von`withCredentials`**

Wenn `withCredentials` auf &quot;true&quot;gesetzt ist, kann die `Access-Control-Allow-Origin`-Kopfzeile nicht auf eine Platzhalterkarte eingestellt werden. Je nach Antwort des Servers legt Browser TVSDK selektiv das `withCredentials`-Attribut fest. Weitere Informationen zu dieser Unterstützung finden Sie unter [Browser TVSDK API docs](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

**Version 2.4.4**

Die folgenden Funktionen wurden in Version 2.4.4 neu hinzugefügt:

* **Beispiel-App für Chromecast**

Diese Version unterstützt eine Sender- und Receiver-App, die die Wiedergabe von DASH-VOD-Streams und DASH-Widevine-Streams mit clientseitiger Anzeigeneinfügung demonstriert.

* **Erweiterte Failover-Unterstützung**

Diese Version enthält Unterstützung für erweiterte Failover-Nutzungsszenarien (Segment- und Server-Failover) für HLS VOD-Streams.

**Version 2.4.3**

Die folgenden Funktionen wurden in Version 2.4.3 neu hinzugefügt:

* **Benutzerdefinierte Tags für DASH VOD**

   Inline-Tags (Ereignis) können als TimedMetadata-Objekt abonniert und empfangen werden.

* **Wiedergabe von Streams ohne Erweiterungen**

   HLS- und DASH-Streams ohne Erweiterungen werden jetzt unterstützt. Für die Manifestdatei muss der resourceType beim Laden der Ressource angegeben werden. Bei Segmenten und VTT-Dateien wird der Content-Type-Antwortheader zur Bestimmung des Inhaltstyps verwendet.

**Version 2.4.2**

Die folgenden Funktionen wurden in Version 2.4.2 neu hinzugefügt:

* **API-Parität**

Eine vollständige Liste der API-Parität finden Sie im [TVSDK for 1.4 DHLS to Browser TVSDK 2.4 Migrationsleitfaden](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

* **Beispiel-AES-Unterstützung**

   Diese Version unterstützt jetzt die Wiedergabe von mit Sample-AES verschlüsselten Inhalten auf MSE und Flash-Fallback. Die Anforderung, AES-Inhalte über eine sichere Herkunft auf Google Chrome zu hosten, wurde entfernt.

* **Unterstützung für AAC-Container**

   Die Wiedergabe von Dateien mit der Erweiterung .aac wird jetzt unterstützt. Dies kann reiner Audio- oder alternativer Audio-Stream sein.

   >[!NOTE]
   >
   >AC3 und verbesserte AC3-Codecs werden noch nicht unterstützt.

* **Tokenisierte Stream-Wiedergabe**

HLS-Streams, die über ein Content Versand Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für die Manifestanforderungen und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Header bereitgestellt werden. Die Wiedergabe solcher Streams wird jetzt unterstützt.

**Version 2.4.1**

Die folgenden Funktionen wurden in Version 2.4.1 neu hinzugefügt:

* **UI-Framework**

Dieses Framework, das die Entwicklung der Benutzeroberfläche für JavaScript-basierte Videoplayer-Anwendungen beschleunigen soll, besteht aus APIs zum Einschließen grundlegender Steuerelemente wie Wiedergabe/Pause und Lautstärke sowie zum einfachen Hinzufügen oder Entfernen von Elementen wie Scrubbing-Status und Einstellungen für Untertitel. Sie können das mit Steuerelementen verknüpfte Verhalten festlegen, benutzerdefinierte Steuerelemente erstellen und die Benutzeroberfläche des Players per Skin gestalten. Dies alles geschieht über das Framework, ohne dass die DOM-Struktur direkt manipuliert werden muss.

* **HLS-Wiedergabeverbesserungen für Live-Streams**

Diese Version unterstützt Unterbrechungen, die durch Anzeigeneinfügungen verursacht werden. Es wird das EXT-PROGRAMM-DATE-TIME-Tag gefolgt vom EXT-MEDIA-SEQUENCE-Tag verwendet, um die Profile mit adaptiver Bitrate für eine reibungslose Wiedergabe zu synchronisieren.

* **VPAID 2.0-Unterstützung**

Die Version 2.0 (Video Player Ad-Serving Interface Definition, VPAID) bietet eine Rich-Media-Erfahrung für Benutzer und ermöglicht Herausgebern eine bessere Zielgruppe von Anzeigen, die Verfolgung von Anzeigenimpressionen und die Monetarisierung von Videoinhalten. Diese Version unterstützt lineare JavaScript VPAID-Anzeigen für Video-on-Demand-Inhalte (VOD).

* **Benutzerdefinierte HLS-Tags**

Medienstreams können zusätzliche Metadaten in Form von Tags in der Wiedergabeliste/Manifestdatei enthalten. Mit Browser TVSDK können Sie zusätzliche Tags angeben und abonnieren und benachrichtigt werden, wenn diese Tags im Manifest erscheinen.

* **Anzeigenmarken auf der Player-Zeitleiste**

Diese Version unterstützt das Anzeigen von Anzeigenmarken auf der Player-Zeitleiste für VOD- und Live-Inhalte. Sie können dieses Verhalten im Referenz-Player sehen.

**Unterstützt in 2.4**

Die folgenden Funktionen sind in Version 2.4 verfügbar:

* **MP3-Audiowiedergabe**

   Diese Version unterstützt die MP3-Audiowiedergabe in Browsern mit Media Source Extensions (MSE) und dem Safari-Video-Tag.

* **MP4-Videowiedergabe**

   Die folgenden Funktionen werden unterstützt:

   * Einzelstream-Wiedergabe
   * Pre-Roll- und Post-Roll-MP4-Anzeigen mit Anzeigenverhalten und Verfolgung
   * Pre-Roll- und Post-Roll-HLS-Anzeigen mit Anzeigenverhalten und Verfolgung
   * Pre-Roll- und Post-Roll-DASH-Anzeigen mit Anzeigenverhalten und Verfolgung

## Unterstützte Plattformen {#supported-platforms}

Browser TVSDK hat spezielle Anforderungen an die Ebenen von Plattformen und Software, auf denen es ausgeführt werden muss. Die folgenden Plattformen und Softwareebenen werden unterstützt:

### Desktop-Konfigurationen {#desktop-configurations}

* Microsoft Windows 7:

   * Internet Explorer 11+
   * Chrome 33+
   * Firefox 38+

* Microsoft Windows 8.1

   * Internet Explorer 11+
   * Chrome 33+
   * Firefox 38+

* Microsoft Windows 10

   * Edge+

* Apple OS X

   * Safari 9+
   * Chrome 33+
   * Firefox 38+

### Mobile Webkonfigurationen {#mobile-web-configurations}

* Android 4.4

   * Nativer Browser
   * Chrome 33+

* Android 5.0

   * Nativer Browser
   * Chrome 33+

* Android 6.0

   * ・ Chrome 33+

* Apple iOS 9

   * Safari 9+
   * Chrome 33+

* Apple iOS 10

   * Safari 9+
   * Chrome 33+

**Google Chromecast (zweite Generation); nur für DASH-Wiedergabe)**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Technologie</strong> </p> </td> 
   <td><p><strong>Browser TVSDK Video-Tag</strong><sup> 1</sup></p> </td> 
   <td><p><strong>Browser TVSDK MSE</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>Standardtechnik</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>iOS</p> </td> 
   <td><p>MP4 und HLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>-</p> </td> 
   <td><p>Video-Tag</p> </td> 
  </tr> 
  <tr> 
   <td><p>Android</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS und DASH</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Apple Safari 8</p> </td> 
   <td><p>MP4 und HLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4 und HLS</p> </td> 
   <td><p>Video-Tag</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS und DASH</p> </td> 
   <td><p>MP4 und HLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS und DASH</p> </td> 
   <td><p>MP4 und HLS</p> </td> 
   <td><p>MSE<sup>2</sup></p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 7)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4 und HLS</p> </td> 
   <td><p>Flash</p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 8.1)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS, DASH</p> </td> 
   <td><p>MP4 und HLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
 </tbody> 
</table>

## Funktionsmatrix {#feature-matrix}

Im Folgenden finden Sie eine Liste der unterstützten und nicht unterstützten Funktionen für diese Version:

* *MP3 Audio-Funktionen Core-Wiedergabe*
* *MP4-Videofunktionen Core-Wiedergabe*
* *MP4-Videofunktionen Core Ad Insertion*

>[!NOTE]
>
>*In den unten stehenden Funktionsmatrix-Tabellen bedeutet ein &quot;Y&quot;, dass die Funktion in der aktuellen Version unterstützt wird.*

### MP3-Audiofunktionen {#mp-audio-features}

**Tabelle 1: Core-Wiedergabe{#table-core-playback}**

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Wiedergabe | MP3 VOD | Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | Nicht unterstützt | Y | Y |

1 Das Browser TVSDK Video-Tag unterstützt kein Streaming und DRM. Die Codec- und Container-Unterstützung ist nicht in allen Browsern gleich.

2 Firefox verwendet standardmäßig Flash Player für Version 41 oder früher.

### MP4-Audiofunktionen {#mp-audio-features-1}

**Tabelle 2: Core-Wiedergabe**

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Wiedergabe | MP4 VOD | Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | Nicht unterstützt | Y | Y |

**Tabelle 3: Core Ad Insertion**

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | MP4 VOD | Pre-Roll (MP4) | Nicht unterstützt | Y | Y |
| Ad Insertion | MP4 VOD | Post-Roll (MP4) | Nicht unterstützt | Y | Y |

Weitere Informationen zur Unterstützung von HLS- oder DASH-Funktionen finden Sie unten.

## HLS-Funktionsmatrix {#hls-feature-matrix}

Hier finden Sie die Funktionsmatrix für die HLS-Funktionen in Browser TVSDK.

* *HLS Core-Wiedergabe*
* *HLS Advanced-Wiedergabe*
* *HLS-Inhaltsschutzfunktionen*
* *HLS Core-Anzeigeneinfügefunktionen*
* *HLS Erweiterte Anzeigeneinfügefunktionen*
* *HLS-Integrationen*

>[!NOTE]
>
>*In den unten stehenden Funktionsmatrix-Tabellen bedeutet ein &quot;Y&quot;, dass die Funktion in der aktuellen Version unterstützt wird.*

### HLS-Funktionen {#hls-features}

Die folgenden Funktionen werden unterstützt:

**Tabelle 4: HLS Core-Wiedergabe**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Allgemeine Wiedergabe (Wiedergabe, Pause, Suchen)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Allgemeine Wiedergabe (Wiedergabe, Pause und Suchen)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adaptive Bitrate</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>608/708 Beschriftungen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Nur VOD</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Manifest-Failover</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Erweiterte Failover</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Servicequalitäts- und Player-Benachrichtigungen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Eingeschränkte QoS-Unterstützung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Unterstützung für Cookie-Kopfzeilen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Festlegen von Puffersteuerungsparametern</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adaptive Einstellung</p> <p>Steuerelemente für Bitraten</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Benutzerdefinierte Tags</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td>Spätbindendes Audio</td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302 Umleitung</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 5: Erweiterte HLS-Wiedergabe-Funktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Wiedergabe beim Versatz</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Nur-Audio-Wiedergabe</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Trick Play</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Glatte Trick-Wiedergabe</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3-Analyse</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Unterstützung von Diskontinuitätsmarken</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Tokenisierte Streams</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Rechnungsstellung</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 6: HLS-Inhaltsschutzfunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhaltsschutz</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhaltsschutz</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Beispiel-AES</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhaltsschutz</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>Zugriff auf Adoben</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
   <td><p>FairPlay</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 7: HLS Core-Anzeigeneinfügefunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Pre-Roll (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Mid-Roll (HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Post-Roll (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Anzeigenauflösung und -verhalten</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Standard-Anzeigenrichtlinie</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Kreative Neuverpackung (MP4 in HLS)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 8: HLS Erweiterte Anzeigeneinfügefunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Nur Anzeige</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Targeting-Parameter</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Benutzerdefinierte Parameter</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Benutzerspezifische Anzeigenrichtlinie</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Verzögertes Laden von Werbeanzeigen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Begleitanzeigen, Banneranzeigen, klickbare Anzeigen</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>SWF</p> </td> 
   <td><p>JavaScript</p> </td> 
   <td><p>JavaScript</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 9: HLS-Integrationen{#table-hls-integrations}**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Integrationen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adobe Analytics VHL-Integration</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## DASH-Funktionsmatrix {#dash-feature-matrix}

Hier finden Sie die Funktionsmatrix für die DASH-Funktionen in Browser TVSDK.

・ *DASH-Core-Wiedergabe-Funktionen*

・ *DASH Erweiterte DASH-Wiedergabefunktionen*

・ *DASH-Inhaltsschutzfunktionen*

・ *DASH Core-Anzeigeneinfügefunktionen*

・ *DASH Erweiterte Anzeigeneinfügefunktionen*

・ *DASH-Integrationen*

>[!NOTE]
>
>In den unten stehenden Funktionsmatrix-Tabellen bedeutet ein Y, dass die Funktion in der aktuellen Version unterstützt wird.

### DASH-Funktionen {#dash-features}

Die folgenden Funktionen werden unterstützt:

**Tabelle 10: DASH-Core-Wiedergabe**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Allgemeine Wiedergabe (Wiedergabe, Pause, Suchen)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Allgemeine Wiedergabe (Wiedergabe, Pause und Suchen)</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adaptive Bitrate</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>608/708 Beschriftungen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Failover</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Servicequalitäts- und Player-Benachrichtigungen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Unterstützung für Cookie-Kopfzeilen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Festlegen von Puffersteuerungsparametern</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Festlegen der Steuerelemente für adaptive Bitraten</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Benutzerdefinierte Tags (EventStream)</p> </td> 
   <td><p>Nur VOD (Inline)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Spätgebundenes Audio</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302 Umleitung</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 11: DASH Advanced-Wiedergabe-Funktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Wiedergabe beim Versatz</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Nur-Audio-Wiedergabe</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Trick Play</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Glatte Trick-Wiedergabe</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3-Analyse</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Unterstützung über mehrere Jahre</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Tokenisierte Streams</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Rechnungsstellung</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 12: DASH-Inhaltsschutzfunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhaltsschutz</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhaltsschutz</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Beispiel-AES</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhaltsschutz</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>・ Widevine auf Chrome, Firefox 47 und höher und Chromecast</p> <p>・ PlayReady unter Internet Explorer unter Windows 8.1 und Edge</p> <p>・ Primetime DRM für Windows Firefox (nur Video)</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 13: DASH-Kern-Anzeigeneinfügefunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Pre-Roll (MP4/DASH)</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Mid-Roll (DASH)</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Post-Roll (MP4/DASH)</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Anzeigenauflösung und -verhalten</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Standard-Anzeigenrichtlinie</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Kreative Neuverpackung (MP4 bis DASH)</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 14: DASH Advanced Ad-Einfügefunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>HTML5</strong> FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Nur Anzeige</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Targeting-Parameter</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Benutzerdefinierte Parameter</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Benutzerspezifische Anzeigenrichtlinie</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Verzögertes Laden von Werbeanzeigen</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>begleitende Anzeigen, Banneranzeigen, anklickbare Anzeigen</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 15: DASH-Integrationen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Integrationen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adobe Analytics VHL-Integration</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## Behobene Probleme {#issues-fixed}

**In der Aktualisierung 2.4.12 behobene Probleme (Build 204)**

Die folgenden Probleme wurden in Browser TVSDK Version 2.4.12 Update (Build 204) behoben:

・ **21647**- TVSDK sollte die automatische Videowiedergabe auf iOS-Geräten ermöglichen, wenn Audio stummgeschaltet wird.

・ **21465**- Der Systemzugriff mit Fehlerschlüssel verweigert wird empfangen, wenn ein DRM-geschützter DASH-Stream wiedergegeben wird, nachdem ein DASH Live-Stream wiedergegeben wurde.

・ **21442**- Aktivieren Sie die automatische Wiedergabe von Inhalten im iOS Web, nachdem die Preroll-Anzeige mit einer Benutzergeste wiedergegeben wurde.

・ **21240**- Bereitstellung einer API zum Filtern von VPAID-Anzeigen, die aus Auditude/VMAP analysiert werden.

**In Version 2.4.11 behobene Probleme**

Die folgenden Probleme wurden in Browser TVSDK Version 2.4.11 behoben:

**Hauptwiedergabefunktionen:**

・ **19192**: TVSDK implementiert jetzt TextFormat:bottomInset und TextFormat:safeArea. Aufgrund dieser Verbesserungen können Untertitel neu positioniert werden, wenn die Steuerleiste auf dem Bildschirm angezeigt wird.

・ **21009**: Geschlossene Beschriftungen bleiben auf dem Bildschirm erhalten, wenn die Suche über die Kontinuität hinausgeht, bis neue Beschriftungen angezeigt werden.

・ **21141**: Die Suche wird aufgrund einer Racebedingung während des Segmentanhangs abgelehnt.

・ **21142**: Verfügbare Wiedergabe-Bereiche verfügbar machen, wenn der Player INITIALISIERT ist. Aufgrund dieser Änderungen wird jetzt die Beginn-Sitzung an der Position unterstützt.

・ **21363**: 608/708 Untertitel werden nach dem Einfügen der Anzeige für DASH-Streams nicht mehr synchronisiert.

**Anzeigeneinfügefunktionen:**

・ **21179**: Probleme im Zusammenhang mit dem Mitlauf (lange Pausen, schwarze Rahmen) mit VOD-Inhalten werden nun durch die korrekte Einstellung der Eigenschaft ad.primaryAsset.adParameters gelöst.

・ **21257**: Die MP4-Datei mit der höchsten Bitrate wird für die Transkodierung ausgewählt, wenn MP4 kein gültiger Mime-Typ ist und die Funktion zum Neupacken kreativer Elemente aktiviert ist.

・ **21361**: TVSDK übergibt nun Anzeigen- und Kreativsystem-IDs aus der VAST-Antwort als Abfrage-Parameter in der Creative Packaging-Anforderung, um zusätzliche Normalisierungsregeln zu unterstützen.

**In Version 2.4.10 behobene Probleme**

Die folgenden Probleme wurden in Browser TVSDK Version 2.4.10 behoben:

**Hauptwiedergabefunktionen:**

・ **21060**: Ungültiger Codec-Fehler bei HLS-Streams, die Diskontinuität und die ISO-BMFF-Felder enthalten, werden bis zum Ende des Streams ausgegeben.

・ **21045**: Die automatische Wiedergabe unter iOS funktioniert nicht, nachdem die erste Videowiedergabe in einer Wiedergabeliste abgeschlossen ist.

・ **20975**: Die Framerate wird vom QoS-Anbieter im Chrome-Browser als NaN zurückgegeben.

・ **20823**: Nicht unterstützter Codec-Fehler, der ausgegeben wird, wenn Segmente ohne Daten gefunden werden.

・ **20769**: SDK-Beginn mit der aktuellen Bitrate bei der Suche statt sofort basierend auf der ABR-Richtlinie zu wechseln.

・ **20031**: Wenn Sie sich im Hochformat in IE11 (Windows 8.1) befinden, wird der Videobildschirm klein. Inhaltsschutzfunktion:

・ **19316**: Segmente, bei denen die Entschlüsselung fehlschlägt, werden bei HLS-AES-128-Streams übersprungen.

**In Version 2.4.9 behobene Probleme**

Die folgenden Probleme wurden in Browser TVSDK Version 2.4.9 behoben:

**Hauptwiedergabefunktionen:**

・ **13407**: DASH-Streams können anhalten, wenn Firefox während der Wiedergabe das Senden des Ereignisses &quot;ontimeupdate&quot;beendet.

・ **16380**: Während der Wiedergabe von Videoinhalten mit gemischten Audiodaten in Segmenten, die nicht die gleichen Beginn über MSE aufweisen, wird der Fehler &quot;Audiosynchronisierung zwischen Repräsentationen&quot;auf ABR-Switches akkumuliert, was schließlich zu einem Fehler führt (Chrome-Problem #663686).

・ **17985**: Beim Abspielen eines bestimmten ISO-BMFF-Streams im Firefox-Browser wird die Wiedergabe gestoppt (Firefox-Problem #1342913). Dieses Problem wurde seit Firefox Version 53 behoben.

・ **19141**: Nicht gefangen (im Versprechen) ReferenceError: width ist nicht definiert.

・ **18997, 19299**: Problem mit dem Videoflimmern an der Segmentgrenze. Dies geschah, da SDK den Zeitversatz für die Komposition des letzten Beispiels nicht korrekt berechnete.

・ **19780**: Bei der Wiedergabe werden keine Beginn für HLS-Inhalte und HLS-Anzeigen in Firefox Version 53 (Firefox-Ausgabe #354653) ausgeführt.

・ **20046**: Programm Date Time wird als Schlüssel statt als Wert empfangen, wenn sie als zeitgesteuertes Metadatenobjekt empfangen wird.

・ **20047**: useDefaultResizeHandler gibt einen Fehler mit Flash-Fallback aus.

・ **20179**: Flash-Fallback funktioniert nicht mit Flash Player v25.0.0.171.

・ **20293**: Firefox stoppt die Pufferung von Daten für bestimmte HLS-Streams, die zum Anhalten führen.

・ **20626**: Der Player gibt in Chrome einen Mediendecode-Fehler aus, der auf eine fehlerhafte Handhabung von Videobeispielen mit null Dauer zurückzuführen ist.

・ **20078**: Die Wiedergabe wird bei Browserfehler &quot;QuotaExceeded&quot;angehalten.

・ **18639**: In HLS Live stream 608 CC wird Text manchmal als Rechtschreibfehler angezeigt.

・ **20028**: Der Parameter für die Größe von ClosedCaptions ändert die Schriftgröße nicht.

・ **20613**: Geschlossene Beschriftungsfelder überlappen sich gegenseitig, sodass sie unleserlich sind.

**Hauptfunktionen der Ad Insertion:**

・ **20043**: Fehlende Anzeigenimpressions- und Anzeigenverfolgungsaufrufe mit mehreren Anzeigen und Weiterleitungen von Drittanbietern.

・ **20044**: Wenn Sie kreative Umverpackungen verwenden, müssen alle Anzeigen in der Werbeunterbrechung erfolgreich neu verpackt werden, da sonst die Werbeunterbrechung vollständig verworfen wird.

・ **20097**: Die Anzeigenwiedergabe wird übersprungen und der Hauptinhalt wird sofort fortgesetzt, anstatt auf eine Zeitüberschreitung von 20 Sekunden zu warten, wenn kein Anzeigenmanifest verfügbar ist.

**In Version 2.4.8 Update behobene Probleme (Build 6002)**

Die folgenden Probleme wurden in Browser TVSDK Version 2.4.8 Update (Build 6002) behoben:

・ **14126:** Wiedergabe kann bei Firefox (Problem #1316024) aufgrund der internen Lücke im MSE-Quellpuffer anhalten. Versuchen Sie, die Wiedergabe fortzusetzen, um die Suche fortzusetzen

・ **19608:** Korrektur, um den Zeitversatzwert der VMAP-Antwort von Auditude zu berücksichtigen.

・ **19635:** Fehlerbehebungen Videostillstand in Internet Explorer 11 unter Windows 10.

・ **19761: Fehlerbehebungen bei ABR-Problemen mit HLS.**

・ **19780:** Korrigiert die Anzeigenwiedergabe mit HLS-Inhalten, die in Mozilla Firefox v53 fehlerhaft waren.

・ **19877 und 19744:** Die Probleme beheben die Inkonsistenz bei der Auswahl der Bitrate nach einem Suchvorgang. Die Bitratenauswahl bei der Suche ist nun der niedrigere Wert der aktuellen Bitrate und die Bitrate beim Beginn-Up.

・ **19881:** Wiedergabe-hängengeblieben und Pufferung-Überlagerung wird unendlich lange angezeigt, nachdem die Suche 3-4-mal durchgeführt wurde.

・ **19884:** Konformität mit den Anforderungen von Chrome 59 Beta Verified Media Path (VMP) bestätigen. bTVSDK konnte Widevine DRM-Inhalte mit Chrome 59 Beta wiedergeben.

・ **19916:** DRM-Wiedergabe auf UI-Framework wurde unterbrochen. Jetzt ruft sie &quot;acquisitionLicense&quot;auf, selbst wenn die Metadaten keine Richtlinie enthalten.

**In Version 2.4.8 behobene Probleme**

Die folgenden Probleme wurden in Browser TVSDK 2.4.8 behoben:

・ **10075**: Bei der Suche vor der Zeitschiene, play complete Ereignis wurde nicht empfangen in Firefox und Chrome und Suche Ereignis wurde nicht in Firefox empfangen.

・ **15775**: Spielen Sie komplettes Ereignis ab, das nicht unter Windows 8.1 Internet Explorer empfangen wurde.

・ **17306**: Bei SSAI-Streams wird die Wiedergabe unterstützt. Die Verfolgung von gehefteten Anzeigen wird nicht unterstützt.

・ **19142**: Manchmal führt der Rücklauf dazu, dass der Videoplayer für immer im Pufferzustand bleibt.

・ **19218**: Anzeigenmarken sind nicht über das UI-Framework verfügbar.

・ **19219**: Die Wiedergabe nur von Anzeigen funktioniert nicht über das UI-Framework.

・ **19222**: Der AES-128-Schlüssel wird einmal für eine Wiedergabeliste angefordert und nachfolgende Anforderungen werden aus dem Cache bereitgestellt. Zuvor wurde sie für jedes Segment angefordert.

・ **19597**: &quot;Nicht gefundener TypeError: Die Eigenschaft &#39;log&#39; von undefined&#39; konnte nicht gelesen werden.

・ **19605**: adRequestDomain war im Flash-Fallback-Modus nicht verfügbar.

・ **19608**: Für HLS Live Streams wurden keine VMAP-Anzeigen eingefügt. SDK berücksichtigt jetzt die Cue-Marker und verlässt sich nicht auf Zeitversatzwerte in VMAP-Antworten.

・ **19637**: Die Wiedergabe von Anzeigen führt nur zu einem Skriptfehler am Ende der Anzeige.

・ **19732**: CRS-Playlist-Anforderungen fehlschlugen mit 404-Fehler fehl. Die Anfragen 1401 und 1403 von Browser TVSDK werden nun aktualisiert, um dies zu gewährleisten.

・ **19762**: acquisitionLicense wurde früher vor setAuthenticationToken aufgerufen, aufgrund dessen unabhängig von der Token-Gültigkeit eine gültige Lizenz zurückgegeben wurde. Dieser Fehler wurde jetzt behoben und &quot;acquisitionLicense&quot;wird nur nach der setAuthenticationToken-Antwort aufgerufen.

**In Version 2.4.7 behobene Probleme**

Die folgenden Probleme wurden in Version 2.4.7 behoben:

・ **8397**: Über Adobe Mediums Server generierte HLS Live-Streams werden möglicherweise nicht wiedergegeben, wenn die Segmente nicht mit einem Schlüsselbild Beginn werden.

・ **13606**: Probleme mit mehreren Suchvorgängen wurden für den HLS-Stream im Chrome-Browser behoben.

・ **14807**: Wenn im Chrome-Browser unmittelbar nach play() die Suche oder Pause ausgelöst wird, wird die Wiedergabe möglicherweise mit dem Fehler DOMException beendet: Die play()-Anforderung wurde durch einen Aufruf unterbrochen...(Chrom-Problem# 593273).

・ **19085**: MediaPlayer-Parameter wie volume, abrControlParameters und ccStyle sind beim Zurücksetzen des Players nicht auf Default eingestellt.

**In Version 2.4.6 behobene Probleme**

Das folgende Problem wurde in Version 2.4.6 behoben:

・ **18093**: TimedMetadata für das Tag neben dem abonnierten Tag wird zurückgegeben, wenn Sie Flash Player 24 im Flash-Fallback-Modus verwenden.

**In Version 2.4.4 behobene Probleme**

Die folgenden Probleme wurden in Version 2.4.4 behoben:

・ **8711**: Bei MSE bleiben die Beschriftungen 608/708 standardmäßig ausgerichtet.

・ **13934**: ABR-Einstellungen für Anzeigen sind bei der Wiedergabe mit HLS Live Streams nicht anwendbar.

・ **14079**: Die Langlebigkeit von HLS Live Streams mit niedrigem DVR-Fenster kann fehlschlagen, da die Wiedergabe aufgrund von Netzwerklatenzproblemen möglicherweise zurückfällt. Klicken Sie auf den Live-Point, um die Wiedergabe fortzusetzen.

・ **15037**: Die mit dem Player-UI-Framework ausgelieferten Beispiele funktionieren unter Microsoft Internet Explorer 10 unter Windows 7 nicht.

・ **15913**: Bei HLS VOD-Streams wird der Stream in Chrome nicht wiedergegeben, wenn die Manifestantwort 304 nicht geändert wurde. Dieser Fehler wurde seit Chrome v55 behoben (Chrome-Problem 633696).

・ **16103**: Unter Android Chrome kann die Wiedergabe unter Bedingungen mit niedriger Bandbreite mit dem Uncatch-TypeError anhalten: Die Eigenschaft &#39;programmeDateTime&#39; des nicht definierten Fehlers kann nicht gelesen werden.

・ **16265**: Für HLS VOD- und Live-Streams suchen über Diskontinuitäten funktioniert nicht.

・ **16709**: Das Wiederaufnehmen des HLS Live-Streams mit PDT und Diskontinuitätsmarkierung kann dazu führen, dass der Player in der Pufferung hängen bleibt.

## Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

Die Einschränkungen und bekannten Probleme in Browser TVSDK werden unten erwähnt.

**Tabelle 16: Hauptwiedergabefunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhaltstyp</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Allgemeine Wiedergabe (Wiedergabe, Pause, Suche)</td> 
   <td><p>・ Andere Medienformate als HLS werden nicht unterstützt.</p> <p>8799: Flash-Fallback kümmert sich nicht um gemischte Inhalte. Daher muss sichergestellt werden, dass Inhalte, Anzeigen und andere URLs nicht zu gemischten Inhalten führen (sichere und unsichere Inhalte zusammen).</p> <p>・ 19271: Die Wiedergabe mit mehreren Ansichten über das UI-Framework wird im Ausweichmodus des Flashs nicht unterstützt.</p> <p>・ Flash-Fallback funktioniert unter Microsoft Internet Explorer 8 und 9 unter Windows 7 nicht, da diese Versionen vom SDK nicht unterstützt werden.</p> <p>・ 20262: Flash-Fallback fügt benutzerdefinierte Parameter zur Targeting-Info-Liste hinzu. Die Reihenfolge der benutzerdefinierten Parameter unterscheidet sich auch bei Flash und MSE.</p> <p>・ 20653:Browser TVSDK Flash Fallback funktioniert nicht auf Win10 mit Creators Update.</p> <p>・ Flash Fallback funktioniert mit Flash Player Version 23 und höher.</p> <p>・ 20087 - Chrome 59 Beta mit</p> <p>Flash 25.0.0.171</p> <p>Beta (Standard), HLS-Wiedergabe funktioniert nicht im Flash-Fallback-Modus. Es funktioniert gut auf Kanaren.</p> </td> 
   <td><p>・ 12563: Dash-Streams mit dem Audio-Codec mp4a.40.02 werden aufgrund der nicht unterstützten Audio-Codec-Zeichenfolge in MPD nicht in Firefox wiedergegeben. Audio Codec mp4a.40.2 wird unterstützt.</p> <p>15029: Beim Wechseln zwischen Videos in multiView in UI-Framework wird die Schaltfläche zum Abspielen/Anhalten nicht entsprechend aktualisiert.</p> <p>・ 16034:Unter Windows 8.1 IE führt der Aufruf von reset() zu einem unbekannten MIME-Typfehler. Bitte laden Sie die Medien neu, um die Wiedergabe fortzusetzen.</p> <p>・ 18235: Bestimmte Suchprobleme werden bei DASH-vod-Streams mit Anzeigen beobachtet.</p> <p>18727: Fehler-API wird für MSE nicht unterstützt</p> <p>18750: Die Ereignisse zur Statusänderung sind in einigen Fällen nicht in der richtigen Reihenfolge für SDK- und UI-Framework verfügbar. In UI-Framework fehlen möglicherweise die Ereignis IDLE und Initialisieren von StatusChange für die Ereignis-Listener, die nach dem Laden der Ressource hinzugefügt wurden.</p> <p>・ 18889: Wenn sich MediaPlayer im FEHLER-Status befindet, wird das Objekt "Ansicht"nicht zurückgegeben.</p> <p>・ 19039: Wenn AdobePSDK. MediaPlayer. "searchToLocal()"wird mit einem Wert größer als EOF verwendet, dann werden bei MSE Beginn für die Wiedergabe von Anfang an verwendet.</p> <p>・ 19049: Für Flash Player in Chrome, IE und Firefox wird kein Fehlerstatus gemeldet, wenn das Video während der Wiedergabe blockiert wird.</p> <p>・ 17205: Die Videowiedergabe wird beim Abspielen des ungemusterten Streams einige Stunden lang angehalten, während die Audiowiedergabe fortgesetzt wird (Chrome-Problem# 664033).</p> <p>・ 12308: Bei DASH-Streams mit der Angabe "zusammensetzung_time_offset"wird im Chrome-Browser möglicherweise "timeStampOffset"angewendet, was zu einer negativen Dekodierungszeit und somit zu einem MEDIA_ERR_ SRC_NOT_-UNTERSTÜTZTEN Fehler führt (Chrome-Problem #398141).</p> <p>・ 14126: Die Wiedergabe kann bei Firefox (Problem# 1316024) aufgrund der internen Lücke im MSE-Quellpuffer anhalten. Versuchen Sie, die Wiedergabe fortzusetzen, um die Suche fortzusetzen.</p> <p>・ 1915: MS Edge und IE 11 (Win 8.1 und 10) setzen die Herkunft bei der CORS-Umleitung nicht auf null und schlagen trotzdem fehl, da der Header nicht null ist und zu einem Wiedergabefehler führt.</p> <p>・ 19861: Problem mit dem Verhalten von Anhängen im Quellpuffer für bereits abgespielte Medien. Chrome lehnt das angehängte Fragment einschließlich moov ab, was zu einem anschließenden Dekodierungsfehler führt. (Chrom-Problem #735335)</p> <p>19921: Wiedergabe wird für bestimmte HLS-Inhalte gestoppt, obwohl sie erfolgreich gepuffert wurde (Chrome-Problem #713540)</p> <p>・ 20444:Beim Suchen nach dem Ende des gepufferten Bereichs in IE und Edge wird die Wiedergabe möglicherweise angehalten.</p> <p>・ 2011: Manchmal kann die Ablehnung von Suchvorgängen bei HLS-Streams mit oder ohne Anzeigen beobachtet werden.</p> <p>・ 20743: Unter Windows 10 Chrome wird der HLS Live-Stream einige Sekunden vor der Wiedergabe im MP4-Vorlauf wiedergegeben.</p> <p>・ 21043: Die Videodimension ist beim ersten Laden möglicherweise nicht korrekt, da Metadaten fehlen.</p> <p>・ 21115: Eine Android-Benutzergeste ist erforderlich, damit die Wiedergabe Beginn wird, wenn eine Pre-Roll-Anzeige für Videos in einer Wiedergabeliste verfügbar ist.</p> <p>・ HLS Live unterstützt keine Zeitstempelaktualisierung.</p> <p>・ AAC-SSR Audio wird nicht unterstützt.</p> <p>Audio-Codecs AC3 und Enhanced AC3 werden nicht unterstützt.</p> <p>・ Für Streams mit Zeitstempelabweichung, jedoch ohne Diskontinuitätsmarkierungen</p> <p>・ Die Wiedergabe kann aufgrund von Sprüngen fehlerhaft und die Suche fehlerhaft sein.</p> <p>・ Die Dauer von Inhalt und Wiedergabe stimmen möglicherweise nicht überein.</p> <p>・ Diskontinuitäten zwischen Darstellungen und Darstellungen sollten mit anderen Weisen übereinstimmen, können zu Problemen bei der Synchronisierung und zum Anhalten führen.</p> <p>・ Beschriftungen und WebVTT werden möglicherweise nicht nahe am Ende des Streams angezeigt.</p> <p>・ Audio-Codec-Änderungen werden bei Zeitstempelwechseln nicht unterstützt.</p> <p>・ Anzeigeneinfügung wird nicht unterstützt.</p> <p>・ Der schnelle Vorwärtstrick-Modus kann zu einer Wiedergabeschleife unter Win 8.1 IE 11 führen (MS-Problem #12446268).</p> <p>DASH:</p> <p>・ Live Streams - Live-Profil mit dynamischem Typ wird unterstützt.</p> <p>・ Für VoD-Streams - Live-Profil mit statischem Typ wird unterstützt.</p> <p>Für VoD-Streams - On-Demand-Profil ist nicht für Workflows zertifiziert.</p> </td> 
   <td><p>・ DASH Live- und DASH Video on Demand-Streams werden nicht unterstützt.</p> <p>・ PIP(Picture in Picture)-Videowiedergabe wird unter iOS im Vollbildmodus nicht unterstützt.</p> <p>Bei Safari (Video-Tag)-Erweiterung weniger Manifest ohne den richtigen Inhaltstyp Header funktioniert nicht.</p> </td> 
   <td><p>・ applicationID in sender app muss mit der beim Registrieren der URL des Empfängers als benutzerdefinierte Receiver-App identisch sein.</p> <p>・ Referenz Player ist für DASH Workflows zertifiziert. UI-Framework ist nicht zertifiziert.</p> <p>Die Liste der unterstützten Mediencodecs finden Sie unter <a href="https://developers.google.com/cast/docs/media"><em>hier</em></a>.</p> </td> 
  </tr> 
  <tr> 
   <td>FER VOD</td> 
   <td>Allgemeine Wiedergabe (Wiedergabe, Pause, Suche)</td> 
   <td> </td> 
   <td>18098: Bestimmte Suchprobleme werden mit dem HLS LBA FER-Stream beobachtet.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Adaptive Bitrate</td> 
   <td><p>・ 20079: Puffer muss bei Suche innerhalb des gepufferten Bereichs neu geschrieben werden.</p> <p>2008: Das ABR-Verhalten von Flashs stimmt mit dem von MSE überein.</p> </td> 
   <td><p>・ Nur Audio-Ausweichvariante in einem ABR-Stream wird aufgrund von Pufferbeschränkungen ignoriert.</p> <p>・ 12289: ABR-Steuerungsparameter gelten nicht für Audio bei ungemusterten HLS/DASH-Streams.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>608/708 Beschriftungen</td> 
   <td> </td> 
   <td><p>・ 7810: Unter Android 4.4.4 scheint Chrome keine Unterstützung für grundlegende CSS-Schriftfamilien zu haben, die vom Player verwendet werden. Daher funktioniert die Funktion zum Ändern des Schriftstils nicht.</p> <p>・ Bei 608 Beschriftungen können die CC-Kanal nicht geändert werden.</p> <p>・ Erweiterte Stilfunktionen werden für 608 Beschriftungen nicht unterstützt.</p> <p>Eingebettete Beschriftungen (608/708), die über das Tag "Ein-/Ausgabehilfe"signalisiert wurden, werden unterstützt.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>WebVTT</td> 
   <td> </td> 
   <td><p>・ 5206: Regions-Tags in der WebVTT-Datei werden vom Player bei der Anzeige der Beschriftungen ignoriert.</p> <p>・ DASH: Fragmentierte/segmentierte VTT-Dateien werden nicht unterstützt.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Manifest-Failover</td> 
   <td>21056: Bei Flash-Fallback tritt Failover für Live-Stream nicht auf, wenn der primäre Stream während der Wiedergabe einen 404-Fehler zurückgibt.</td> 
   <td>Manifest-Failover gilt nur für Inhalte und nicht für Anzeigen.</td> 
   <td>Fehlendes Wiedergabelisten-Failover funktioniert in Safari nur für HTTP-Fehlercode 404.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Erweiterte Failover</td> 
   <td> </td> 
   <td><p>・ Segment-Failover unterstützt nicht das Überspringen nicht verfügbarer Segmente und die weitere Wiedergabe.</p> <p>2053: Fehlende Segmente in einer Wiedergabeliste sollten als Diskontinuität behandelt werden und die Wiedergabe sollte vom nächsten verfügbaren Segment fortgesetzt werden.</p> <p>21267: Stream-Switching aufgrund eines Fehlers kann zum Herunterladen älterer Segmente führen.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Servicequalitäts- und Player-Benachrichtigungen</td> 
   <td>21129: Die Framerate ist nicht verfügbar, wenn der Flash ausfällt.</td> 
   <td><p>・ 11170:</p> <p>Timed_Ereignis ist nicht für Browser TVSDK mit MSE verfügbar, anders als für Browser TVSDK mit Flash Fallback.</p> <p>21129: Die Framerate wird für Live-Streams nicht berechnet.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Unterstützung für Cookie-Kopfzeilen</td> 
   <td> </td> 
   <td> </td> 
   <td><p>withCredentials-Flag- und Cookie-Kopfzeilen werden in Safari nicht unterstützt.</p> <p>21051: Um Cookies in Safari zuzulassen, aktivieren Sie die Einstellung "Cookies und Website-Daten" unter Voreinstellungen &gt; Datenschutz.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Benutzerdefinierte Tags</td> 
   <td>14763: Andere benutzerspezifische Tags als # sollten nicht unterstützt werden. Derzeit wird das TimedMetadata-Objekt während des Fallback des Flashs für solche Tags erstellt und berichtet.</td> 
   <td>Streams mit inband-benutzerdefinierten Tags sind nicht zertifiziert.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Verspätete Bindung</td> 
   <td> </td> 
   <td><p>・ Die Anzeigeneinfügung wird nicht von HLS Live LBA-Streams unterstützt.</p> <p>・ 17273: HLS VOD LBA-Streams wechseln im Falle eines Failover zur Standarddarstellung und können nicht zur zuletzt ausgewählten Version zurückgeschaltet werden.</p> <p>・ 20251: Der HLS Live LBA-Stream kann bei der Suche anhalten.</p> <p>・ 20497: Der Player bleibt im Pufferzustand, wenn in HLS-LBA-Unmuxed-Streams kurz vor dem Stream keine Audio- oder Videobilder fehlen.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>302 Umleitung</td> 
   <td> </td> 
   <td><p>15787: 302</p> <p>Die Umleitungsoptimierung wird in Windows-Browsern von Edge und IE nicht unterstützt, da diese die Eigenschaft responseURL im XMLHttpRequest-Objekt nicht unterstützen.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 17: Erweiterte Wiedergabe-Funktionen**

<table> 
 <tbody> 
  <tr> 
   <td>Inhaltstyp</td> 
   <td>Funktion</td> 
   <td>Flash</td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Wiedergabe beim Versatz</td> 
   <td><p>Das Starten der Wiedergabe bei einem bestimmten Offset-Wert wird nicht unterstützt.</p> </td> 
   <td>20492: Mid-Roll-Anzeigen vor dem Offset werden wiedergegeben, bevor der Inhalt vom Offset-Wert fortgesetzt wird.</td> 
   <td>Wiedergabe mit Offset wird unter iOS nicht unterstützt.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Trick Play</td> 
   <td>Smooth-Trickplay funktioniert nicht bei Streams ohne iFrame-Darstellungen.</td> 
   <td><p>・ Trick Play-Anpassungen werden in Firefox und Internet Explorer nicht unterstützt und daher ist der Reverse-Trick-Modus in diesen Browsern nicht verfügbar.</p> <p>・ Trickplay ist nicht verfügbar, wenn Inhalte zusammen mit Anzeigen wiedergegeben werden.</p> <p>・ 10435: Während der DASH-Wiedergabe friert das Video bei der vorwärts gerichteten Wiedergabe im Internet Explorer (Win 8.1) ein</p> <p>gelegentlich. Dies geschieht, da wir die video-Elemente playRate-Eigenschaft ohne Anpassung an die Trick-Wiedergabe verwenden.</p> <p>14182: Manchmal, während der Rücklauf auf Chrome-Browser, Suche Ereignis möglicherweise nicht empfangen werden und daher funktioniert der Trick-Modus nicht.</p> <p>・ 14942: Die Wiedergabegeschwindigkeit kann auch bei nicht-trick-basierten Wiedergabe-Streams in Chrome für Android eingestellt werden. Die Einstellung wird jedoch nicht angewendet und die Wiedergabe wird mit normaler Geschwindigkeit fortgesetzt.</p> <p>・ 17308: Die Suche funktioniert nicht im Trickplay-Modus.</p> <p>・ 17309: Im Chrome-Browser kann der Reverse-Trick-Modus nicht länger als 2 Sekunden aufrechterhalten werden.</p> <p>19272: Bei der Trick-Wiedergabe wird die Pufferung unter Windows 10 Edge im Falle von DASH-Streams möglicherweise nicht wiederhergestellt.</p> </td> 
   <td>Der Rückspultrickmodus wird nicht unterstützt.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>ID3-Analyse</td> 
   <td>20346: Das Textkodierungsbyte von ID3-Frames sollte auch von SDK zurückgegeben werden.</td> 
   <td><p>ID3-Tags, die in Datenübertragungsströmen (ADTS) verfügbar sind, werden vom SDK ignoriert.</p> <p>・ 12378: ID3-zeitgesteuerte Metadaten werden auf dem Flash und im Browser mit MSE-Unterstützung zu unterschiedlichen Zeitpunkten analysiert. Daher unterscheidet sich auch das Anzeigeverhalten auf der Zeitleiste des Referenzplayers.</p> <p>・ 19247: Die ID3-Analyse wird vom UI-Framework nicht unterstützt.</p> </td> 
   <td><p>・ 20323: Das zum Signalisieren des Zeitstempels des ersten Beispiels eines Segments verwendete PRIV ID3-Tag wird von Safari nicht analysiert (Safari-Problem #32422733)</p> <p>・ 20350: Auf bestimmten Geräten (einschließlich MAC OS X 10.1, iPad10) bietet Safari kein Cue-Change-Ereignis, wenn es sich im Trick-Modus befindet und daher keine ID3-Frames empfangen werden. (Safari-Problem #32450526)</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Unterstützung von Diskontinuitätsmarken</td> 
   <td> </td> 
   <td><p>・ Das Einfügen clientseitiger Anzeigen wird bei HLS-Streams mit Diskontinuität nicht unterstützt.</p> <p>・ Audio-Codec-Änderungen sind bei Unterbrechungen im HLS-Stream nicht zulässig.</p> <p>・ Der Audiospurschalter wird für HLS-Streams mit Diskontinuitätsmarkierungen nicht unterstützt</p> </td> 
   <td>Die Diskontinuitätssequenznummer ist eine Voraussetzung für die Wiedergabe von HLS-Streams mit Diskontinuität in Safari.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 18: Inhaltsschutzfunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhaltstyp</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>AES-128</td> 
   <td> </td> 
   <td>Der Bytebereich wird nicht mit AES-128-verschlüsselten Inhalten unterstützt.</td> 
   <td>12324: HLS AES-128 verschlüsselte Streams können nicht in Safari wiedergegeben werden, wenn das IV-Tag nicht angegeben ist.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>DRM</td> 
   <td> </td> 
   <td><p>・ 12660: Der HTML5-Player gibt einen internen Serverfehler für abgelaufene PlayReady-verschlüsselte Dasheinhalte aus.</p> <p>・ 16720: DASH DRM-verschlüsselte Inhalte funktionieren nicht, wenn das Beginn-Attribut im Punkt-Tag fehlt.</p> <p>・ 18589: Die Wiedergabe wird für DRM-geschützte Dash VoD-Multiperiod-Streams mit Xlink nicht unterstützt.</p> <p>・ 18653: Die Wiedergabe von umfangreichen MultiPeriod-Inhalten mit mehreren Schlüsseln wird beim ersten Punkt angehalten und kann nicht zum nächsten Zeitraum wechseln.</p> <p>・ 18656: MultiPeriod Stream, mit verschiedenen Schlüsseln verschlüsselt, wird nicht wiedergegeben.</p> <p>Play-ready 2.0 für Dash ist nicht zertifiziert.</p> <p> </p> <p> </p> </td> 
   <td>12602: HLS Fairplay DRM-Metadaten werden vom HTML5-Player in Safari wiederholt aktualisiert.</td> 
   <td><p>DASH Widevine DRM-Inhalte, die mit Bento4 verpackt werden, können wiedergegeben werden. Inhalte, die mit Offline Packager und Shaka Packager verpackt werden, werden nicht wiedergegeben. DASH PlayReady DRM wird nicht unterstützt.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 19: Hauptfunktionen der Ad Insertion (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhaltstyp</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Pre/Mid/Post</td> 
   <td> </td> 
   <td><p>・ Preroll-Anzeigen mit HLS-Live-Inhalt werden im Dual-Player-Modus abgespielt.</p> <p>・ DASH-Anzeigen mit HLS-Inhalten und HLS-Anzeigen mit DASH-Inhalten werden nicht unterstützt.</p> <p>・ 19002: In HTML5 Player mit MSE adBreak. insertType gibt keinen korrekten Wert zurück, um den richtigen Einfügetyp anzuzeigen, d. h. Client eingesteckt und/oder Server eingesteckt.</p> <p>7794: Auf Mobilgeräten (iOS, Android mit Chrome 33 oder niedriger oder nativer Browser), auf denen die Standardsteuerleiste im Vollbildmodus sichtbar ist, stehen bei der Wiedergabe von Anzeigen die Schaltflächen "Suchleiste"und "Vorwärts vorwärts"zur Verfügung.</p> <p>・ 11048: Der Wechsel von Anzeige zu HLS Live-Inhalt ist bei Media Source-Erweiterungen nicht reibungslos.</p> <p>・ 16083: Unter Android 4.4 Chrome v52 können HLS-Anzeigen mit HLS-Inhalt gelegentlich zu einem Pipelines-Dekodierungsfehler führen, nachdem die Wiedergabe angehalten wurde.</p> <p>・ 16097: Während des Werbeunterbrechens aufgetretene Fehler werden nicht verarbeitet. Dies kann dazu führen, dass der Hauptstream die Wiedergabe stoppt.</p> <p>・ 18095: MP4-Anzeigen werden von HLS-Live-Inhalten nicht unterstützt.</p> <p>19120: Mehrere Suchvorgänge bei HLS-Anzeigen mit HLS-Inhalten können dazu führen, dass der Stream die Wiedergabe stoppt.</p> <p>・ 19131: Beim Wechsel von Pre-Roll-Werbeunterbrechungen zu Inhalten kann es zu einer Pufferüberlagerung kommen.</p> <p>・ 20296: Bei HLS Live-Streams kann die Suche im DVR-Fenster, gefolgt von der Suche nach aufgelösten mid-Rollen, zu einem Abspielen führen.</p> <p>・ 20298:HLS Live Streams mit mittleren Rollen stall den Moment, in dem die erste Mid Roll-Anzeige aus dem DVR-Fenster zieht.</p> <p>・ 20317: HLS Live-Streams können beim Wechsel zur nächsten Anzeige oder von der Anzeige zum Inhalt anhalten, falls eine Werbeunterbrechung mehr als eine Anzeige enthält.</p> 
    <ul> 
     <li>Anzeigen im DVR-Fenster von HLS Live Streams werden nicht aufgelöst.</li> 
    </ul> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>SDK berücksichtigt keine Sequenzattribute in der VMAP-Antwort für VAST adSource.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>2079: Das SDK berücksichtigt nicht das Sequenzattribut innerhalb der VMAP-Antwort für VAST adSource.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VMAP 1.0</td> 
   <td> </td> 
   <td>12014: Das VMAP-Wiederholungsattribut wird nicht unterstützt.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Kreative Umverpackung</td> 
   <td> </td> 
   <td>21464: Die Anzeigenantwort wird vollständig verworfen, wenn eine kreative Neuverpackung für eine der Anzeigen in der Werbeunterbrechung fehlschlägt.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 20: Erweiterte Ad Insertion-Funktionen (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhaltstyp</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Nur Anzeige</td> 
   <td> </td> 
   <td>2005: Die Player-Technologie-Eigenschaft ist nicht relevant, da sie auf Hauptinhalt basiert, der bei Wiedergabe nur Anzeige leer ist.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Benutzerspezifische Anzeigenrichtlinie</td> 
   <td> </td> 
   <td><p>・ Anzeigenverhalten werden von MP4-Anzeigen und MP4-Inhalten nicht unterstützt.</p> <p>・ 13973: Benutzerdefiniertes Anzeigenverhalten - Die SKIP-Richtlinie löst bei Verwendung mit MSE kein vollständiges Ereignis aus.</p> <p>・ 14939: Richtlinien zum Überspringen und Überspringen von Werbeunterbrechungen für benutzerdefinierte Anzeigen funktionieren nicht für DASH-Inhalte.</p> <p>・ 17131: Der erste Anzeigenrahmen ist sichtbar und der Inhalt wird bei einer SKIP-Werbeunterbrechungsrichtlinie fortgesetzt.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Ergänzende Anzeigen/ Banneranzeigen/ anklickbare Anzeigen</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>Banneranzeigen sind bei Verwendung des Referenz-Players nicht sichtbar.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>VPAID 2.0</td> 
   <td> </td> 
   <td><p>・ Anzeigenverhalten werden für VPAID-Anzeigen nicht unterstützt.</p> <p>・ 15032: VPAID-Anzeigen in Kombination mit MP4- oder HLS-Anzeigen in einer Werbeunterbrechung werden nicht unterstützt.</p> <p>・ 19001: Unter Android und iOS, wenn VPAID-Anzeige mit MP4 wiedergegeben wird, da Audiospuren der Hauptinhalt-Dublette hörbar sind, eine von Hauptinhalten und eine von Anzeigen.</p> <p>・ 20762: VPAID-Anzeigen werden von Picture in Picture (PIP) nicht unterstützt.</p> <p>・ 21172: Für HLS VOD-Inhalte mit VPAID-Anzeigen wird kein Ereignis zum Abspielen empfangen.</p> <p>・ 21173: onAdBreakCompleteEvent wird nicht für HLS VOD-Inhalte und Post-Roll-VPAID-Anzeigen empfangen.</p> </td> 
   <td>Der Player wechselt zwischen dem normalen Modus und dem Vollbildmodus, während zwischen VPAID-Anzeige und Hauptinhalt gewechselt wird.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 21: Integrationen**

| **Inhaltstyp** | **Funktion** | **Flash** | **HTML5 in Firefox, IE, Chrome, Android Chrome** | **HTML5 in Safari, iOS Safari** | **Chromecast (nur DASH-Wiedergabe)** |
|---|---|---|---|---|---|
| VOD + Live | Adobe Analytics VHL-Integration |  | 19004: Die Verfolgung von Videoanalysen ist nicht über das UI Configurator Tool verfügbar. |  |  |

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).