---
description: Der Anzeigesignalmodus gibt an, wo der Videostream Werbeinformationen erhalten soll.
title: Anzeigenanzeigemodus
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Anzeigenanzeigemodus {#ad-signaling-mode}

Der Anzeigesignalmodus gibt an, wo der Videostream Werbeinformationen erhalten soll.

Die gültigen Werte sind `DEFAULT`, `SERVER_MAP`, und `MANIFEST_CUES`.

In der folgenden Tabelle werden die Auswirkungen von `AdSignalingMode` Werte für die verschiedenen Arten von HLS-Streams:

<table frame="all" colsep="1" rowsep="1" id="table_AdSignalingMode"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> </th> 
   <th colname="2" class="entry"> <b>Standard </b></th> 
   <th colname="3" class="entry"><b> Manifestbefehle</b> </th> 
   <th colname="4" class="entry"> <b>Ad Server Map </b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Video on Demand (VOD) </td> 
   <td colname="2"> 
    <ul id="ul_E79DA79107364D0D8B46A1859CA75B5C"> 
     <li id="li_B259ED87743F463095071F58DC840E39"> Verwendet die Serverzuordnung zur Platzierungserkennung </li> 
     <li id="li_8957E4151466467BA6C954E5010E34EA"> Anzeigen werden eingefügt </li> 
    </ul> </td> 
   <td colname="3"> 
    <ul id="ul_D462C76717D94DE09915BDF6E9B3FB68"> 
     <li id="li_FB46108F4AD9457D99D2618ABEF7DBD1"> Verwendet In-Stream-Hinweise zur Platzierungserkennung </li> 
     <li id="li_C3F7FBB98F524CEF97D17318C292E9EA"> Pre-Roll-Anzeigen werden in den Hauptstrom eingefügt </li> 
     <li id="li_A56E1545F84840DFA6D065DA60E98C31"> Mid-Roll-Anzeigen ersetzen den Hauptstrom </li> 
    </ul> </td> 
   <td colname="4"> 
    <ul id="ul_F10192B1B6F745CBB0D4C1A6D52A57B4"> 
     <li id="li_2ADACF71FA5F4A08A00A3399F5593420"> Verwendet die Serverzuordnung zur Platzierungserkennung </li> 
     <li id="li_1201085B9C554A4BBD471E7EB2E363AC"> Anzeigen werden eingefügt </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> Live/linear </td> 
   <td colname="2"> 
    <ul id="ul_82AAC9EE056F49E999F809536A96C2F8"> 
     <li id="li_73BAD2BAA95F4592808B77F8DA436237"> Verwendet Manifestzeichen zur Platzierungserkennung </li> 
     <li id="li_A97B6F61078D4149A984B2412021E103"> Anzeigen ersetzen den Hauptstrom </li> 
    </ul> </td> 
   <td colname="3"> 
    <ul id="ul_CAED2D4F46334D76AE025482881BF843"> 
     <li id="li_A8023845A037482DBFDEF7EF247FECFD"> Verwendet In-Stream-Hinweise zur Platzierungserkennung </li> 
     <li id="li_62A3CDAD249344EB89043B2AE0F4D7FF"> Anzeigen ersetzen den Hauptstrom </li> 
    </ul> </td> 
   <td colname="4"> Nicht unterstützt </td> 
  </tr> 
 </tbody> 
</table>
