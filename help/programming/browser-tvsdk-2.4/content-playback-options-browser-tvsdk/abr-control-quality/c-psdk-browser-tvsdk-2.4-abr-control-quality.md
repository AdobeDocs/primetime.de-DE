---
description: HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. Browser TVSDK kann die Qualitätsstufe für jeden Burst anhand der verfügbaren Bandbreite auswählen.
seo-description: HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. Browser TVSDK kann die Qualitätsstufe für jeden Burst anhand der verfügbaren Bandbreite auswählen.
seo-title: Adaptive Bitraten (ABR) für Videoqualität
title: Adaptive Bitraten (ABR) für Videoqualität
uuid: 4c34fb7b-1bbd-4fa9-8929-d50e85a17396
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 1%

---


# Übersicht {#adaptive-bit-rates-abr-for-video-quality-overview}

HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. Browser TVSDK kann die Qualitätsstufe für jeden Burst anhand der verfügbaren Bandbreite auswählen.

Browser TVSDK überwacht ständig die Bitrate, um sicherzustellen, dass der Inhalt mit der optimalen Bitrate für die aktuelle Netzwerkverbindung wiedergegeben wird.

Sie können die Richtlinie zum Wechseln der adaptiven Bitrate (ABR) und die anfänglichen, minimalen und maximalen Bitraten für einen MBR-Stream (multiple bit rate) festlegen. Browser TVSDK wechselt automatisch zur Bitrate, die die beste Wiedergabe in der angegebenen Konfiguration bietet.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Initial-Bitrate </td> 
   <td colname="col2">Die gewünschte Wiedergabe-Bitrate (in Bit pro Sekunde) für das erste Segment. Bei Wiedergabe-Beginn wird für das erste Segment das nächstgelegene Profil verwendet, das gleich oder größer als die anfängliche Bitrate ist. <p> Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate niedriger als die minimale Bitrate ist, wählt Browser TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt Browser TVSDK die höchste Rate unter der maximalen Rate aus. </p> <p>Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate von der ABR-Richtlinie bestimmt. </p> <p><span class="codeph"> </span> initialBitRatergibt einen ganzzahligen Wert zurück, der das Byte-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale Bitrate </td> 
   <td colname="col2">Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profil mit einer niedrigeren Bitrate ignoriert. <p><span class="codeph"> Gibt </span> einen ganzzahligen Wert zurück, der das Bit-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale Bitrate </td> 
   <td colname="col2">Die höchste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profil mit einer höheren Bitrate als dieser ignoriert. <p><span class="codeph"> </span> maxBitRatergibt einen ganzzahligen Wert zurück, der das Bits pro Sekunde-Profil darstellt. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie die folgenden Informationen:

* Wenn sich die Bitrate ändert, sendet Browser TVSDK `AdobePSDK.ProfileEvent` mit dem Typ `AdobePSDK.PSDKEventType.PROFILE_CHANGED`.

* Sie können Ihre ABR-Einstellungen jederzeit ändern und der Player wechselt zur Verwendung des Profils, das den neuesten Einstellungen am ehesten entspricht.

Wenn ein Stream beispielsweise die folgenden Profile hat:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Wenn Sie einen Bereich von 300000 bis 2000000 angeben, berücksichtigt Browser TVSDK nur die Profil 1, 2 und 3. Dadurch können Anwendungen an verschiedene Netzwerkbedingungen angepasst werden, z. B. an den Wechsel von Wi-Fi zu 3G oder zu verschiedenen Geräten wie einem Telefon, einem Tablet oder einem Desktop-Computer.

So legen Sie ABR-Steuerungsparameter fest:

* Legen Sie die Parameter für die Klasse `ABRControlParameters` fest.

