---
title: Browser TVSDK 2.4 - Versionshinweise
description: In den Versionshinweisen zu Browser TVSDK 2.4 werden die neuen, unterstützten und nicht unterstützten Funktionen und die bekannten Probleme in Browser TVSDK 2.4 beschrieben.
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '6812'
ht-degree: 0%

---

# Browser TVSDK 2.4 - Versionshinweise {#browser-tvsdk-release-notes}

In den Versionshinweisen zu Browser TVSDK 2.4 werden die neuen, unterstützten und nicht unterstützten Funktionen und die bekannten Probleme in Browser TVSDK 2.4 beschrieben.

## Einführung {#introduction}

Browser TVSDK ist ein Toolkit, mit dem Sie erweiterte Funktionen zur Videowiedergabe, zum Inhaltsschutz und zur Werbung zu Ihren browserbasierten Video-Player-Anwendungen hinzufügen können.

Browser TVSDK 2.4 bietet JavaScript-APIs zum Erstellen browserbasierter Videoanwendungen und unterstützt die Wiedergabe in den folgenden Modi:

* Nur HTML5
* HTML 5 mit automatischem Flash-Fallback
* Flash immer

Diese Version enthält die folgenden Informationen:

・ [Dokumentation zur Browser TVSDK-API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

・ [Browser TVSDK-Programmierhandbuch](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_browser-tvsdk.pdf).

・ [Migrationshandbuch für TVSDK für 1.4 DHLS zu Browser TVSDK 2.4](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

・ [Konvertieren von Browser TVSDK 2.4.6 in Version 2.4.7](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-246-to-247-for-javascript.html).

・ Eine Referenzimplementierung, die im Build enthalten ist.

>[!NOTE]
>
>*Eine vollständige Liste der Sicherheitsüberlegungen für diese Version finden Sie unter Sicherheitsüberlegungen .

## Neue und unterstützte Funktionen {#what-s-new-and-supported-features}

Diese Version von Browser TVSDK bietet neue Funktionen, mit denen Sie Ihre Videoanwendungen verbessern können.

**Neu in Version 2.4.12 (Build 204)**

Die folgende Ergänzung ist als Teil des Browser TVSDK 2.4.12-Updates (Build 204) verfügbar:

* Die Implementierung der Volume-API von AdobePSDK.MediaPlayer wurde geändert, um die automatische Wiedergabe auf iOS zu ermöglichen, wenn die Wiedergabe stummgeschaltet ist.

・ eine neue API, `auditudeSettings.ignoreVPAIDAds`hinzugefügt, um das Ignorieren von VPAID-Anzeigen zu ermöglichen, die vom Auditude-Server empfangen wurden. Die API funktioniert nicht für Flash Fallback.

**Version 2.4.11**

Die folgenden Verbesserungen und Ergänzungen sind als Teil der Browser TVSDK-Version 2.4.11 verfügbar:

・ HLS Live Segment-Failover wird für MSE- und Flash-Fallback-Modi unterstützt.

・ Unterstützung für `AuditudeSettings.creativeRepackagingDomain` Die API ist jetzt auch für MSE verfügbar. Sie wurde bisher nur im Flash-Fallback-Modus unterstützt.

・ Die Version enthält Fehlerbehebungen für wichtige Kundenprobleme. Siehe *Behobene Probleme* eine Liste.

**Version 2.4.10**

Die folgenden Verbesserungen und Ergänzungen sind als Teil der Browser TVSDK-Version 2.4.10 verfügbar:

・ TVSDK stellt enableLogging() bereit, um die Protokollierung zu aktivieren oder zu deaktivieren. Siehe Abschnitt [API-Dokumentation](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)zur Verwendung.

・ TVSDK unterstützt bei Verwendung von Adobe Analytics keine Standardkapitel mehr. Definieren und verwalten Sie Kapitel mithilfe Ihrer Anwendung.

・ Die Version enthält Fehlerbehebungen für wichtige Kundenprobleme. Siehe *Behobene Probleme *eine Liste.

**Version 2.4.9**

Die folgenden Verbesserungen und Ergänzungen sind als Teil der Browser TVSDK-Version 2.4.9 verfügbar:

・ HLS VOD- und Live-Streams mit Zeitunterbrechung, aber ohne Diskontinuitätsmarkierungen werden unterstützt.

・ ID3-Frames der Version 2.4.0 werden mit dem Safari-Video-Tag für HLS VOD- und Live-Streams unterstützt.

・ Die sichere Implementierung des Ladens von Anzeigen stellt sicher, dass Ad-Server-Aufrufe basierend auf der API-Konfiguration auf sicheres HTTP aktualisiert werden. Weitere Informationen finden Sie unter Klassen AdobePSDK.AdvertisingMetadata und AdobePSDK.ForceHttpsAdConfiguration . Diese Funktion wird im Flash-Fallback-Modus nicht unterstützt.

・ Informationen zur Anzeigen-ID und Erweiterung, die mit VAST 3.0-Antworten verknüpft sind, werden jetzt von TVSDK der Anwendung zur Verfügung gestellt und können zur Implementierung der Moat-Integration für Anzeigenmessungen verwendet werden. Weitere Informationen finden Sie unter AdobePSDK.NetworkAdInfo-API. Dies wird im Flash-Fallback-Modus nicht unterstützt.

・ Die Klasse AdobePSDK.ForceHttpsConfiguration ist nicht mehr verfügbar. Sie wird durch

AdobePSDK.ForceHttpsAdConfiguration-Klasse.

・ Eine neue API, AdobePSDK.optimizeFlashCalls, ist jetzt verfügbar, um die Aufrufe zu optimieren, um die HLS-Wiedergabe im Flash-Fallback-Modus zu verbessern. Dies ist standardmäßig deaktiviert.

**Neu in Version 2.4.8 (Build 6002)**

Dieses Update enthält Fehlerbehebungen für wichtige Kundenprobleme. Siehe *Behobene Probleme*, für die Liste.

**Version 2.4.8**

Die folgenden Verbesserungen und Ergänzungen sind als Teil der Browser TVSDK-Version 2.4.8 verfügbar:

・ Das SDK ist jetzt mit dem Chrome-EME kompatibel und die Best Practices ändern sich ab Chrome-Version 58. Weitere Informationen finden Sie unter [https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf](https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf)**

・ Das UI-Framework unterstützt jetzt den Workflow HLS-Zugriff auf DRM auf Flash, Anzeigen und Targeting Info .

・ Die setDRMAuthenticateData-API wird dem UI-Framework hinzugefügt. Um mit Adobe Access DRM geschützte Streams wiederzugeben, rufen Sie diese API auf. Alternativ kann das Attribut drmAuthenticateData im Player angegeben werden. Siehe [AdobePSDK.videoBehavior](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/VideoBehavior.html)für Details.

**Version 2.4.7**

Die folgenden Funktionen sind in Version 2.4.7 neu:

・ Hinzufügung des UI-Konfigurators im UI Framework

Sie können den Player auf eine der folgenden Arten konfigurieren:

・ Verwenden eines JSON-Objekts

・ Verwendung von APIs

Um das JSON-Objekt zu generieren, stellt Browser TVSDK ein Tool für den Benutzeroberflächenkonfigurator bereit.

In diesem Tool können Sie verschiedene Einstellungen auswählen, auf &quot;Konfiguration testen&quot;klicken, um die Einstellungen zu überprüfen, und auf &quot;Konfiguration herunterladen&quot;klicken, um die Einstellungen herunterzuladen. Nach dem Herunterladen der Datei können Sie den Inhalt dieser Datei als JSON-Objekt an die API ptp.videoPlayer übergeben.

・ Hinzufügen der MediaPlayerItemConfig-API zum UI-Framework

Verschiedene Funktionen wie advertisingMetadata, advertisingFactory, adSignalingMode, networkConfiguration, customRangeMetadata, useHardwareDecoder, subscribeTags, adTags, thumbnailScrubber, billingMetricsConfiguration können über MediaPlayerItemConfig konfiguriert werden. Weitere Informationen finden Sie in der Dokumentation zu AdobePSDK.MediaPlayerItemConfig im Abschnitt [Browser TVSDK-API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)* * * [Dokumentation](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

Im UI Framework wurde die Methode zum Übergeben von Netzwerkkonfigurationen über die Player-Konfiguration geändert.

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

* Unterstützung für DRM- und Analytics-Workflows im UI Framework

DRM-Konfigurationen und das Analytics-Tracking können über das UI-Framework aktiviert werden.

* Zusatz von `AdobePSDK.embedSWFinFullScreenDiv` API

Diese neue API bietet Flexibilität für die Player-App bei der Auswahl des div-Elements, in das die FlashFallback.swf-Datei eingebettet werden kann.

* Ersetzt `getVersion`API von `AdobePSDK.MediaPlayer` -Klasse mit `AdobePSDK.Version` -Klasse für TVSDK-Versionsbezogene Informationen. Weitere Informationen finden Sie unter `AdobePSDK.Version` API [here](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.Version.html).

**Version 2.4.6**

Die folgenden Funktionen sind in Version 2.4.6 neu:

* **Unterstützung durchsuchen**

Mit Browserfy können Sie die Stilmodule node.js im Browser verwenden. Sie können die Abhängigkeiten definieren und Durchsuchen packt alles in eine JavaScript-Datei.

* **Rechnungsstellung**

Mithilfe der Rechnungsstellung kann Browser TVSDK Metriken zur Player-Nutzung erfassen, um Primetime-Kunden abzurechnen.

>[!NOTE]
>
>Die veralteten enum MediaPlayer.Events- und veralteten Konstanten in Enum PSDKErrorCode wurden in Version 2.4.6 entfernt. Weitere Informationen finden Sie unter [Konvertieren von Browser TVSDK 2.4.5 in Version 2.4.6](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-245-to-246-for-javascript.html).

**Version 2.4.5**

Die folgenden Funktionen sind in Version 2.4.5 neu:

* **Wiedergaben vollständiger Ereignisse und Anzeigen**

  HLS Full Event Replay (FER)-Streams unterstützen jetzt die Anzeigenauflösung und Anzeigenverhalten. Um diese Unterstützung zu aktivieren, legen Sie den Anzeigesignalmodus auf `MANIFEST_CUES` bei der Erstellung der `MediaPlayerItemConfig` -Objekt.

* **MediaLayerView ScalePolicy-Unterstützung**

  Anwendungsentwickler können jetzt mit der MediaView scalePolicy -Eigenschaft eine andere scalePolicy für die Ansicht angeben.

* **Unterstützung für anamorphe Inhalte**

  Die Wiedergabe von anamorphem Inhalt wird jetzt bei Verwendung von MSE und Flash-Wiedergabe unterstützt.

* **Selektive Anwendung von`withCredentials`**

Wann `withCredentials` auf &quot;true&quot;festgelegt ist, wird die `Access-Control-Allow-Origin` -Kopfzeile kann nicht auf eine Platzhalterkarte gesetzt werden. Abhängig von der Antwort des Servers legt Browser TVSDK selektiv die `withCredentials` -Attribut. Weitere Informationen zu diesem Support finden Sie unter [Browser TVSDK-API-Dokumente](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

**Version 2.4.4**

Die folgenden Funktionen waren in Version 2.4.4 neu:

* **Beispiel-App für Chromecast**

Diese Version bietet Unterstützung für eine Sender- und Empfänger-App, die die Wiedergabe von DASH-VOD-Streams und DASH-Widevine-Streams mit clientseitiger Anzeigeneinfügung demonstriert.

* **Erweiterte Failover-Unterstützung**

Diese Version enthält Unterstützung für erweiterte Failover-Anwendungsfälle (Segment- und Server-Failover) für HLS-VOD-Streams.

**Version 2.4.3**

Die folgenden Funktionen waren in Version 2.4.3 neu:

* **Benutzerdefinierte Tags für DASH VOD**

  Inline-benutzerdefinierte Tags (Ereignisse) können als TimedMetadata-Objekt abonniert und empfangen werden.

* **Wiedergabe von Streams ohne Erweiterungen**

  HLS- und DASH-Streams ohne Erweiterungen werden jetzt unterstützt. Für die Manifestdatei muss beim Laden der Ressource der resourceType angegeben werden. Bei Segmenten und VTT-Dateien wird der Content-Type-Antwortheader verwendet, um den Inhaltstyp zu bestimmen.

**Version 2.4.2**

Die folgenden Funktionen waren in Version 2.4.2 neu:

* **API-Parität**

Eine vollständige Liste der API-Parität finden Sie unter [Migrationshandbuch für TVSDK für 1.4 DHLS zu Browser TVSDK 2.4](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

* **Beispielunterstützung für AES**

  Diese Version unterstützt nun die Sample-AES-verschlüsselte Inhaltswiedergabe auf MSE und Flash Fallback. Die Anforderung, AES-Inhalte über sicheren Ursprung in Google Chrome zu hosten, wurde entfernt.

* **Unterstützung für AAC-Container**

  Die Wiedergabe von Dateien mit der Erweiterung .aac wird jetzt unterstützt. Dabei kann es sich um reine Audiostreams oder alternative Audioformate handeln.

  >[!NOTE]
  >
  >AC3 und erweiterte AC3-Codecs werden noch nicht unterstützt.

* **Tokenierte Stream-Wiedergabe**

HLS-Streams, die über ein Content Delivery Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für Manifest- und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Header bereitgestellt werden. Die Wiedergabe solcher Streams wird jetzt unterstützt.

**Version 2.4.1**

Die folgenden Funktionen waren in Version 2.4.1 neu:

* **UI-Framework**

Dieses Framework, das die Entwicklung der Benutzeroberfläche für JavaScript-basierte Video-Player-Anwendungen beschleunigen soll, besteht aus APIs zum Einschließen grundlegender Steuerelemente wie Wiedergabe/Pause und Lautstärke sowie zum einfachen Hinzufügen oder Entfernen von Elementen wie Scrubbing-Balkenstatus und Einstellungen für geschlossene Beschriftungen. Sie können das Verhalten angeben, das mit Steuerelementen verknüpft ist, benutzerdefinierte Steuerelemente erstellen und die Player-Benutzeroberfläche gestalten. Dies alles geschieht über das Framework, ohne dass die DOM-Struktur direkt bearbeitet werden muss.

* **HLS-Wiedergabeverbesserungen für Live-Streams**

Diese Version unterstützt Unterbrechungen, die durch das Einfügen von Anzeigen verursacht werden. Es verwendet das Tag EXT-PROGRAM-DATE-TIME , gefolgt vom Tag EXT-MEDIA-SEQUENCE , um für eine reibungslose Wiedergabe über adaptive Bitratenprofile zu synchronisieren.

* **VPAID 2.0-Unterstützung**

Die VPAID-Definition (Video Player Ad-Serving Interface Definition), Version 2.0, bietet Anwendern ein Rich-Media-Erlebnis und ermöglicht es Herausgebern, Anzeigen gezielter anzusprechen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren. Diese Version unterstützt lineare JavaScript-VPAID-Anzeigen für Video-on-Demand (VOD)-Inhalte.

* **Benutzerdefinierte HLS-Tags**

Medien-Streams können zusätzliche Metadaten in Form von Tags in der Wiedergabeliste/Manifestdatei enthalten. Mit Browser TVSDK können Sie zusätzliche Tags angeben und abonnieren und benachrichtigt werden, wenn diese Tags im Manifest erscheinen.

* **Auf der Player-Timeline angezeigte Anzeigenmarken**

Diese Version unterstützt das Anzeigen von Anzeigenmarken in der Player-Timeline für VOD- und Live-Inhalte. Sie können dieses Verhalten im Referenz-Player sehen.

**Unterstützt in 2.4**

Die folgenden Funktionen waren in Version 2.4 verfügbar:

* **MP3-Audiowiedergabe**

  Diese Version unterstützt die MP3-Audiowiedergabe in Browsern mit Media Source Extensions (MSE) und dem Safari-Video-Tag.

* **MP4-Videowiedergabe**

  Die folgenden Funktionen werden unterstützt:

   * Single-Stream-Wiedergabe
   * Pre-Roll- und Post-Roll-MP4-Anzeigen mit Anzeigenverhalten und Tracking
   * Pre-Roll- und Post-Roll-HLS-Anzeigen mit Anzeigenverhalten und Tracking
   * Pre-Roll- und Post-Roll-DASH-Anzeigen mit Anzeigenverhalten und Tracking

## Unterstützte Plattformen {#supported-platforms}

Browser TVSDK hat spezifische Anforderungen an die Ebenen von Plattformen und Software, auf denen es ausgeführt werden muss. Die folgenden Plattformen und Softwareebenen werden unterstützt:

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

* APPLE OS X

   * Safari 9+
   * Chrome 33+
   * Firefox 38+

### Mobile Web-Konfigurationen {#mobile-web-configurations}

* Android 4.4

   * Nativer Browser
   * Chrome 33+

* Android 5.0

   * Nativer Browser
   * Chrome 33+

* Android 6.0

   * ・ Chrome 33+

* APPLE IOS 9

   * Safari 9+
   * Chrome 33+

* Apple iOS 10

   * Safari 9+
   * Chrome 33+

**Google Chromecast (zweite Generation, nur für DASH-Wiedergabe)**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Technologie</strong> </p> </td> 
   <td><p><strong>Browser TVSDK-Video-Tag</strong><sup>1</sup></p> </td> 
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

* *MP3-Audiofunktionen - Core-Wiedergabe*
* *MP4-Videofunktionen - Core-Wiedergabe*
* *MP4-Videofunktionen - Core-Ad Insertion*

>[!NOTE]
>
>*In den Tabellen mit Funktionsmatrix unten bedeutet ein &quot;Y&quot;, dass die Funktion in der aktuellen Version unterstützt wird.*

### MP3-Audiofunktionen {#mp-audio-features}

**Tabelle 1: Core-Wiedergabe{#table-core-playback}**

| Kategorie | Content-Typ | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Wiedergabe | MP3 VOD | Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | Nicht unterstützt | Y | Y |

1 Das Browser TVSDK Video-Tag unterstützt kein Streaming und DRM. Die Codec- und Container-Unterstützung ist nicht in allen Browsern identisch.

2 Firefox verwendet standardmäßig Flash Player für Version 41 oder früher.

### MP4-Audiofunktionen {#mp-audio-features-1}

**Tabelle 2: Core-Wiedergabe**

| Kategorie | Content-Typ | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Wiedergabe | MP4 VOD | Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | Nicht unterstützt | Y | Y |

**Tabelle 3: Core-Ad Insertion**

| Kategorie | Content-Typ | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | MP4 VOD | Pre-roll (MP4) | Nicht unterstützt | Y | Y |
| Ad Insertion | MP4 VOD | Post-Roll (MP4) | Nicht unterstützt | Y | Y |

Weitere Informationen zur Unterstützung von HLS- oder DASH-Funktionen finden Sie unten.

## HLS-Funktionsmatrix {#hls-feature-matrix}

Hier finden Sie die Funktionsmatrix für die HLS-Funktionen im Browser TVSDK.

* *HLS-Core-Wiedergabe*
* *HLS Advanced-Wiedergabefunktionen*
* *HLS-Inhaltsschutzfunktionen*
* *HLS Core-Anzeigeneinfüge-Funktionen*
* *HLS Erweiterte Anzeigeneinfüge-Funktionen*
* *HLS-Integrationen*

>[!NOTE]
>
>*In den Tabellen mit Funktionsmatrix unten bedeutet ein &quot;Y&quot;, dass die Funktion in der aktuellen Version unterstützt wird.*

### HLS-Funktionen {#hls-features}

Die folgenden Funktionen werden unterstützt:

**Tabelle 4: HLS-Core-Wiedergabe**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML 5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Allgemeine Wiedergabe (Wiedergabe, Pause, Suche)</p> </td> 
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
   <td><p>608/708 Untertitel</p> </td> 
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
   <td><p>Erweitertes Failover</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>QoS- und Player-Benachrichtigungen</p> </td> 
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
   <td><p>Einrichten von Puffersteuerparametern</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adaptive Einstellung festlegen</p> <p>Bitratenkontrollen</p> </td> 
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
   <td>Spätbindende Audiowiedergabe</td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302-Umleitung</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 5: Erweiterte HLS-Wiedergabefunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML 5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Wiedergabe mit Versatz</p> </td> 
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
   <td><p>Glätte Trick Play</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3-Parsing</p> </td> 
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
   <td><p><strong>HTML 5: Safari, iOS Safari</strong></p> </td> 
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
   <td><p>Sample-AES</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhaltsschutz</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>Adobe-Zugriff</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
   <td><p>FairPlay</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 7: HLS-Core-Anzeigeneinfüge**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML 5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Pre-roll (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Mid-roll (HLS)</p> </td> 
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

**Tabelle 8: HLS Erweiterte Anzeigeneinfüge-Funktionen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Kategorie</strong></p> </td> 
   <td><p><strong>Inhaltstyp</strong></p> </td> 
   <td><p><strong>Funktion</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML 5: Safari, iOS Safari</strong></p> </td> 
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
   <td><p>Benutzerdefinierte Anzeigenrichtlinie</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Verzögertes Laden von Anzeigen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
   <td><p>Plattformbeschränkung</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Companion-Anzeigen, Banneranzeigen, klickbare Anzeigen</p> </td> 
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
   <td><p><strong>HTML 5: Safari, iOS Safari</strong></p> </td> 
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

Hier finden Sie die Funktionsmatrix für die DASH-Funktionen im Browser TVSDK.

・ *DASH-Core-Wiedergabefunktionen*

・ *DASH Advanced-Wiedergabefunktionen*

・ *DASH-Inhaltsschutzfunktionen*

・ *DASH-Core-Anzeigeneinfüge-Funktionen*

・ *DASH Erweiterte Anzeigeneinfüge-Funktionen*

・ *DASH-Integrationen*

>[!NOTE]
>
>In den unten stehenden Tabellen der Funktionsmatrix bedeutet ein Y, dass die Funktion in der aktuellen Version unterstützt wird.

### DASH-Funktionen {#dash-features}

Die folgenden Funktionen werden unterstützt:

**Tabelle 10: DASH-Core-Wiedergabefunktionen**

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
   <td><p>Allgemeine Wiedergabe (Wiedergabe, Pause, Suche)</p> </td> 
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
   <td><p>608/708 Untertitel</p> </td> 
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
   <td><p>QoS- und Player-Benachrichtigungen</p> </td> 
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
   <td><p>Einrichten von Puffersteuerparametern</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Festlegen von adaptiven Bitratensteuerelementen</p> </td> 
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
   <td><p>Verspätete Audiowiedergabe</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302-Umleitung</p> </td> 
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
   <td><p>Wiedergabe mit Versatz</p> </td> 
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
   <td><p>Trick play</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Glätte Trick Play</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3-Parsing</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Wiedergabe</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Unterstützung für mehrere Zeiträume</p> </td> 
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
   <td><p>Sample-AES</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhaltsschutz</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>・ Widevine auf Chrome, Firefox 47 und höher und Chromecast</p> <p>・ PlayReady in Internet Explorer unter Windows 8.1 und Edge</p> <p>・ Primetime DRM für Windows Firefox (nur Video)</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 13: DASH-Core-Anzeigeneinfüge-Funktionen**

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
   <td><p>Pre-roll (MP4/DASH)</p> </td> 
   <td><p>Nur VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Mid-roll (DASH)</p> </td> 
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
   <td><p>Auflösung und Verhalten von Anzeigen</p> </td> 
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
   <td><p>Kreative Neuverpackung (MP4 in DASH)</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 14: DASH Advanced Ad Insertion Features**

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
   <td><p>Benutzerdefinierte Anzeigenrichtlinie</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Verzögertes Laden von Anzeigen</p> </td> 
   <td><p>Nicht unterstützt</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Companion-Anzeigen, Banneranzeigen, anklickbare Anzeigen</p> </td> 
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

**Behobene Probleme in Version 2.4.12 (Build 204)**

Die folgenden Probleme wurden in der Browser TVSDK-Version 2.4.12 Update (Build 204) behoben:

・ **21647**- TVSDK sollte die automatische Videowiedergabe auf iOS-Geräten zulassen, wenn Audio stummgeschaltet ist.

・ **21465**- Fehlerschlüssel Systemzugriff verweigert wird empfangen, wenn ein DRM-geschützter DASH-Stream wiedergegeben wird, nachdem ein DASH-Live-Stream wiedergegeben wurde.

・ **21442**- Aktivieren Sie die automatische Wiedergabe von Inhalten im iOS Web, nachdem die Pre-oll-Anzeige mit einer Benutzergeste wiedergegeben wurde.

・ **21240**- API zum Filtern von VPAID-Anzeigen bereitgestellt, die von Auditude/VMAP geparst wurden.

**In Version 2.4.11 behobene Probleme**

Die folgenden Probleme wurden in der Browser TVSDK-Version 2.4.11 behoben:

**Kernwiedergabefunktionen:**

・ **19192**: TVSDK implementiert jetzt TextFormat:bottomInset und TextFormat:safeArea. Aufgrund dieser Verbesserungen können geschlossene Beschriftungen neu positioniert werden, wenn die Steuerleiste auf dem Bildschirm angezeigt wird.

・ **21.09**: Geschlossene Untertitel bleiben auf dem Bildschirm erhalten, wenn Sie über einen Unterbrechungsvorgang hinweg suchen, bis neue Untertitel angezeigt werden.

・ **21141**: Die Suche wird aufgrund einer Race-Bedingung beim Anhängen eines Segments abgelehnt.

・ **2142**: Verfügbar machen suchbarer Wiedergabefelder, wenn der Player im INITIALISIERTEN Status ist. Aufgrund dieser Änderungen wird die Sitzung an Position starten jetzt unterstützt.

・ **21363**: 608/708 geschlossene Untertitel werden nach dem Einfügen von Anzeigen für DASH-Streams nicht mehr synchronisiert.

**Anzeigeneinfüge-Funktionen:**

・ **21179**: Mid-Roll-bezogene Probleme (lange Pausen, schwarze Rahmen) mit VOD-Inhalt werden jetzt behoben, indem die Eigenschaft ad.primaryAsset.adParameters korrekt festgelegt wird.

・ **21257**: Die MP4-Datei mit der höchsten Bitrate wird für die Transkodierung ausgewählt, wenn MP4 kein gültiger MIME-Typ ist und die Funktion für die kreative Neuverpackung aktiviert ist.

・ **21361**: TVSDK übergibt jetzt das Anzeigensystem und die kreative ID aus der VAST-Antwort als Abfrageparameter in der kreativen Verpackungsanfrage, um zusätzliche Normalisierungsregeln zu unterstützen.

**Behobene Probleme in Version 2.4.10**

Die folgenden Probleme wurden in der Browser TVSDK-Version 2.4.10 behoben:

**Kernwiedergabefunktionen:**

・ **21060**: Ungültiger Codec-Fehler, der bei HLS-Streams mit Unterbrechungen ausgegeben wird und die ISO-BMFF-Felder bis zum Ende des Streams ausgeführt werden.

・ **21045**: Automatische Wiedergabe auf iOS funktioniert nicht, nachdem die erste Videowiedergabe in einer Wiedergabeliste abgeschlossen ist.

・ **20975**: Die Framerate wird vom QoS-Provider im Chrome-Browser als NaN zurückgegeben.

・ **20823**: Nicht unterstützter Codec-Fehler, der beim Erkennen von Segmenten ohne Daten ausgegeben wird.

・ **20769**: Das SDK beginnt jetzt mit der aktuellen Bitrate bei der Suche, anstatt sofort basierend auf der ABR-Richtlinie zu wechseln.

・ **2003**: Im Hochformat in IE11 (Windows 8.1) wird der Videobildschirm klein. Inhaltsschutzfunktion:

・ **19316**: Segmente, die bei HLS AES-128-Streams mit Fehler bei der Entschlüsselung auftreten, werden übersprungen.

**In Version 2.4.9 behobene Probleme**

Die folgenden Probleme wurden in der Browser TVSDK-Version 2.4.9 behoben:

**Kernwiedergabefunktionen:**

・ **13407**: DASH-Streams können anhalten, wenn Firefox während der Wiedergabe das Senden des Ereignisses &quot;ontimeupdate&quot;beendet.

・ **16380**: Während der Wiedergabe des Audiovideoinhalts von Segmenten mit nicht übereinstimmenden Startzeiten über MSE wird der Fehler bei der Audiosynchronisierung zwischen den Darstellungen auf ABR-Switches akkumuliert, was letztendlich zu Fehler führt (Chromium-Problem #663686).

・ **17985**: Beim Abspielen eines bestimmten ISO-BMFF-Streams im Firefox-Browser wird die Wiedergabe unterbrochen (Firefox-Problem #1342913). Dieses Problem wurde seit Firefox v53 behoben.

・ **1941**: Uncaught (in promise) ReferenceError: width is not defined.

・ **1897, 19299**: Problem mit Videoflackern bei Segmentgrenzen. Dies geschah, da das SDK den Zeitversatz Komposition des letzten Beispiels nicht korrekt berechnet hat.

・ **19780**: Die Wiedergabe wird für HLS-Inhalte und HLS-Anzeigen in Firefox v53 nicht gestartet (Firefox-Problem #354653).

・ **20046**: Die Programmdatumszeit wird als Schlüssel statt als Wert empfangen, wenn sie als zeitgesteuertes Metadatenobjekt empfangen wird.

・ **20047**: useDefaultResizeHandler gibt einen Fehler mit Flash-Fallback aus.

・ **2017**: Flash Fallback funktioniert nicht mit Flash Player v25.0.0.171.

・ **20293**: Firefox stoppt die Pufferung von Daten für bestimmte HLS-Streams, die zum Anhalten führen.

・ **20626**: Der Player gibt in Chrome einen Fehler bei der Mediendekodierung aus, da Videobeispiele mit Nulllaufzeit falsch verarbeitet werden.

・ **20078**: Die Wiedergabe wird bei dem Browser-Fehler &quot;QuotaExceeded&quot;angehalten.

・ **18639**: In HLS Live Stream 608 CC wird Text manchmal als falsch geschrieben angezeigt.

・ **2028**: Der Parameter &quot;Größe der ClosedCaptions&quot;ändert die Schriftgröße nicht.

・ **2013**: Geschlossene Untertitelfelder überschneiden sich, sodass sie nicht mehr lesbar sind.

**Core Ad Insertion (CSAI)-Funktionen:**

・ **20043**: Fehlende Ad-Impression- und Anzeigen-Tracking-Aufrufe mit mehreren Anzeigen und Umleitungen von Drittanbietern.

・ **2004**: Bei Verwendung der kreativen Neuverpackung müssen alle Anzeigen in der Werbeunterbrechung erfolgreich neu verpackt werden, da die Werbeunterbrechung sonst vollständig verworfen wird.

・ **2097**: Die Anzeigenwiedergabe wird übersprungen und der Hauptinhalt wird sofort fortgesetzt, anstatt auf eine Zeitüberschreitung von 20 Sekunden zu warten, wenn das Anzeigenmanifest nicht verfügbar ist.

**Behobene Probleme in Version 2.4.8 Update (Build 6002)**

Die folgenden Probleme wurden in der Browser TVSDK-Version 2.4.8 (Build 6002) behoben:

・ **14126:** Die Wiedergabe kann in Firefox (Problem #1316024) aufgrund einer internen Lücke im MSE-Quellpuffer anhalten. Suchen Sie nach , um die Wiedergabe fortzusetzen.

・ **19608** Fehlerbehebung zur Berücksichtigung des Zeitversatzwerts aus der Auditude VMAP-Antwort.

・ **19635** Behebt den Videostil in Internet Explorer 11 unter Windows 10.

・ **19761** Fehlerbehebungen für ABR-Probleme mit HLS.

・ **19780** Fehlerbehebung der Anzeigenwiedergabe mit HLS-Inhalt, der in Mozilla Firefox v53 fehlerhaft war.

・ **1987 und 19744:** Die Probleme beheben die Inkonsistenz bei der Auswahl der Bitrate nach einem Suchvorgang. Jetzt ist die Auswahl der Bitrate bei der Suche der niedrigere Wert der aktuellen Bitrate und die Bitrate beim Start.

・ **1981:** Die Wiedergabe hängt und die Pufferüberlagerung wird unbegrenzt lange angezeigt, nachdem die Suche 3-4-mal durchgeführt wurde.

・ **1984:** Bestätigen Sie die Einhaltung der Anforderungen an Chrome 59 Beta Verified Media Path (VMP). bTVSDK konnte Widevine DRM-Inhalte mit Chrome 59 Beta wiedergeben.

・ **19916** Die DRM-Wiedergabe auf UI-Framework war fehlerhaft. Jetzt ruft sie acquisitionLicense auf, selbst wenn in den Metadaten keine Richtlinie enthalten ist.

**Behobene Probleme in Version 2.4.8**

Die folgenden Probleme wurden in der Browser TVSDK-Version 2.4.8 behoben:

・ **10075**: Bei der Suche vor der Timeline wurde das Ereignis &quot;Wiedergabe abgeschlossen&quot;in Firefox und Chrome nicht empfangen und das Suchereignis wurde in Firefox nicht empfangen.

・ **15775**: Ereignis &quot;Abschluss abspielen&quot;wird in Windows 8.1 Internet Explorer nicht empfangen.

・ **17306**: Bei SSAI-Streams wird die Wiedergabe unterstützt. Das Tracking von zusammengefügten Anzeigen wird nicht unterstützt.

・ **19142**: Manchmal führt die Wiederholung dazu, dass der Videoplayer für immer im Pufferstatus bleibt.

・ **19218**: Anzeigenmarkierungen sind nicht über das UI-Framework verfügbar.

・ **19219**: Die Wiedergabe von Anzeigen funktioniert nur nicht über das UI-Framework.

・ **1922**: Der AES-128-Schlüssel wird einmal für eine Wiedergabeliste angefordert und nachfolgende Anforderungen werden aus dem Cache bereitgestellt. Zuvor wurde sie für jedes Segment angefordert.

・ **19597**: &quot;Uncaught TypeError: Cannot read property &#39;log&#39; of undefined&quot; wurde bei Chrome-Kanarienbausteinen angezeigt.

・ **19605**: adRequestDomain war im Flash-Fallback-Modus nicht verfügbar.

・ **19608**: Für HLS-Live-Streams wurden keine VMAP-Anzeigen eingefügt. Das SDK berücksichtigt jetzt die Cue-Point-Markierungen und verlässt sich in VMAP-Antworten nicht auf Zeitversatzwerte.

・ **19637**: Die Wiedergabe von Anzeigen führt nur zu einem Skriptfehler am Ende der Anzeige.

・ **19732**: CRS-Playlist-Anforderungen schlugen mit 404-Fehler fehl. Die Anfragen 1401 und 1403 von Browser TVSDK werden jetzt aktualisiert, um dies zu übernehmen.

・ **19762**: acquisitionLicense , die früher vor setAuthenticationToken aufgerufen wurde und aufgrund derer unabhängig von der Token-Gültigkeit eine gültige Lizenz zurückgegeben wurde. Dieses Problem wurde jetzt behoben und acquisitionLicense wird nur nach der setAuthenticationToken-Antwort aufgerufen.

**Behobene Probleme in Version 2.4.7**

Die folgenden Probleme wurden in Version 2.4.7 behoben:

・ **8397**: Durch Adobe Media Server generierte HLS-Live-Streams werden möglicherweise nicht wiedergegeben, wenn die Segmente nicht mit einem Schlüssel-Frame beginnen.

・ **13606**: Mehrere suchbezogene Probleme wurden für HLS-Stream im Chrome-Browser behoben.

・ **14807**: Wenn im Chrome-Browser unmittelbar nach play() die Suche oder Pause ausgelöst wird, kann die Wiedergabe mit dem Fehler DOMException beendet werden: Die play() -Anfrage wurde durch einen -Aufruf unterbrochen.. (Chromium-Problem# 593273).

・ **19085**: MediaPlayer-Parameter wie Lautstärke, abrControlParameters und ccStyle werden beim Zurücksetzen des Players nicht auf &quot;Standard&quot;festgelegt.

**In Version 2.4.6 behobene Probleme**

Das folgende Problem wurde in Version 2.4.6 behoben:

・ **18093**: TimedMetadata für das Tag neben dem abonnierten Tag wird zurückgegeben, wenn Sie Flash Player Version 24 im Flash-Fallback-Modus verwenden.

**In Version 2.4.4 behobene Probleme**

Die folgenden Probleme wurden in Version 2.4.4 behoben:

・ **8711**: Bei MSE bleiben Beschriftungen vom Typ 608/708 standardmäßig ausgerichtet.

・ **13934**: ABR-Einstellungen für Anzeigen können nicht bei der Wiedergabe mit HLS Live Streams verwendet werden.

・ **14079**: Die Langlebigkeit für HLS-Live-Streams mit geringem DVR-Fenster kann fehlschlagen, da die Wiedergabe aufgrund von Netzwerklatenz-Problemen möglicherweise fehlschlägt. Klicken Sie auf den Live Point, um die Wiedergabe fortzusetzen.

・ **15037**: Die mit dem Player-UI-Framework ausgelieferten Beispiele funktionieren nicht in Microsoft Internet Explorer 10 unter Windows 7.

・ **15913**: Bei HLS-VOD-Streams wird in Chrome der Stream nicht abgespielt, wenn die Manifestantwort 304 nicht geändert wurde. Dieses Problem wurde seit Chrome v55 behoben (Chromium-Problem 633696).

・ **16103**: Unter Android-Chrome kann die Wiedergabe unter Bedingungen mit geringer Bandbreite mit dem Uncaught TypeError: Cannot read property &#39;programDateTime&#39; of undefined error anhalten.

・ **16265**: Bei HLS-VOD- und Live-Streams funktioniert die Suche über Unterbrechungen hinweg nicht.

・ **16709**: Das Fortsetzen des HLS-Live-Streams mit PDT und Diskontinuitätsmarkierung kann dazu führen, dass der Player bei der Pufferung hängen bleibt.

## Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

Die Einschränkungen und bekannten Probleme in Browser TVSDK sind unten aufgeführt.

**Tabelle 16: Kernfunktionen der Wiedergabe**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhaltstyp</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML 5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML 5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Allgemeine Wiedergabe (Wiedergabe, Pause, Suche)</td> 
   <td><p>・ Andere Medienformate als HLS werden nicht unterstützt.</p> <p>8799: Flash Fallback kümmert sich nicht um gemischte Inhalte. Daher muss sichergestellt werden, dass Inhalte, Anzeigen und andere URLs nicht zu gemischten Inhalten führen (sichere und unsichere Inhalte zusammen).</p> <p>・ 19271: Die Wiedergabe mehrerer Ansichten über das UI-Framework wird im Flash-Fallback-Modus nicht unterstützt.</p> <p>・ Flash Fallback funktioniert nicht in Microsoft Internet Explorer 8 und 9 unter Windows 7, da diese Versionen vom SDK nicht unterstützt werden.</p> <p>・ 20262: Flash Fallback fügt benutzerdefinierte Parameter zur Targeting-Informationsliste hinzu. Auch die Prioritätsreihenfolge von benutzerdefinierten Parametern unterscheidet sich bei Flash und MSE.</p> <p>・ 20653:Browser TVSDK Flash Fallback funktioniert nicht auf Win10 mit Creators Update.</p> <p>・ Flash Fallback funktioniert mit Flash Player Version 23 und höher.</p> <p>・ 20087 - Chrome 59 Beta mit</p> <p>Flash 25.0.0.171</p> <p>Beta (Standard): Die HLS-Wiedergabe funktioniert im Flash-Fallback-Modus nicht. Es funktioniert gut auf Kanaren.</p> </td> 
   <td><p>・ 12563: Dash-Streams mit Audio-Codec mp4a.40.02 werden aufgrund der nicht unterstützten Audio-Codec-Zeichenfolge in MPD nicht in Firefox wiedergegeben. Audio Codec mp4a.40.2 wird unterstützt.</p> <p>15029: Beim Wechseln zwischen Videos in der MultiView-Benutzeroberfläche in UI-Framework wird die Wiedergabe/Pause-Schaltfläche nicht entsprechend aktualisiert.</p> <p>・ 16034:Unter Windows 8.1 IE führt der Aufruf von reset() zu einem Fehler vom Typ "Unbekannter MIME". Bitte laden Sie das Medium neu, um die Wiedergabe fortzusetzen.</p> <p>・ 18235: Bestimmte Suchprobleme werden bei DASH vod-Streams mit Ads beobachtet.</p> <p>・ 18727: Fehler-API wird für MSE nicht unterstützt</p> <p>18750: Statusänderungsereignisse sind in einigen Fällen sowohl für das SDK- als auch für das UI-Framework nicht in der richtigen Reihenfolge. In UI Framework fehlen möglicherweise IDLE- und Initializing StatusChange-Ereignisse für die Ereignis-Listener, die hinzugefügt werden, nachdem die Ressource geladen wurde.</p> <p>・ 18889: Wenn der MediaPlayer den FEHLER aufweist, wird das Ansichtsobjekt nicht zurückgegeben.</p> <p>・ 19039: Wenn AdobePSDK. MediaPlayer. searchToLocal() mit einem Wert verwendet wird, der größer als EOF ist, beginnt die Wiedergabe bei MSE mit dem Anfang.</p> <p>・ 19049: Kein Fehlerstatus für Flash Player in Chrome, IE und Firefox gemeldet, wenn das Video während der Wiedergabe blockiert wird.</p> <p>・ 17205: Die Videowiedergabe hält einige Stunden lang bei der Wiedergabe des unmutierten Streams an, während die Audiowiedergabe fortgesetzt wird (Chromium-Problem# 664033).</p> <p>・ 12308: Für DASH-Streams mit angegebenem "zusammensetzung_ time_offset"kann auf den Chrome-Browser timeStampOffset angewendet werden, was zu einer negativen Dekotzeit und somit zu MEDIA_ERR_ SRC_NOT_ SUPPORTED-Fehler führt (Chromium-Problem #398141).</p> <p>・ 14126: Die Wiedergabe kann bei Firefox anhalten (Problem# 1316024), da die interne Lücke im MSE-Quellpuffer besteht. Versuchen Sie es mit der Suche, um die Wiedergabe fortzusetzen.</p> <p>・ 19115: MS Edge und IE 11 (Win 8.1 und 10) setzen den Origin bei der CORS-Umleitung nicht auf null und scheitern dennoch, da der Header nicht null ist und zu einem Wiedergabefehler führt.</p> <p>・ 19861:Problem mit dem Anlagenverhalten beim Quellpuffer für bereits abgespielte Medien. Chrome lehnt das angehängte Fragment einschließlich "moov"ab, was zu einem nachfolgenden Dekodierungsfehler führt. (Chromium-Problem #735335)</p> <p>19921: Wiedergabe wird für bestimmte HLS-Inhalte gestoppt, obwohl sie erfolgreich gepuffert wurde (Chromium-Problem #713540)</p> <p>・ 20444:Wenn Sie versuchen, den gepufferten Bereich in IE und Edge zu beenden, wird die Wiedergabe möglicherweise angehalten.</p> <p>・ 20511: Gelegentlich kann eine Zurückweisung der Suche bei HLS-Streams mit oder ohne Anzeigen beobachtet werden.</p> <p>・ 20743: Unter Windows 10 Chrome wird der HLS-Live-Stream einige Sekunden vor der MP4-Vorab-Roll-Wiedergabe wiedergegeben.</p> <p>・ 21043: Die Dimension "Video"ist beim ersten Laden möglicherweise nicht korrekt, da Metadaten fehlen.</p> <p>・ 21115: Eine Android-Benutzergeste ist erforderlich, um die Wiedergabe zu starten, wenn eine Pre-Roll-Anzeige für Videos in einer Wiedergabeliste verfügbar ist.</p> <p>・ HLS Live unterstützt das Rollover von Zeitstempeln nicht.</p> <p>・ AAC-SSR-Audio wird nicht unterstützt.</p> <p>Audio-Codecs AC3 und Enhanced AC3 werden nicht unterstützt.</p> <p>・ Bei Streams mit Zeitstempelunterbrechung, jedoch ohne Diskontinuitätsmarkierungen</p> <p>・ Die Wiedergabe kann aufgrund von Sprüngen zu Fehlern und falschen Suchen führen.</p> <p>・ Die Inhaltsdauer und die Wiedergabedauer stimmen möglicherweise nicht überein.</p> <p>・ Diskontinuitäten zwischen Darstellungen und Ausgabedarstellungen sollten mit anderen Ansichten übereinstimmen, können zu Synchronisations- und Unterbrechungsproblemen führen.</p> <p>・ Untertitel und WebVTT werden möglicherweise nicht nah am Ende des Streams angezeigt.</p> <p>・ Änderungen am Audio-Codec werden nicht über Zeitstempelsprünge hinweg unterstützt.</p> <p>・ Das Einfügen von Anzeigen wird nicht unterstützt.</p> <p>・ Der schnelle Forward-Trick-Modus kann zu einer Wiedergabeschleife unter Win 8.1 IE 11 führen (MS-Problem #1246268).</p> <p>DASH:</p> <p>・ Live-Streams: Live-Profile mit dynamischem Typ werden unterstützt.</p> <p>・ Bei VoD-Streams wird ein Live-Profil mit statischem Typ unterstützt.</p> <p>Für VoD-Streams: Das On-Demand-Profil ist nicht für Anzeigen-Workflows zertifiziert.</p> </td> 
   <td><p>・ DASH Live- und DASH-Video on Demand-Streams werden nicht unterstützt.</p> <p>・ PIP(Picture im Picture)-Videowiedergabe wird auf iOS im Vollbildmodus nicht unterstützt.</p> <p>In der Safari-Erweiterung (Video-Tag) funktioniert ein geringeres Manifest, ohne dass der richtige Content-Typ-Header vorhanden ist.</p> </td> 
   <td><p>・ Die applicationID in der Absender-App muss mit der bei der Registrierung der URL des Empfängers als benutzerdefinierte Receiver-App generierten übereinstimmen.</p> <p>・ Referenz-Player ist für DASH-Workflows zertifiziert. UI-Framework ist nicht zertifiziert.</p> <p>Eine Liste der unterstützten Medien-Codecs finden Sie unter <a href="https://developers.google.com/cast/docs/media"><em>here</em></a>.</p> </td> 
  </tr> 
  <tr> 
   <td>FER VOD</td> 
   <td>Allgemeine Wiedergabe (Wiedergabe, Pause, Suche)</td> 
   <td> </td> 
   <td>18098: Beim HLS LBA-FER-Stream treten bestimmte Suchprobleme auf.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Adaptive Bitrate</td> 
   <td><p>・ 20079: Neuschreiben von Puffern bei Suche im gepufferten Bereich.</p> <p>2008: Flash ABR-Verhalten ist konsistent mit MSE.</p> </td> 
   <td><p>・ Nur Audio-Fallback-Variante in einem ABR-Stream wird aufgrund von Pufferbeschränkungen ignoriert.</p> <p>・ 12289: ABR-Kontrollparameter gelten nicht für Audio bei unmuxed HLS/DASH-Streams.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>608/708 Untertitel</td> 
   <td> </td> 
   <td><p>・ 7810: Unter Android 4.4.4 scheint Chrome keine Unterstützung für grundlegende CSS-Schriftfamilien zu haben, die vom Player verwendet werden. Daher funktioniert die Funktion zum Ändern des Schriftstils nicht.</p> <p>・ Die CC-Kanäle können bei 608 Untertiteln nicht geändert werden.</p> <p>・ Erweiterte Stilfunktionen werden für 608 Beschriftungen nicht unterstützt.</p> <p>Eingebettete Untertitel (608/708), die über das Tag "Ein-/Ausgabehilfe"signalisiert wurden, werden unterstützt.</p> </td> 
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
   <td>21056: Bei Flash-Fallback tritt kein Failover für Live-Stream auf, wenn der primäre Stream während der Wiedergabe einen 404-Fehler zurückgibt.</td> 
   <td>Das Manifest-Failover gilt nur für Inhalte und nicht für Anzeigen.</td> 
   <td>Fehlendes Wiedergabelisten-Failover funktioniert in Safari nur für HTTP-Fehlercode 404.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Erweitertes Failover</td> 
   <td> </td> 
   <td><p>・ Segment-Failover unterstützt nicht das Überspringen von nicht verfügbaren Segmenten und das Fortsetzen der Wiedergabe.</p> <p>20533: Fehlende Segmente in einer Wiedergabeliste sollten als Diskontinuität behandelt werden und die Wiedergabe sollte ab dem nächsten verfügbaren Segment fortgesetzt werden.</p> <p>21267: Stream-Switching aufgrund eines Fehlschlagens kann zum Herunterladen älterer Segmente führen.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>QoS- und Player-Benachrichtigungen</td> 
   <td>21129: Die Framerate ist bei Flash Fallback nicht verfügbar.</td> 
   <td><p>• 11170:</p> <p>Timed_Event ist nicht für Browser TVSDK mit MSE verfügbar, im Gegensatz zu Browser TVSDK mit Flash Fallback.</p> <p>21129: Die Framerate wird für Live-Streams nicht berechnet.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Unterstützung für Cookie-Kopfzeilen</td> 
   <td> </td> 
   <td> </td> 
   <td><p>Die Header mit Anmeldedaten und Cookies werden in Safari nicht unterstützt.</p> <p>21051: Um Cookies in Safari zuzulassen, aktivieren Sie die Einstellung "Cookies und Website-Daten"unter Voreinstellungen &gt; Datenschutz.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Benutzerdefinierte Tags</td> 
   <td>14763: Benutzerdefinierte Tags, die nicht mit # beginnen, sollten nicht unterstützt werden. Derzeit wird das TimedMetadata-Objekt während des Flash Fallback für solche Tags erstellt und gemeldet.</td> 
   <td>Streams mit inband-benutzerdefinierten Tags sind nicht zertifiziert.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Spätes Binding Audio</td> 
   <td> </td> 
   <td><p>・ Das Einfügen von Anzeigen wird nicht von HLS Live LBA-Streams unterstützt.</p> <p>・ 17273: HLS VOD LBA-Streams wechseln im Falle von Failover zur Standardausgabe und können nicht zur letzten Auswahl zurückgeschaltet werden.</p> <p>・ 20251: HLS Live LBA-Stream kann bei der Suche anhalten.</p> <p>・ 20497: Player bleibt im Pufferstatus, wenn bei HLS LBA-unmuxed Streams in der Nähe des Streams Audio- oder Video-Frames fehlen.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>302 Umleitung</td> 
   <td> </td> 
   <td><p>15787: 302</p> <p>Die Umleitungsoptimierung wird in Windows Edge- und IE-Browsern nicht unterstützt, da diese die Eigenschaft responseURL im XMLHttpRequest-Objekt nicht unterstützen.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 17: Erweiterte Wiedergabefunktionen**

<table> 
 <tbody> 
  <tr> 
   <td>Content-Typ</td> 
   <td>Funktion</td> 
   <td>Flash</td> 
   <td><strong>HTML 5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML 5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Wiedergabe mit Versatz</td> 
   <td><p>Der Start der Wiedergabe mit einem bestimmten Offset-Wert wird nicht für MP4-Inhalte unterstützt.</p> </td> 
   <td>20492: Mid-Roll-Anzeigen vor dem Offset werden wiedergegeben, bevor der Inhalt aus dem Offset-Wert fortgesetzt wird.</td> 
   <td>Die Wiedergabe mit der Offset-Funktion wird in iOS nicht unterstützt.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Trick Play</td> 
   <td>Smooth Trickplay funktioniert nicht für Streams ohne iFrame-Ausgabeformate.</td> 
   <td><p>・ Trick Play-Anpassungen werden in Firefox und Internet Explorer nicht unterstützt und daher ist der Reverse-Trick-Modus in diesen Browsern nicht verfügbar.</p> <p>・ Trickplay ist nicht verfügbar, wenn Inhalte zusammen mit Anzeigen wiedergegeben werden.</p> <p>・ 10435: Während der DASH-Wiedergabe friert das Video bei der Vorwärts-Trick-Wiedergabe in Internet Explorer ein (Win 8.1)</p> <p>intermittierend. Dies geschieht, da wir die Eigenschaft "playRate"der Videoelemente ohne Anpassung der Trick-Wiedergabe verwenden.</p> <p>14182: Manchmal wird das Suchereignis während der Rückspaltung im Chrome-Browser möglicherweise nicht empfangen, weshalb der Trick-Modus nicht funktioniert.</p> <p>・ 14942: Die Wiedergabegeschwindigkeit kann in Chrome für Android festgelegt werden, auch wenn es sich um nicht-trick-Wiedergabe-Streams handelt. Die Einstellung wird jedoch nicht angewendet und die Wiedergabe wird mit normaler Geschwindigkeit fortgesetzt.</p> <p>・ 17308: Die Suche funktioniert nicht im Trickplay-Modus.</p> <p>・ 17309: Im Chrome-Browser kann der Reverse-Trick-Modus nicht länger als 2 Sekunden aufrechterhalten werden.</p> <p>19272: Die Trick-Wiedergabe wird im Fall von DASH-Streams möglicherweise nicht von der Pufferung im Windows 10 Edge-Browser wiederhergestellt.</p> </td> 
   <td>Der Rückspultrickmodus wird nicht unterstützt.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>ID3-Analyse</td> 
   <td>20346: Auch das Textkodierungsbyte von ID3-Frames sollte vom SDK zurückgegeben werden.</td> 
   <td><p>ID3-Tags, die in Audio Data Transport Streams (ADTS) verfügbar sind, werden vom SDK ignoriert.</p> <p>・ 12378: Zeitgesteuerte ID3-Metadaten werden zu unterschiedlichen Zeitpunkten auf Flash und Browser mit MSE-Unterstützung analysiert. Daher unterscheidet sich auch das Anzeigeverhalten auf der Referenzplayer-Timeline.</p> <p>・ 19247: ID3-Parsing wird nicht vom UI-Framework unterstützt.</p> </td> 
   <td><p>・ 20323: PRIV ID3-Tag, mit dem der Zeitstempel der ersten Stichprobe eines Segments signalisiert wird, wird von Safari nicht analysiert (Safari-Problem #32422733)</p> <p>・ 20350: Auf bestimmten Geräten (einschließlich MAC OS X 10.1, iPad10) bietet Safari kein Cue-Change-Ereignis, wenn es sich im Trick-Modus befindet, weshalb ID3-Frames nicht empfangen werden. (Safari-Problem #32450526)</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Unterstützung von Diskontinuitätsmarken</td> 
   <td> </td> 
   <td><p>・ Die clientseitige Anzeige wird bei HLS-Streams mit Unterbrechungen nicht unterstützt.</p> <p>・ Audio-Codec-Änderungen sind nicht über Unterbrechungen im HLS-Stream hinweg zulässig.</p> <p>・ Der Audio Track Switch wird für HLS-Streams mit Diskontinuitätsmarkierungen nicht unterstützt</p> </td> 
   <td>Die Sequenznummer der Diskontinuität ist eine Voraussetzung für HLS-Streams mit Diskontinuität, um sie in Safari wiedergeben zu können.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 18: Inhaltsschutzfunktionen**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Content-Typ</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML 5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML 5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>AES-128</td> 
   <td> </td> 
   <td>Der Byte-Bereich wird mit verschlüsseltem AES-128-Inhalt nicht unterstützt.</td> 
   <td>12324: Verschlüsselte HLS AES-128-Streams können nicht in Safari wiedergegeben werden, wenn das IV-Tag nicht angegeben ist.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>DRM</td> 
   <td> </td> 
   <td><p>・ 12660: HTML5-Player gibt Internen Server-Fehler für abgelaufenen PlayReady-verschlüsselten Dash-Inhalt aus.</p> <p>・ 16720: DASH DRM-verschlüsselter Inhalt funktioniert nicht, wenn das Attribut start im Punkt-Tag fehlt.</p> <p>・ 18589: Die Wiedergabe wird für DRM geschützte Dash VoD Multiperiod-Streams mit Xlink nicht unterstützt.</p> <p>・ 18653: Wiedergabe des umfangreichen MultiPeriod-Inhalts mit mehreren Schlüsseln, hält beim ersten Punkt an und kann nicht zum nächsten Zeitraum wechseln.</p> <p>・ 18656: Play-ready MultiPeriod Stream, mit verschiedenen Schlüsseln verschlüsselt, wird nicht wiedergegeben.</p> <p>Playready 2.0 für Dash ist nicht zertifiziert.</p> <p> </p> <p> </p> </td> 
   <td>12602: HLS Fairplay DRM-Metadaten werden wiederholt vom HTML5-Player in Safari aktualisiert</td> 
   <td><p>DASH Widevine DRM Inhalt, der über Bento4 verpackt wurde, kann wiedergegeben werden. Inhalte, die über Offline Packager und Shaka Packager gepackt wurden, werden nicht abgespielt. DASH PlayReady DRM wird nicht unterstützt.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 19: Kernfunktionen der Ad Insertion (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Content-Typ</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML 5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML 5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Pre/Mid/Post</td> 
   <td> </td> 
   <td><p>・ Preroll-Anzeigen mit HLS-Live-Inhalten werden im Dualplayer-Modus abgespielt.</p> <p>・ DASH-Anzeigen mit HLS-Inhalten und HLS-Anzeigen mit DASH-Inhalten werden nicht unterstützt.</p> <p>・ 19002: In HTML5 Player mit MSE adBreak. InsertionType gibt keinen korrekten Wert zurück, um den korrekten Einfügetyp darzustellen, d. h. den eingefügten Client oder den eingefügten Server.</p> <p>7794: Auf Mobilgeräten (iOS, Android mit Chrome 33 oder nativem Browser), auf denen die Standardsteuerleiste im Vollbildmodus angezeigt wird, sind die Schaltflächen "Suchleiste"und "Schnellvorwärts"verfügbar, wenn Anzeigen abgespielt werden.</p> <p>・ 11048: Der Wechsel von Anzeigen zu HLS Live-Inhalten erfolgt nicht reibungslos bei Media Source-Erweiterungen.</p> <p>・ 16083: Unter Android 4.4 Chrome v52 kann HLS und HLS-Inhalte manchmal zu Pipeline-Dekodierungsfehlern führen, nachdem die Wiedergabe angehalten wurde.</p> <p>・ 16097: Fehler, die während einer Werbeunterbrechung aufgetreten sind, werden nicht verarbeitet. Dies kann dazu führen, dass der Hauptstrom die Wiedergabe stoppt.</p> <p>・ 18095: MP4-Anzeigen werden von HLS-Live-Inhalten nicht unterstützt.</p> <p>19120: Mehrere Suchvorgänge für HLS-Anzeigen mit HLS-Inhalten können dazu führen, dass der Stream die Wiedergabe stoppt.</p> <p>・ 19131: Beim Wechsel von Pre-roll-Werbeunterbrechungen zu Inhalten kann eine Pufferüberlagerung auftreten.</p> <p>・ 20296: Bei HLS Live Streams kann die Suche im DVR-Fenster, gefolgt von der Suche nach aufgelösten Mid-Roll-Laufwerken, zu einer Wiedergabe-Unterbrechung führen.</p> <p>・ 20298:HLS Live Streams mit Mid-Roll stall den Moment, in dem die erste Mid-Roll-Anzeige das DVR-Fenster verlässt.</p> <p>・ 20317: HLS-Live-Streams können beim Wechsel zur nächsten Anzeige oder von Anzeige zu Inhalt anhalten, falls eine Werbeunterbrechung mehr als eine Anzeige enthält.</p> 
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
   <td>Das SDK berücksichtigt kein Sequenzattribut in der VMAP-Antwort für VAST adSource.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>20779: Das SDK berücksichtigt das Sequenzattribut nicht in der VMAP-Antwort für VAST adSource.</td> 
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
   <td>Kreative Neuverpackung</td> 
   <td> </td> 
   <td>21464: Die Anzeigenantwort wird vollständig verworfen, wenn die kreative Neuverpackung für eine der Anzeigen in der Werbeunterbrechung fehlschlägt.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 20: Erweiterte Ad Insertion-Funktionen (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Content-Typ</strong></td> 
   <td><strong>Funktion</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML 5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML 5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (nur DASH-Wiedergabe)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Nur Anzeige</td> 
   <td> </td> 
   <td>2005: Die Eigenschaft der Player-Technologie ist nicht relevant, da sie auf dem Hauptinhalt basiert, der im Falle der Wiedergabe "Nur Anzeige"leer ist</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Benutzerspezifische Anzeigenrichtlinie</td> 
   <td> </td> 
   <td><p>・ Werbeverhalten werden von MP4-Anzeigen und MP4-Inhalten nicht unterstützt.</p> <p>・ 13973: Benutzerdefiniertes Anzeigenverhalten - Die SKIP-Richtlinie löst bei Verwendung mit MSE kein complete-Ereignis aus.</p> <p>・ 14939: Benutzerdefinierte Anzeigenverhaltensrichtlinien zum Überspringen und Überspringen von Werbeunterbrechungen funktionieren nicht für DASH-Inhalte.</p> <p>・ 17131: Der erste Frame der Anzeige ist sichtbar und der Inhalt wird dann im Fall einer SKIP-Werbeunterbrechungsrichtlinie fortgesetzt.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Unternehmensanzeigen/ Banneranzeigen/ klickbare Anzeigen</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>Banneranzeigen sind bei Verwendung des Referenz-Players nicht sichtbar.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>VPAID 2.0</td> 
   <td> </td> 
   <td><p>・ Das Anzeigenverhalten wird bei VPAID-Anzeigen nicht unterstützt.</p> <p>・ 15032: VPAID-Anzeigen in Kombination mit MP4- oder HLS-Anzeigen in einer Werbeunterbrechung werden nicht unterstützt.</p> <p>・ 19001: In Android und iOS, wenn VPAID-Anzeige mit MP4 abgespielt wird, da doppelte Audiospuren hörbar sind, einer der Hauptinhalte und einer der Anzeigen.</p> <p>・ 20762: VPAID-Anzeigen werden von Picture-in-Picture (PIP) nicht unterstützt.</p> <p>・ 21172: Das Abspielereignis wird nicht für HLS VOD-Inhalte mit VPAID-Anzeigen empfangen.</p> <p>・ 21173: onAdBreakCompleteEvent wird nicht für HLS-VOD-Inhalte und Post-Roll-VPAID-Anzeigen empfangen.</p> </td> 
   <td>Der Player wechselt zwischen dem normalen Modus und dem Vollbildmodus beim Wechsel zwischen VPAID-Anzeige und Hauptinhalt.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 21: Integrationen**

| **Content-Typ** | **Funktion** | **Flash** | **HTML 5 in Firefox, IE, Chrome, Android Chrome** | **HTML 5 in Safari, iOS Safari** | **Chromecast (nur DASH-Wiedergabe)** |
|---|---|---|---|---|---|
| VOD + Live | Adobe Analytics VHL-Integration |  | 1904: Das Video Analytics-Tracking ist nicht über das UI Configurator Tool verfügbar. |  |  |

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation unter [Adobe Primetime - Lernen und Support](https://experienceleague.adobe.com/docs/primetime.html) Seite.
