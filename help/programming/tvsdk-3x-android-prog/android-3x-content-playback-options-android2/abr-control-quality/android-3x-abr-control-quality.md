---
description: HLS- und DASH-Streams bieten verschiedene Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf der Basis der aktuellen Pufferung und der verfügbaren Bandbreite auswählen.
title: Adaptive Bitraten (ABR) für Videoqualität
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Übersicht {#adaptive-bit-rates-abr-for-video-quality-overview}

HLS- und DASH-Streams bieten verschiedene Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf der Basis der aktuellen Pufferung und der verfügbaren Bandbreite auswählen.

TVSDK überwacht ständig die Bitrate, um sicherzustellen, dass der Inhalt mit der optimalen Bitrate für die aktuelle Netzwerkverbindung wiedergegeben wird. Sie können die Richtlinie zum Wechseln der adaptiven Bitrate (ABR) sowie die anfänglichen, minimalen und maximalen Bitraten für einen MBR-Stream (multiple bit-rate) festlegen. TVSDK wechselt automatisch zu der Bitrate, die das beste Wiedergabeerlebnis in der angegebenen Konfiguration bietet.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Anfängliche Bitrate </td> 
   <td colname="col2"> <p>Die gewünschte Wiedergabe-Bitrate (in Bits pro Sekunde) für das erste Segment. </p> <p>Beim Start der Wiedergabe wird für das erste Segment das nächstgelegene Profil verwendet, das der anfänglichen Bitrate entspricht oder darüber liegt. Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate unter der Mindestrate liegt, wählt TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt TVSDK die höchste Rate unter der maximalen Rate aus. Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate durch die ABR-Richtlinie bestimmt. </p> <p><span class="codeph"> getABRInitialBitRate</span> gibt einen ganzzahligen Wert zurück, der das Profil "byte-per-second"darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale Bitrate </td> 
   <td colname="col2"> <p>Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. </p> <p>Beim ABR-Switching werden Profile ignoriert, deren Bitrate unter dieser Bitrate liegt. <span class="codeph"> getABRMinBitRate</span> gibt einen ganzzahligen Wert zurück, der das Bit-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale Bitrate </td> 
   <td colname="col2"> <p>Die höchste zulässige Bitrate, zu der der ABR wechseln kann. </p> <p>Beim ABR-Switching werden Profile ignoriert, deren Bitrate über dieser Bitrate liegt. <span class="codeph"> getABRMaxBitRate</span> gibt einen ganzzahligen Wert zurück, der das Bit-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR-Switching-Richtlinie </td> 
   <td colname="col2"> <p>Die Wiedergabe wechselt nach Möglichkeit schrittweise zum Profil mit der höchsten Bitrate. Sie können die Richtlinie für ABR-Switching festlegen, die bestimmt, wie schnell TVSDK zwischen Profilen wechselt. Der Standardwert ist <span class="codeph"> ABR_MODERATE</span>. </p> <p>Wenn TVSDK beschließt, zu einer höheren Bitrate zu wechseln, wählt der Player das ideale Bitratenprofil aus, zu dem basierend auf der aktuellen ABR-Richtlinie gewechselt werden soll: 
     <ul id="ul_AC9C99D84A3B4A8DBD1A05CC05DEE771"> 
      <li id="li_B79C0AA2CBFB42FF98A257CEC9C400BA"><span class="codeph"> ABR_CONSERVATIVE</span>: Wechselt zum Profil mit der nächsthöheren Bitrate, wenn die Bandbreite um 50 % über der aktuellen Bitrate liegt. </li> 
      <li id="li_38CC3A95D8634F359D0F7C273D0108C0"><span class="codeph"> ABR_MODERATE</span>: Wechselt zum Profil mit der nächsten höheren Bitrate, wenn die Bandbreite um 20 % über der aktuellen Bitrate liegt. </li> 
      <li id="li_E845C035420D4B3FB2B179F448F8CA85"><span class="codeph"> ABR_AGGRESSIVE</span>: Wechselt sofort zum Profil mit der höchsten Bitrate, wenn die Bandbreite über der aktuellen Bitrate liegt. </li> 
     </ul> </p> <p>Wenn die anfängliche Bitrate null ist oder nicht angegeben, aber eine Richtlinie angegeben ist, beginnt die Wiedergabe mit dem niedrigsten Bitratenprofil für eine konservative Richtlinie, dem Profil, das der Median-Bitrate der verfügbaren Profile für eine moderate Richtlinie am nächsten ist, und dem Profil mit der höchsten Bitrate für eine aggressive Richtlinie. </p> <p>Die Richtlinie arbeitet in den Begrenzungen der Mindest- und Höchstbit-Raten, wenn diese festgelegt sind. </p> <p> <span class="codeph"> getABRPolicy</span> gibt die aktuelle Einstellung aus der <span class="codeph"> ABRControlParameters</span> enum: <span class="codeph"> ABR_CONSERVATIVE</span>, <span class="codeph"> ABR_MODERATE</span>oder <span class="codeph"> ABR_AGGRESSIVE</span>. </p> <p>Weitere Informationen finden Sie in der ABR Control Parameters API-Dokumentation. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie die folgenden Informationen:

* Der TVSDK-Failover-Mechanismus überschreibt möglicherweise Ihre Einstellungen, da TVSDK eine kontinuierliche Wiedergabe bevorzugt, anstatt die Kontrollparameter strikt einzuhalten.
* Wenn sich die Bitrate ändert, sendet TVSDK `onProfileChanged` Ereignisse in `PlaybackEventListener`.

* Sie können Ihre ABR-Einstellungen jederzeit ändern und der Player wechselt zur Verwendung des Profils, das den neuesten Einstellungen am ehesten entspricht.

Wenn ein Stream beispielsweise die folgenden Profile aufweist:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Wenn Sie einen Bereich von 300000 bis 2000000 angeben, berücksichtigt TVSDK nur die Profile 1, 2 und 3. Dadurch können Anwendungen sich an verschiedene Netzwerkbedingungen anpassen, wie z. B. den Wechsel von WiFi zu 3G oder zu verschiedenen Geräten wie einem Telefon, einem Tablet oder einem Desktop-Computer.

Um ABR-Steuerungsparameter festzulegen, legen Sie die Parameter auf der `ABRControlParameter` -Klasse.
