---
description: Browser TVSDK unterstützt eine Reihe von DASH-Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.
title: Unterstützte DASH-Funktionen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Unterstützte DASH-Funktionen{#supported-dash-features}

Browser TVSDK unterstützt eine Reihe von DASH-Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.

* [DASH-Core-Wiedergabefunktionen](#dash-core-playback)
* [DASH Advanced-Wiedergabefunktionen](#dash-advanced-playback)
* [DASH-Inhaltsschutzfunktionen](#dash-content-protection)
* [DASH-Core-Anzeigeneinfüge-Funktionen](#dash-core-ad-insertion)
* [DASH Erweiterte Anzeigeneinfüge-Funktionen](#dash-advanced-insertion-features)
* [DASH-Integrationen](#dash-integrations)

>[!TIP]
>
>In den Funktionsmatrix-Tabellen unten:  ![](assets/supported15.png)
>bedeutet, dass die Funktion in der aktuellen Version unterstützt wird.

Die folgenden Funktionen werden unterstützt:

<!-- 

<table id="table_lrb_p2g_xx"> 
 <title>DASH integrations</title> 
 <tgroup cols="4"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col6" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" class="entry"> Category </th> 
    <th colname="col2" class="entry"> Content type </th> 
    <th colname="col3" class="entry"> Feature </th> 
    <th colname="col6" align="center" class="entry"> 
     <lines>
       HTML5 FF, IE, Chrome, Android Chrome
     </lines> </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_14D9248BD1D8410E83AD27DB4AB3B6ED" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_EFA853CB763446B3B37F2CF6BCC53EE1" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Billing </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_B3A4E5937CEC4052977C08767219BC2B" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Browserify </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_3330E81B86C84AD391AEBFDFE911A47F" /> </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## DASH-Integrationen {#dash-integrations}

| Kategorie | Inhaltstyp | Funktion | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Integrationen | VOD + Live | Adobe Analytics VHL-Integration | ![](assets/supported15.png) |
| Integrationen | VOD + Live | Rechnungsstellung | ![](assets/supported15.png) |
| Integrationen | VOD + Live | Durchsuchen | ![](assets/supported15.png) |

## Erweiterte DASH-Funktionen für Anzeigeneinfügungen (CSAI) {#dash-advanced-insertion-features}

| Kategorie | Inhaltstyp | Funktion | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Ad Insertion | VOD | Nur Anzeige | Nicht unterstützt |
| Ad Insertion | VOD | Targeting-Parameter | Nur VOD |
| Ad Insertion | VOD | Benutzerdefinierte Parameter | Nur VOD |
| Ad Insertion | VOD + Live | Benutzerdefinierte Anzeigenrichtlinie | Nicht unterstützt |
| Ad Insertion | VOD + Live | Verzögertes Laden von Anzeigen | Nicht unterstützt |
| Ad Insertion | VOD | Companion-Anzeigen, Banneranzeigen und anklickbare Anzeigen | Nicht unterstützt |
| Ad Insertion | VOD | VPAID 2.0 | Nicht unterstützt |

## DASH-Kern-Anzeigeneinfüge-Funktionen (CSAI) {#dash-core-ad-insertion}

| Kategorie | Inhaltstyp | Funktion | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Ad Insertion | VOD + Live | Pre-roll | Nur VOD |
| Ad Insertion | VOD + Live | Mid-roll | Nur VOD |
| Ad Insertion | VOD + Live | Post-Roll | Nur VOD |
| Ad Insertion | FER VOD | Auflösung und Verhalten von Anzeigen | Nicht unterstützt |
| Ad Insertion | VOD + Live | Standard-Anzeigenrichtlinie | Nur VOD |
| Ad Insertion | VOD + Live | VAST 2.0/3.0 | Nur VOD |
| Ad Insertion | VOD + Live | VMAP 1.0 | Nur VOD |
| Ad Insertion | VOD + Live | CRS v3.1 | Nur VOD |

## DASH-Inhaltsschutzfunktionen {#dash-content-protection}

<table id="table_hrb_p2g_xx">  
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Kategorie </th> 
   <th colname="col2" class="entry"> Inhaltstyp </th> 
   <th colname="col3" class="entry"> Funktion </th> 
   <th colname="col6" class="entry"> HTML5 FF, IE, Chrome, Android Chrome</th>
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Inhaltsschutz </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> AES-128 </td> 
   <td colname="col6"> Nicht unterstützt </td>
  </tr> 
  <tr> 
   <td colname="col1"> Inhaltsschutz </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> Sample-AES </td> 
   <td colname="col6"> Nicht unterstützt </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Inhaltsschutz </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3"> DRM </td> 
   <td colname="col6"> 
    <ul id="ul_irb_p2g_xx"> 
     <li id="li_C4643F2978BC4C8ABDB3E6C72C75A468">Widevine on 
      <ul id="ul_7047EA49AA3F40FE8F90E0ED6C028D83"> 
       <li id="li_B575735388D74D789D56BF373A470A6D">Chrome </li> 
       <li id="li_855146E4AC3A48E69B65F0022E1C0156">Firefox 47+ </li> 
       <li id="li_BC06B0A6EAAC4FC991C713775A8BB4DA">Chromecast </li> 
      </ul> </li> 
     <li id="li_D48B51C2208F423CB85D08886C2E1C66">PlayReady in Internet Explorer unter Windows 8.1 und Edge </li> 
     <li id="li_2786AC19387241A296E015EE6FD07F2D">Adobe-Zugriff für Windows Firefox (nur Video) </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Erweiterte DASH-Wiedergabefunktionen {#dash-advanced-playback}

| Kategorie | Inhaltstyp | Funktion | HTML5, FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Wiedergabe | VOD | Wiedergabe mit Versatz | ![](assets/supported15.png) |
| Wiedergabe | VOD | Nur-Audio-Wiedergabe | ![](assets/supported15.png) |
| Wiedergabe | VOD | Trick play | ![](assets/supported15.png) |
| Wiedergabe | VOD | Glätte Trick Play | ![](assets/supported15.png) |
| Wiedergabe | VOD + Live | ID3-Parsing | Nicht unterstützt |
| Wiedergabe | VOD | Unterstützung für mehrere Zeiträume | Nur VOD |
| Wiedergabe | VOD + Live | Tokenisierte Streams | Nicht unterstützt |
| Wiedergabe | VOD + Live | Rechnungsstellung | ![](assets/supported15.png) |
| Wiedergabe | VOD + Live | Durchsuchen | ![](assets/supported15.png) |

## DASH-Core-Wiedergabefunktionen {#dash-core-playback}

| Kategorie | Inhaltstyp | Funktion | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Wiedergabe | VOD + Live | Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | ![](assets/supported15.png) |
| Wiedergabe | FER VOD | Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | Nicht unterstützt |
| Wiedergabe | VOD + Live | Adaptive Bitrate | ![](assets/supported15.png) |
| Wiedergabe | VOD + Live | 608/708 Untertitel | ![](assets/supported15.png) |
| Wiedergabe | VOD + Live | WebVTT | Nur VOD |
| Wiedergabe | VOD + Live | Failover | Nur VOD |
| Wiedergabe | VOD + Live | QoS- und Player-Benachrichtigungen | ![](assets/supported15.png) |
| Wiedergabe | VOD + Live | Unterstützung für Cookie-Kopfzeilen | ![](assets/supported15.png) |
| Wiedergabe | VOD + Live | Einrichten von Puffersteuerparametern | ![](assets/supported15.png) |
| Wiedergabe | VOD + Live | Festlegen der Steuerelemente für die adaptive Bitrate | ![](assets/supported15.png) |
| Wiedergabe | VOD + Live | Benutzerdefinierte Tags (EventStream) | Nur VOD (Inline) |
| Wiedergabe | VOD + Live | Spätbindende Audiowiedergabe | Nur VOD |
| Wiedergabe | VOD + Live | 302-Umleitung | Nur VOD |
