---
description: Wenn der Medienplayer sein aktuelles Profil in ein neues Profil ändert, können Sie Informationen über den Switch abrufen, einschließlich Informationen zum Umschalten, zur Breite und Höhe oder dazu, warum eine andere Bitrate verwendet wurde.
title: Informationen zum Profilwechsel erhalten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Informationen zum Profilwechsel erhalten{#get-information-about-profile-switch}

Wenn der Medienplayer sein aktuelles Profil in ein neues Profil ändert, können Sie Informationen über den Switch abrufen, einschließlich Informationen zum Umschalten, zur Breite und Höhe oder dazu, warum eine andere Bitrate verwendet wurde.

1. Suchen Sie nach `AdobePSDK.PSDKEventType.PROFILE_CHANGED` -Ereignis.

   Der Browser TVSDK-Medienplayer sendet dieses Ereignis, wenn der Algorithmus für den Wechsel der adaptiven Bitrate aufgrund von Netzwerk- oder Maschinenbedingungen zu einem anderen Profil wechselt. (Wenn sich die Bitrate oder der Zeitraum ändert.)
1. Wenn das Ereignis eintritt, überprüfen Sie die folgenden Eigenschaften auf Informationen zum Switch:

   * `profile`: Kennung für das neue verwendete Profil.
   * `time`: Die Stream-Zeit, zu der der Wechsel erfolgte.
   * `description`: Textbeschreibung des Grundes für eine Bitratenänderung als Zeichenfolge aus durch Semikolon getrennten Schlüssel/Wert-Paaren. Beinhaltet maximal 1 `Reason` und einem `Bitrate`. Wenn die Informationen nicht verfügbar sind oder sich die Bitrate nicht geändert hat, ist diese Zeichenfolge leer.

   <table id="table_E400FD9C57FF40CBAC14AF6847CD8301"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> Schlüsselname </th> 
      <th colname="col2" class="entry"> Mögliche Werte </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Grund </span> </td> 
      <td colname="col2"> 
        <ul id="ul_37DDE3F297634ED6B47DF5D73F969369"> 
        <li id="li_E374B029E1AF40689D70A9D30E057C5B">Netzwerkadaption </li> 
        <li id="li_753862EEF1C9474EA8E20C89F5EF5D8D">Suche </li> 
        <li id="li_EC14923F92CF4D11A47928A8D2DE6D8B">Profil wird nicht unterstützt </li> 
        <li id="li_695AB4A89C9D4833AF6D8B6424FC912B">Failover </li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Bitrate </span> </td> 
      <td colname="col2"> 
        <ul id="ul_1B49BD90A91147359712E1AFD8877E23"> 
        <li id="li_1C8E593C65D34742B14A8D0EAD43E0A9"> <span class="codeph"> up </span>: Bitrate erhöht </li> 
        <li id="li_B1A00E3985A849B6855E15CF70D79BB8"> <span class="codeph"> down </span>: Bitrate reduziert </li> 
        </ul> </td> 
      </tr> 
    </tbody> 
    </table>

   Im Folgenden finden Sie einige Beispiele für zurückgegebene `description` Zeichenfolgen:

   ```
   "Bitrate::=up;Reason::=Network Adaptation;" 
   
   "Bitrate::=down;Reason::=Failover;"
   ```

   * `width`: Ganzzahl, die die Breite in Pixel angibt.
   * `height`: Ganzzahl, die die Höhe in Pixel angibt.

   >[!NOTE]
   >
   >Daten zur Breite und Höhe sind nur verfügbar, wenn sie in der Variablen `RESOLUTION` -Tag im M3U8-Manifest. Wenn die Informationen nicht im M3U8 enthalten sind, werden die Eigenschaften für Breite und Höhe auf 0 gesetzt, da sie nicht Teil der Profilinformationen sind.
