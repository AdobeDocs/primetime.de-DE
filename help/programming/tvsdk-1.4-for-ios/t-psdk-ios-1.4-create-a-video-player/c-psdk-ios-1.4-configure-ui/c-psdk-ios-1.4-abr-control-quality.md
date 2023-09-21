---
description: HLS- und DASH-Streams bieten verschiedene Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf der Grundlage der verfügbaren Bandbreite auswählen.
title: Adaptive Bitraten (ABR) für Videoqualität
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# Adaptive Bitraten (ABR) für Videoqualität{#adaptive-bit-rates-abr-for-video-quality}

HLS- und DASH-Streams bieten verschiedene Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf der Grundlage der verfügbaren Bandbreite auswählen.

TVSDK überwacht ständig die Bitrate, um sicherzustellen, dass der Inhalt mit der optimalen Bitrate für die aktuelle Netzwerkverbindung wiedergegeben wird.

Sie können die Richtlinie zum Wechseln der adaptiven Bit-Rate (ABR) sowie die anfänglichen, minimalen und maximalen Bitraten für einen MBR-Stream (multiple bit-rate) festlegen. TVSDK wechselt automatisch zu der Bitrate, die das beste Wiedergabeerlebnis in der angegebenen Konfiguration bietet.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Anfängliche Bitrate </td> 
   <td colname="col2"> <p>Die gewünschte Wiedergabe-Bitrate (in Bits pro Sekunde) für das erste Segment. Beim Start der Wiedergabe wird für das erste Segment das nächstgelegene Profil verwendet, das der anfänglichen Bitrate entspricht oder darüber liegt. </p> <p> Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate unter der Mindestrate liegt, wählt TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt TVSDK die höchste Rate unter der maximalen Rate aus. </p> <p>Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate durch die ABR-Richtlinie bestimmt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale Bitrate </td> 
   <td colname="col2"> <p>Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profile ignoriert, deren Bitrate unter dieser Bitrate liegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale Bitrate </td> 
   <td colname="col2"> <p>Die höchste zulässige Bitrate, zu der der ABR wechseln kann. Beim ABR-Switching werden Profile ignoriert, deren Bitrate über dieser Bitrate liegt. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie die folgenden Informationen:

* TVSDK sendet keine Ereignisse vom Bitratenwechsel.
* Sie können Ihre ABR-Einstellungen jederzeit ändern und der Player wechselt zur Verwendung des Profils, das den neuesten Einstellungen am ehesten entspricht.

Wenn ein Stream beispielsweise die folgenden Profile aufweist:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Wenn Sie einen Bereich von 300000 bis 2000000 angeben, berücksichtigt TVSDK nur die Profile 1, 2 und 3. Dadurch können Anwendungen auf verschiedene Netzwerkbedingungen wie den Wechsel von WLAN zu 3G oder auf verschiedene Geräte wie ein Telefon, ein Tablet oder einen Desktop-Computer eingestellt werden.

## Konfigurieren der adaptiven Bitraten {#section_572FCE4CC28D4DF8BD9C461F00B3CA17}

So konfigurieren Sie adaptive TVSDK-Bitratenparameter:

1. Konfigurieren einer Instanz von `PTABRControlParameters` , um die anfänglichen, minimalen und maximalen Bitrateneinstellungen festzulegen.

   Die Standardwerte werden im folgenden Codefragment angezeigt, Ihre Anwendung kann jedoch für jeden dieser Parameter einen beliebigen ganzzahligen Wert festlegen.

   >[!IMPORTANT]
   >
   >Geben Sie die Bitrateneinstellungen in Bits pro Sekunde (bps) an.

   ```
   // ARC (add autorelease for non-ARC) 
   PTABRControlParameters *abrMetaData =  
       [[PTABRControlParameters alloc] init];  
   
   abrMetaData.initialBitRate = -1; 
   abrMetaData.minBitRate = 0; 
   abrMetaData.maxBitRate = INT_MAX;
   ```

1. Aktualisieren Sie Ihre `PTMediaPlayer` -Instanz mit dem konfigurierten `PTABRControlParameters` -Instanz.

   ```
   // assuming self.player is the PTMediaPlayer instance 
   self.player.abrControlParameters = abrMetaData;
   ```

Beachten Sie Folgendes:

* Die Anwendung muss die `abrControlParameters` Eigenschaft auf `PTMediaPlayer` vor der Konfiguration `PTMediaPlayerItem` -Instanz für die anfänglichen und minimalen Bitrateneinstellungen, die wirksam werden sollen.

  Nach dem Start der Inhaltswiedergabe wirkt sich das Festlegen einer neuen Instanz nur auf die maximale Bitrateneinstellung aus.

* Um die maximale Bitrateneinstellung während der Wiedergabe zu aktualisieren, erstellen Sie eine neue `PTABRControlParameters` und legen Sie sie in der Player-Instanz fest.
* Sie können die maximale Bitrateneinstellung während der Wiedergabe nur auf iOS 8.0 und höher aktualisieren. Bei früheren Versionen wird die Variable `maxBitrate` -Wert verwendet wird, der vor dem Start der Inhaltswiedergabe festgelegt wurde.
