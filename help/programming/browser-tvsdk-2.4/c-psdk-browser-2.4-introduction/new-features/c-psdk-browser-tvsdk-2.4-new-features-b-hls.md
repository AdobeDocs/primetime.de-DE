---
description: Browser TVSDK unterstützt eine Reihe von HLS-Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.
title: Unterstützte HLS-Funktionen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# Unterstützte HLS-Funktionen {#supported-hls-features}

Browser TVSDK unterstützt eine Reihe von HLS-Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.

* [HLS-Core-Wiedergabe](#hls-core-playback)
* [HLS Advanced-Wiedergabefunktionen](#hls-advanced-playback)
* [HLS-Inhaltsschutzfunktionen](#hls-content-protection)
* [HLS Core-Anzeigeneinfüge-Funktionen](#hls-core-ad-insertion)
* [HLS Erweiterte Anzeigeneinfüge-Funktionen](#hls-advanced-ad-insertion)
* [HLS-Integrationen](#hls-integrations)

>[!TIP]
>
>In den Funktionsmatrix-Tabellen unten: ![unterstütztes Symbol](assets/supported15.png) bedeutet, dass die Funktion in der aktuellen Version unterstützt wird.

>[!TIP]
>
>In der Safari-Spalte bedeutet &quot;Plattformbegrenzung&quot;, dass der Anwendungsfall nicht unterstützt wird, da diese Plattform keine Unterstützung dafür zulässt. Verwenden Sie im Falle eines Einfügens SSAI. Wenn Sie Wiedergabeschränkungen beachten müssen, erzwingen Sie das Fallback in Safari zum Flash, bis die Plattform den Anwendungsfall für das Einfügen von Anzeigen unterstützt.

<!--<a id="section_9FB9193D5763448CB228B96164661738"></a>-->

Die folgenden Funktionen werden unterstützt:

<!-- 

Removed Nielsen row 
<table id="table_D9E2D82992554905A0A551CC71AFA189"> 
 <title>HLS integrations</title> 
 <tgroup cols="6"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col4" colwidth="*" /> 
  <colspec colnum="5" colname="col5" colwidth="*" /> 
  <colspec colnum="6" colname="col7" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" morerows="1" class="entry"> Category </th> 
    <th colname="col2" morerows="1" class="entry"> Content type </th> 
    <th colname="col3" morerows="1" class="entry"> Feature </th> 
    <th colname="col4" morerows="1" class="entry"> Flash </th> 
    <th namest="col5" nameend="col7" class="entry"> HTML5 </th> 
   </tr> 
   <tr> 
    <th colname="col5" class="entry"> FF, IE, Chrome, Android Chrome </th> 
    <th colname="col7" class="entry"> Safari, iOS Safari </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## HLS-Integrationen {#hls-integrations}

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Integrationen | VOD + Live | Adobe Analytics VHL-Integration | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |

## Erweiterte HLS-Anzeigeneinfüge-Funktionen (CSAI) {#hls-advanced-ad-insertion}

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD | Nur Anzeige | Nicht unterstützt | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Ad Insertion | VOD + Live | Targeting-Parameter | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Ad Insertion | VOD + Live | Benutzerdefinierte Anzeigenrichtlinie | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Ad Insertion | VOD + Live | Verzögertes Laden von Anzeigen | ![unterstütztes Symbol](assets/supported15.png) | Nicht unterstützt | Plattformbeschränkung |
| Ad Insertion | VOD | Begleitanzeigen, Banneranzeigen und anklickbare Anzeigen | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Ad Insertion | VOD | VPAID 2.0 | SWF | JavaScript | JavaScript |

## HLS-Kernfunktionen für Anzeigeneinfügungen (CSAI) {#hls-core-ad-insertion}

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD + Live | Pre-roll | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Ad Insertion | VOD + Live | Mid-roll | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Ad Insertion | VOD + Live | Post-Roll | Nur VOD | Nur VOD | Nur VOD |
| Ad Insertion | FER VOD | Auflösung und Verhalten von Anzeigen | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Ad Insertion | VOD + Live | Standard-Anzeigenrichtlinie | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Ad Insertion | VOD + Live | VAST 2.0/3.0 | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Ad Insertion | VOD + Live | VMAP 1.0 | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Ad Insertion | VOD + Live | CRS v3.1 | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |

## HLS-Inhaltsschutzfunktionen {#hls-content-protection}

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Inhaltsschutz | VOD + Live | AES-128 | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Inhaltsschutz | VOD + Live | Sample-AES | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Inhaltsschutz | VOD | DRM | Adobe-Zugriff | Nicht unterstützt | FairPlay |

## Erweiterte HLS-Wiedergabefunktionen {#hls-advanced-playback}

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Wiedergabe | VOD | Wiedergabe mit Versatz | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD | Nur-Audio-Wiedergabe | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD | Trick play | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD | Glätte Trick-Wiedergabe | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Wiedergabe | VOD + Live | ID3-Parsing | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Nicht unterstützt |
| Wiedergabe | VOD + Live | Unterstützung von Diskontinuitätsmarken | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD + Live | Tokenisierte Streams | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Wiedergabe | VOD + Live | Rechnungsstellung | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD + Live | Durchsuchen | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |

## HLS-Core-Wiedergabe {#hls-core-playback}

| Kategorie | Inhaltstyp | Funktion | Flash | HTML5: FF, IE, Chrome, Android Chrome | HTML 5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Wiedergabe | VOD + Live | Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | FER VOD | Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD + Live | Adaptive Bitrate | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD + Live | 608/708 Untertitel | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD + Live | WebVTT | ![unterstütztes Symbol](assets/supported15.png) | Nur VOD | Nur VOD |
| Wiedergabe | VOD + Live | Manifest-Failover | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) |
| Wiedergabe | VOD + Live | Erweitertes Failover | ![unterstütztes Symbol](assets/supported15.png) | Nur VOD | Plattformbeschränkung |
| Wiedergabe | VOD + Live | QoS- und Player-Benachrichtigungen | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Eingeschränkte QoS-Unterstützung |
| Wiedergabe | VOD + Live | Unterstützung für Cookie-Kopfzeilen | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Wiedergabe | VOD + Live | Einrichten von Puffersteuerparametern | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Wiedergabe | VOD + Live | Festlegen der Steuerelemente für die adaptive Bitrate | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Wiedergabe | VOD + Live | Benutzerdefinierte Tags | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Wiedergabe | VOD + Live | Spätbindende Audiowiedergabe | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
| Wiedergabe | VOD + Live | 302-Umleitung | ![unterstütztes Symbol](assets/supported15.png) | ![unterstütztes Symbol](assets/supported15.png) | Plattformbeschränkung |
