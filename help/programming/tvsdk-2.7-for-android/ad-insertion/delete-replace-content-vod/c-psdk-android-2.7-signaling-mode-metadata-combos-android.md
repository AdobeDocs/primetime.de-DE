---
description: Sie können Zeitbereiche in VOD-Streams mit unterschiedlichen Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten markieren, löschen und ersetzen. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.
seo-description: Sie können Zeitbereiche in VOD-Streams mit unterschiedlichen Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten markieren, löschen und ersetzen. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.
seo-title: Auswirkungen auf Kombinationen aus Anzeigeneinfügung und -löschung im Anzeigensignalisierungsmodus und Anzeigenmetadaten
title: Auswirkungen auf Kombinationen aus Anzeigeneinfügung und -löschung im Anzeigensignalisierungsmodus und Anzeigenmetadaten
uuid: 7b2a5588-110d-4ce5-aa9c-706d357f211d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Auswirkungen auf Kombinationen aus Anzeigeneinfügung und -löschung im Anzeigensignalisierungsmodus und Anzeigenmetadaten {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Sie können Zeitbereiche in VOD-Streams mit unterschiedlichen Kombinationen aus Anzeigensignalisierungsmodus und Anzeigenmetadaten markieren, löschen und ersetzen. Verschiedene Kombinationen aus Signalmodus und Metadaten führen zu unterschiedlichem Verhalten.

>[!TIP]
>
>Bei einem Konflikt zwischen Zeitbereichen und Anzeigensignalisierungsmodi gibt TVSDK den Zeitbereichen Priorität.

Die folgende Tabelle enthält Details zum Verhalten der Kombination aus Signalmodus und Metadaten:

<table id="table_6044AA1ACFA244FA814EA2D0766C6D12"> 
 <thead> 
  <tr> 
   <th class="entry"> Anzeigensignalisierungsmodus </th> 
   <th class="entry"> Anzeigenmetadaten </th> 
   <th class="entry"> Erstellte Auflösungen </th> 
   <th class="entry"><span class="codeph"> Platzierungsinformationen</span> erstellt </th> 
   <th class="entry"> Ergebnis </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="1"> <p><b>Serverzuordnung</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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
    <ul id="ul_E0A2F885E93B4D23A486C37B305E17D8"> 
     <li id="li_D977B398D3904A44AFEC4B05AB0E3340"><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), </span> </li> 
     <li id="li_439886CB38AA46239C2E40352443888A"><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </li> 
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
   <td> Markierte Bereiche, keine Anzeigen eingefügt </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p><b>Manifestfarben</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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
    <ul id="ul_2DD298538E9344B9BAB882485BB57747"> 
     <li id="li_F39A69EFA7ED45C18978A2C462AF7641"><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </li> 
     <li id="li_8CCDA3B1C63F4BC396F28F443D8C42F8"><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </li> 
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
   <td colname="1"> <p><b>Benutzerdefinierter Zeitraum</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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
   <td colname="1"> <p><b>Nicht festgelegt (Standard)</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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

