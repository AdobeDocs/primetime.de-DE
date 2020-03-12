---
description: HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der aktuellen Pufferung und der verfügbaren Bandbreite auswählen.
seo-description: HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der aktuellen Pufferung und der verfügbaren Bandbreite auswählen.
seo-title: Adaptive Bitraten (ABR) für Videoqualität
title: Adaptive Bitraten (ABR) für Videoqualität
uuid: 87fd7d97-8d13-430d-a88e-bcbff8026679
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Übersicht {#adaptive-bit-rates-abr-for-video-quality-overview}

HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der aktuellen Pufferung und der verfügbaren Bandbreite auswählen.

TVSDK überwacht ständig die Bitrate, um sicherzustellen, dass der Inhalt mit der optimalen Bitrate für die aktuelle Netzwerkverbindung wiedergegeben wird. Sie können die Richtlinie zum Wechseln der adaptiven Bitrate (ABR) und die anfänglichen, minimalen und maximalen Bitraten für einen MBR-Stream (multiple bit rate) festlegen. TVSDK wechselt automatisch zur Bitrate, die die beste Wiedergabe in der angegebenen Konfiguration bietet.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Initial-Bitrate </td> 
   <td colname="col2"> <p>Die gewünschte Wiedergabe-Bitrate (in Bit pro Sekunde) für das erste Segment. </p> <p>Bei Wiedergabe-Beginn wird für das erste Segment das nächstgelegene Profil verwendet, das gleich oder größer als die anfängliche Bitrate ist. Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate niedriger als die minimale Bitrate ist, wählt TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt TVSDK die höchste Rate unter der maximalen Rate aus. Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate von der ABR-Richtlinie bestimmt. </p> <p><span class="codeph"> getABRInitialBitRate</span> gibt einen ganzzahligen Wert zurück, der das Byte-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale Bitrate </td> 
   <td colname="col2"> <p>Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. </p> <p>Beim ABR-Switching werden Profil mit einer niedrigeren Bitrate ignoriert. <span class="codeph"> getABRMinBitRate</span> gibt einen ganzzahligen Wert zurück, der das Bits pro Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale Bitrate </td> 
   <td colname="col2"> <p>Die höchste zulässige Bitrate, zu der die ABR wechseln kann. </p> <p>Beim ABR-Switching werden Profil mit einer höheren Bitrate als dieser ignoriert. <span class="codeph"> getABRMaxBitRate</span> gibt einen ganzzahligen Wert zurück, der das Bits pro Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR-Switching-Richtlinie </td> 
   <td colname="col2"> <p>Die Wiedergabe wechselt nach Möglichkeit schrittweise zum Profil mit der höchsten Bitrate. Sie können die Richtlinie für das ABR-Switching festlegen, die bestimmt, wie schnell TVSDK zwischen Profilen wechselt. Der Standardwert ist <span class="codeph"> ABR_MODERATE</span>. </p> <p>Wenn TVSDK beschließt, zu einer höheren Bitrate zu wechseln, wählt der Player das ideale Bitrate-Profil, zu dem er je nach der aktuellen ABR-Richtlinie wechseln soll: 
     <ul id="ul_AC9C99D84A3B4A8DBD1A05CC05DEE771"> 
      <li id="li_B79C0AA2CBFB42FF98A257CEC9C400BA"><span class="codeph"> ABR_CONSERVATIVE</span>: Wechselt zum Profil mit der nächsthöheren Bitrate, wenn die Bandbreite um 50 % höher als die aktuelle Bitrate ist. </li> 
      <li id="li_38CC3A95D8634F359D0F7C273D0108C0"><span class="codeph"> ABR_MODERATE</span>: Wechselt zum Profil mit der nächsten höheren Bitrate, wenn die Bandbreite um 20 % höher ist als die aktuelle Bitrate. </li> 
      <li id="li_E845C035420D4B3FB2B179F448F8CA85"><span class="codeph"> ABR_AGGRESSIVE</span>: Wechselt sofort zum Profil mit der höchsten Bitrate, wenn die Bandbreite höher als die aktuelle Bitrate ist. </li> 
     </ul> </p> <p>Wenn die anfängliche Bitrate null ist oder nicht angegeben wurde, aber eine Richtlinie angegeben ist, können Sie Beginn mit dem niedrigsten Profil für die Bitrate einer konservativen Richtlinie wiedergeben, mit dem Profil, das der mittleren Bitrate der verfügbaren Profil bei einer moderaten Richtlinie am nächsten liegt, und mit dem höchsten Profil für eine aggressive Richtlinie. </p> <p>Die Richtlinie funktioniert in den Beschränkungen der minimalen und maximalen Bitraten, wenn diese angegeben werden. </p> <p> <span class="codeph"> getABRPopolicy</span> gibt die aktuelle Einstellung aus dem <span class="codeph"> ABRControlParameters</span> -Enum zurück: ABR_CONSERVATIVE <span class="codeph"> ,</span>ABR_MODERATE <span class="codeph"> oder</span>ABR_AGGRESSIVE <span class="codeph"></span>. </p> <p>Weitere Informationen finden Sie unter API-Dokument zu ABR-Steuerungsparametern. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie die folgenden Informationen:

* Der TVSDK-Failover-Mechanismus kann Ihre Einstellungen außer Kraft setzen, da TVSDK eine kontinuierliche Wiedergabe bevorzugt, anstatt strikt Ihre Steuerungsparameter einzuhalten.
* Wenn sich die Bitrate ändert, sendet TVSDK `onProfileChanged` Ereignis in `PlaybackEventListener`.

* Sie können Ihre ABR-Einstellungen jederzeit ändern und der Player wechselt zur Verwendung des Profils, das den neuesten Einstellungen am ehesten entspricht.

Wenn ein Stream beispielsweise die folgenden Profile hat:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Wenn Sie einen Bereich von 300000 bis 2000000 angeben, berücksichtigt TVSDK nur die Profil 1, 2 und 3. Dadurch können Anwendungen an verschiedene Netzwerkbedingungen angepasst werden, z. B. an den Wechsel von Wi-Fi zu 3G oder zu verschiedenen Geräten wie einem Telefon, einem Tablet oder einem Desktop-Computer.

Um ABR-Steuerungsparameter festzulegen, legen Sie die Parameter für die `ABRControlParameter` Klasse fest.