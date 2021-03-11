---
description: Sie können Zeitbereiche in VOD-Streams mit unterschiedlichen Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten markieren, löschen und ersetzen. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.
title: Auswirkungen auf Kombinationen aus Anzeigeneinfügung und -löschung im Anzeigensignalisierungsmodus und Anzeigenmetadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# Auswirkungen auf das Einfügen und Löschen von Werbeanzeigen im Anzeigensignalisierungsmodus und auf Kombinationen von Anzeigenmetadaten{#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Sie können Zeitbereiche in VOD-Streams mit unterschiedlichen Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten markieren, löschen und ersetzen. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.

>[!NOTE]
>
>Bei einem Konflikt zwischen Zeitbereichen und Anzeigensignalisierungsmodi gibt TVSDK den Zeitbereichen Priorität.

**Tabelle 3: Verhalten bei der Kombination von Signalisierungsmodus und Metadaten**

<table>  
 <thead> 
  <tr> 
   <th class="entry"> Anzeigensignalisierungsmodus </th> 
   <th class="entry"> Anzeigenmetadaten </th> 
   <th class="entry"> Erstellte Auflösungen </th> 
   <th class="entry"><span class="codeph"> </span> PlatzierungInformationsbildung erstellt </th> 
   <th class="entry"> Ergebnis </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <b>Serverzuordnung</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> Löschen </td> 
   <td> Löschen </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Bereiche gelöscht </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Löschen, Auditude </td> 
   <td> Löschen, Auditude </td> 
   <td> 
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE),  </span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> Bereiche gelöscht, Anzeigen eingefügt </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Zielgruppe </td> 
   <td> Zielgruppe </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Eingefügte Anzeigen </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Ersetzen, Auditude </td> 
   <td> Löschen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Ersetzte Bereiche </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Markierung </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Markierte Bereiche </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> CustomAd, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Markierte Bereiche, keine eingefügten Anzeigen </td> 
  </tr> 
  <tr> 
   <td> <b>Manifestfarben</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Zielgruppe </td> 
   <td> Zielgruppe </td> 
   <td><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </td> 
   <td> Eingefügte Anzeigen </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Löschen, Auditude </td> 
   <td> Löschen, Auditude </td> 
   <td> 
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> Bereiche gelöscht, Anzeigen eingefügt </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> Mark, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Markierte Bereiche, keine Anzeigen eingefügt </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Löschen </td> 
   <td> Löschen </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Bereiche gelöscht </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Markierung </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Markierte Bereiche </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Ersetzen, Auditude </td> 
   <td> Löschen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Ersetzte Bereiche </td> 
  </tr> 
  <tr> 
   <td> <b>Benutzerdefinierter Zeitraum</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Löschen </td> 
   <td> Löschen </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Bereiche gelöscht </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Löschen, Auditude </td> 
   <td> Löschen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Bereiche gelöscht, keine Anzeigen eingefügt </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Zielgruppe </td> 
   <td> Zielgruppe </td> 
   <td> Keines </td> 
   <td> Keine Anzeigen eingefügt </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Ersetzen, Auditude </td> 
   <td> Löschen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Bereiche durch Anzeigen ersetzt </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Markierung </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Markierte Bereiche </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> Benutzerspezifische Anzeige, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Markierte Bereiche, keine Anzeigen eingefügt </td> 
  </tr> 
  <tr> 
   <td> <b>Nicht festgelegt (Standard)</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Löschen </td> 
   <td> Löschen </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Bereiche gelöscht </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Löschen, Auditude </td> 
   <td> Löschen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Bereiche gelöscht, Anzeigen eingefügt </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Zielgruppe </td> 
   <td> Zielgruppe </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Eingefügte Anzeigen </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Ersetzen, Auditude </td> 
   <td> Löschen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Bereiche durch Anzeigen ersetzt </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Markierung </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Markierte Bereiche </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> CustomAd, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Markierte Bereiche </td> 
  </tr> 
 </tbody> 
</table>

