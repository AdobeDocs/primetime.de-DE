---
description: HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der verfügbaren Bandbreite auswählen.
seo-description: HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der verfügbaren Bandbreite auswählen.
seo-title: Adaptive Bitraten (ABR) für Videoqualität
title: Adaptive Bitraten (ABR) für Videoqualität
uuid: e5752d7e-fa7d-407c-96df-c3830a35c66e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Adaptive Bitraten (ABR) für Videoqualität{#adaptive-bit-rates-abr-for-video-quality}

HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der verfügbaren Bandbreite auswählen.

TVSDK überwacht ständig die Bitrate, um sicherzustellen, dass der Inhalt mit der optimalen Bitrate für die aktuelle Netzwerkverbindung wiedergegeben wird.

Sie können die Richtlinie zum Wechseln der adaptiven Bitrate (ABR) und die anfänglichen, minimalen und maximalen Bitraten für einen MBR-Stream (multiple bit rate) festlegen. TVSDK wechselt automatisch zur Bitrate, die die beste Wiedergabe in der angegebenen Konfiguration bietet.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Initial-Bitrate </td> 
   <td colname="col2"> <p>Die gewünschte Wiedergabe-Bitrate (in Bit pro Sekunde) für das erste Segment. Bei Wiedergabe-Beginn wird für das erste Segment das nächstgelegene Profil verwendet, das gleich oder größer als die anfängliche Bitrate ist. </p> <p> Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate niedriger als die minimale Bitrate ist, wählt TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt TVSDK die höchste Rate unter der maximalen Rate aus. </p> <p>Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate von der ABR-Richtlinie bestimmt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale Bitrate </td> 
   <td colname="col2"> <p>Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profil mit einer niedrigeren Bitrate ignoriert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale Bitrate </td> 
   <td colname="col2"> <p>Die höchste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profil mit einer höheren Bitrate als dieser ignoriert. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie die folgenden Informationen:

* TVSDK löst keine Ereignis vom Bitratenwechsel aus.
* Sie können Ihre ABR-Einstellungen jederzeit ändern und der Player wechselt zur Verwendung des Profils, das den neuesten Einstellungen am ehesten entspricht.

Wenn ein Stream beispielsweise die folgenden Profile hat:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Wenn Sie einen Bereich von 300000 bis 2000000 angeben, berücksichtigt TVSDK nur die Profil 1, 2 und 3. Dadurch können Anwendungen an verschiedene Netzwerkbedingungen angepasst werden, z. B. an den Wechsel von WiFi zu 3G oder zu verschiedenen Geräten wie einem Telefon, einem Tablet oder einem Desktop-Computer.

## Adaptive Bitraten konfigurieren {#section_572FCE4CC28D4DF8BD9C461F00B3CA17}

Adaptive Bitratenparameter für TVSDK konfigurieren:

1. Konfigurieren Sie eine Instanz von , `PTABRControlParameters` um die anfänglichen, minimalen und maximalen Bitrateneinstellungen festzulegen.

   Die Standardwerte werden im folgenden Codefragment angezeigt, Ihre Anwendung kann jedoch für jeden dieser Parameter einen beliebigen Ganzzahlwert festlegen.

   >[!IMPORTANT]
   >
   >Geben Sie die Bitrateneinstellungen in Bit pro Sekunde (bps) an.

   ```
   // ARC (add autorelease for non-ARC) 
   PTABRControlParameters *abrMetaData =  
       [[PTABRControlParameters alloc] init];  
   
   abrMetaData.initialBitRate = -1; 
   abrMetaData.minBitRate = 0; 
   abrMetaData.maxBitRate = INT_MAX;
   ```

1. Aktualisieren Sie Ihre `PTMediaPlayer` Instanz mit der konfigurierten `PTABRControlParameters` Instanz.

   ```
   // assuming self.player is the PTMediaPlayer instance 
   self.player.abrControlParameters = abrMetaData;
   ```

Beachten Sie Folgendes:

* Die Anwendung muss die `abrControlParameters` Eigenschaft auf einstellen, `PTMediaPlayer` bevor eine `PTMediaPlayerItem` Instanz konfiguriert wird, damit die anfänglichen und minimalen Bitrateneinstellungen wirksam werden.

   Nach Beginn der Inhaltswiedergabe wirkt sich das Festlegen einer neuen Instanz nur auf die maximale Bitrateneinstellung aus.

* Um die maximale Bitrateneinstellung während der Wiedergabe zu aktualisieren, erstellen Sie eine neue `PTABRControlParameters` Instanz und legen Sie sie auf der Player-Instanz fest.
* Sie können die Einstellung für die maximale Bitrate während der Wiedergabe nur unter iOS 8.0 und höher aktualisieren. Bei älteren Versionen wird der `maxBitrate` Wert verwendet, der vor dem Start der Inhaltswiedergabe festgelegt wurde.

