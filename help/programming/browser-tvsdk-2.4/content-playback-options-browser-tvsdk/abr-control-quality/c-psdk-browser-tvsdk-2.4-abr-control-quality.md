---
description: HLS- und DASH-Streams bieten verschiedene Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. Browser TVSDK kann die Qualitätsstufe für jeden Burst basierend auf der verfügbaren Bandbreite auswählen.
title: Adaptive Bitraten (ABR) für Videoqualität
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# Übersicht {#adaptive-bit-rates-abr-for-video-quality-overview}

HLS- und DASH-Streams bieten verschiedene Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. Browser TVSDK kann die Qualitätsstufe für jeden Burst basierend auf der verfügbaren Bandbreite auswählen.

Browser TVSDK überwacht ständig die Bitrate, um sicherzustellen, dass der Inhalt mit der optimalen Bitrate für die aktuelle Netzwerkverbindung wiedergegeben wird.

Sie können die Richtlinie zum Wechseln der adaptiven Bit-Rate (ABR) sowie die anfänglichen, minimalen und maximalen Bitraten für einen MBR-Stream (multiple bit-rate) festlegen. Browser TVSDK wechselt automatisch zur Bitrate, die das beste Wiedergabeerlebnis in der angegebenen Konfiguration bietet.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Anfängliche Bitrate </td> 
   <td colname="col2">Die gewünschte Wiedergabe-Bitrate (in Bits pro Sekunde) für das erste Segment. Beim Start der Wiedergabe wird für das erste Segment das nächstgelegene Profil verwendet, das der anfänglichen Bitrate entspricht oder darüber liegt. <p> Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate unter der Mindestrate liegt, wählt Browser TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt Browser TVSDK die höchste Rate unter der maximalen Rate aus. </p> <p>Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate durch die ABR-Richtlinie bestimmt. </p> <p><span class="codeph"> initialBitRate</span> gibt einen ganzzahligen Wert zurück, der das Profil "byte-per-second"darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale Bitrate </td> 
   <td colname="col2">Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profile ignoriert, deren Bitrate unter dieser Bitrate liegt. <p><span class="codeph"> minBitRate</span> gibt einen ganzzahligen Wert zurück, der das Bit-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale Bitrate </td> 
   <td colname="col2">Die höchste zulässige Bitrate, zu der der ABR wechseln kann. Beim ABR-Switching werden Profile ignoriert, deren Bitrate über dieser Bitrate liegt. <p><span class="codeph"> maxBitRate</span> gibt einen ganzzahligen Wert zurück, der das Bit-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie die folgenden Informationen:

* Wenn sich die Bitrate ändert, sendet das Browser TVSDK `AdobePSDK.ProfileEvent` mit dem Typ als `AdobePSDK.PSDKEventType.PROFILE_CHANGED`.

* Sie können Ihre ABR-Einstellungen jederzeit ändern und der Player wechselt zur Verwendung des Profils, das den neuesten Einstellungen am ehesten entspricht.

Wenn ein Stream beispielsweise die folgenden Profile aufweist:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Wenn Sie einen Bereich von 300000 bis 2000000 angeben, berücksichtigt Browser TVSDK nur die Profile 1, 2 und 3. Dadurch können Anwendungen sich an verschiedene Netzwerkbedingungen anpassen, wie z. B. den Wechsel von WiFi zu 3G oder zu verschiedenen Geräten wie einem Telefon, einem Tablet oder einem Desktop-Computer.

So legen Sie ABR-Steuerungsparameter fest:

* Legen Sie die Parameter auf der `ABRControlParameters` -Klasse.
