---
description: Wenn der Medienplayer sein aktuelles Profil auf ein neues Profil umstellt, können Sie Informationen über den Switch abrufen, einschließlich Informationen über den Umschalter, die Breite und Höhe oder warum eine andere Bitrate verwendet wurde.
seo-description: Wenn der Medienplayer sein aktuelles Profil auf ein neues Profil umstellt, können Sie Informationen über den Switch abrufen, einschließlich Informationen über den Umschalter, die Breite und Höhe oder warum eine andere Bitrate verwendet wurde.
seo-title: Informationen zum Profil-Switch
title: Informationen zum Profil-Switch
uuid: e26ad9fb-6c54-450e-ab62-784d9033d214
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Informationen zum Profil-Switch{#get-information-about-profile-switch}

Wenn der Medienplayer sein aktuelles Profil auf ein neues Profil umstellt, können Sie Informationen über den Switch abrufen, einschließlich Informationen über den Umschalter, die Breite und Höhe oder warum eine andere Bitrate verwendet wurde.

1. Hör auf das `ProfileEvent.PROFILE_CHANGED` Ereignis!

   Der TVSDK-Medienplayer löst dieses Ereignis aus, wenn der Algorithmus zum Wechseln der adaptiven Bitrate aufgrund von Netzwerk- oder Maschinenbedingungen zu einem anderen Profil wechselt. (Wenn sich die Bitrate oder der Zeitraum ändert.)
1. Wenn das Ereignis auftritt, überprüfen Sie die folgenden Eigenschaften auf Informationen zum Switch:

   * `profile`: Bezeichner für das neue verwendete Profil.
   * `time`: Die Stream-Zeit, zu der der Switch aufgetreten ist.
   * `description`: Textliche Beschreibung des Grundes für eine Bitratenänderung als Zeichenfolge aus durch Semikolon getrennten Schlüssel/Wert-Paaren. Umfasst maximal eins `Reason` und eins `Bitrate`. Wenn die Informationen nicht verfügbar sind oder sich die Bitrate nicht geändert hat, ist diese Zeichenfolge leer.
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
       <li id="li_E374B029E1AF40689D70A9D30E057C5B">Netzwerkanpassung </li> 
       <li id="li_753862EEF1C9474EA8E20C89F5EF5D8D">Suche </li> 
       <li id="li_EC14923F92CF4D11A47928A8D2DE6D8B">Profil nicht unterstützt </li> 
       <li id="li_695AB4A89C9D4833AF6D8B6424FC912B">Failover </li> 
       </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Bitrate </span> </td> 
      <td colname="col2"> 
       <ul id="ul_1B49BD90A91147359712E1AFD8877E23"> 
       <li id="li_1C8E593C65D34742B14A8D0EAD43E0A9"> <span class="codeph"> up </span>: Die Bitrate wurde erhöht </li> 
       <li id="li_B1A00E3985A849B6855E15CF70D79BB8"> <span class="codeph"> Nach unten </span>: Die Bitrate wurde verringert </li> 
       </ul> </td> 
      </tr> 
    </tbody>
</table>

    Hier einige Beispiele für zurückgegebene &quot;description&quot;-Zeichenfolgen:
    
    &quot;
    &quot;Bitrate:=up;Grund::=Netzwerkadaption;&quot;
    
    &quot;Bitrate::=down;Grund::=Failover;&quot;
    &quot;
    
    * `width`: Ganzzahl, die die Breite in Pixel angibt.
    * &quot;Höhe&quot;: Ganzzahl, die die Höhe in Pixel angibt.
    
    >[!HINWEIS]
    >
    >Daten zur Breite und Höhe sind nur verfügbar, wenn sie im Tag &quot;RESOLUTION&quot;im M3U8-Manifest enthalten sind. Wenn die Informationen nicht im M3U8 enthalten sind, werden die Eigenschaften width und height auf 0 gesetzt, da sie nicht Bestandteil der Informationen zum Profil sind.

<!--<a id="example_A713D420AE2E4E3CB7B78C6BC732BE90"></a>-->

Beispiel:

```
_player.addEventListener(ProfileEvent.PROFILE_CHANGED, onProfileChange); 
private function onProfileChange(event:ProfileEvent):void { 
    _logger.info("#onProfileChange Current profile/bitrate has changed.  
      {0} for reason {1} of resolution [ {2} , {3} ]",  
      event.profile, event.description, event.width, event.height); 
}
```
