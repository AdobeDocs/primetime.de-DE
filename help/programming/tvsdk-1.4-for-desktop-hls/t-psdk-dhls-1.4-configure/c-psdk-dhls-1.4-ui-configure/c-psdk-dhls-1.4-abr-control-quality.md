---
description: HLS- und DASH-Streams bieten verschiedene Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf der Grundlage der verfügbaren Bandbreite auswählen.
title: Adaptive Bitraten (ABR) für Videoqualität
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '973'
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
   <td colname="col2"> <p>Die gewünschte Wiedergabe-Bitrate (in Bits pro Sekunde) für das erste Segment. Beim Start der Wiedergabe wird für das erste Segment das nächstgelegene Profil verwendet, das der anfänglichen Bitrate entspricht oder darüber liegt. </p> <p> Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate unter der Mindestrate liegt, wählt TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt TVSDK die höchste Rate unter der maximalen Rate aus. </p> <p>Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate durch die ABR-Richtlinie bestimmt. </p> <p> <span class="apiname"> ABRInitialBitRate </span> gibt einen ganzzahligen Wert zurück, der das Profil "byte-per-second"darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale Bitrate </td> 
   <td colname="col2"> <p>Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profile ignoriert, deren Bitrate unter dieser Bitrate liegt. </p> <p> <span class="apiname"> ABRMinBitRate </span> gibt einen ganzzahligen Wert zurück, der das Bit-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale Bitrate </td> 
   <td colname="col2"> <p>Die höchste zulässige Bitrate, zu der der ABR wechseln kann. Beim ABR-Switching werden Profile ignoriert, deren Bitrate über dieser Bitrate liegt. </p> <p> <span class="apiname"> ABRMaxBitRate </span> gibt einen ganzzahligen Wert zurück, der das Bit-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR-Switching-Richtlinie </td> 
   <td colname="col2"> Die Wiedergabe wechselt nach Möglichkeit schrittweise zum Profil mit der höchsten Bitrate. Sie können die Richtlinie für ABR-Switching festlegen, die bestimmt, wie schnell TVSDK zwischen Profilen wechselt. Der Standardwert ist <span class="codeph"> MODERATE_POLICY </span>. <p>Wenn TVSDK beschließt, zu einer höheren Bitrate zu wechseln, wählt der Player das ideale Bitratenprofil aus, zu dem basierend auf der aktuellen ABR-Richtlinie gewechselt werden soll: 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY </span>: Wechselt zum Profil mit der nächsthöheren Bitrate, wenn die Bandbreite um 50 % über der aktuellen Bitrate liegt. </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY </span>: Wechselt zum Profil mit der nächsten höheren Bitrate, wenn die Bandbreite um 20 % über der aktuellen Bitrate liegt. </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGGRESSIVE_POLICY </span>: Wechselt sofort zum Profil mit der höchsten Bitrate, wenn die Bandbreite über der aktuellen Bitrate liegt. </li> 
     </ul> </p> <p>Wenn die anfängliche Bitrate null oder nicht angegeben ist, aber eine Richtlinie angegeben ist, beginnt die Wiedergabe mit dem niedrigsten Bitratenprofil für Konservative, dem Profil, das der Median-Bitrate der verfügbaren Profile für Moderate am nächsten ist, und dem Profil mit der höchsten Bitrate für aggressive. </p> <p>Die Richtlinie arbeitet in den Begrenzungen der Mindest- und Höchstbit-Raten, wenn diese festgelegt sind. </p> <p> <span class="codeph"> ABRPolicy </span> gibt die aktuelle Einstellung aus der <span class="codeph"> ABRControlParameters </span> enum: CONSERVATIVE_POLICY, MODERATE_POLICY oder AGGRESSIVE_POLICY. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie die folgenden Informationen:

* Der TVSDK-Failover-Mechanismus überschreibt möglicherweise Ihre Einstellungen, da TVSDK eine kontinuierliche Wiedergabe bevorzugt, anstatt die Kontrollparameter strikt einzuhalten.
* Wenn sich die Bitrate ändert, sendet TVSDK `ProfileEvent.PROFILE_CHANGED`.
* Sie können Ihre ABR-Einstellungen jederzeit ändern und der Player wechselt zur Verwendung des Profils, das den neuesten Einstellungen am ehesten entspricht.

Wenn ein Stream beispielsweise die folgenden Profile aufweist:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Wenn Sie einen Bereich von 300000 bis 2000000 angeben, berücksichtigt TVSDK nur die Profile 1, 2 und 3. Dadurch können Anwendungen sich an verschiedene Netzwerkbedingungen anpassen, wie z. B. den Wechsel von WiFi zu 3G oder zu verschiedenen Geräten wie einem Telefon, einem Tablet oder einem Desktop-Computer.

Führen Sie einen der folgenden Schritte aus, um ABR-Steuerungsparameter festzulegen:

* Verwenden Sie die `ABRControlParameterBuilder` Helper-Klasse zum Festlegen einer Teilmenge der Parameter (wird auf `ABRControlParameter` im Hintergrund)

* Legen Sie die Parameter auf der `ABRControlParameter` -Klasse.

## Adaptive Bitraten mithilfe von ABRControlParametersBuilder konfigurieren {#section_3DDE397A7CE445E1832EBAA46CE5C069}

Verwenden der `ABRControlParametersBuilder` Helper-Klasse ist die einfachste und effizienteste Methode, ABR-Parameter festzulegen.

* Die `ABRControlParametersBuilder` -Konstruktor setzt alle ABR-Parameter auf Standardwerte für den zugrunde liegenden `ABRControlParameters` -Objekt.

* Sie können einzelne ABR-Parameter während der Laufzeit zurücksetzen, solange Sie einen Verweis auf denselben `ABRControlParametersBuilder` -Instanz.

Diese Klasse enthält auch die `toABRControlParameters()` Helper-Methode. Verwenden Sie diese Methode, um eine Instanz von `ABRControlParameters` und legen Sie sie auf der `mediaPlayer.ABRControlParameters` -Eigenschaft. Dadurch werden Ihre Einstellungen im Player wirksam.

1. Instanziieren Sie die `ABRControlParametersBuilder` Helper-Klasse und legen Sie die Parameter auf dem Media Player fest.

   >[!NOTE]
   >
   >Beispielsweise initialisiert das folgende Beispiel alle Parameter auf die Standardwerte, setzt dann nur die Richtlinie auf &quot;konservativ&quot;und beschränkt die maximale Bitrate auf 1000000:
   >
   >```
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```
   >

1. Ändern Sie einzelne ABR-Parameter zur Laufzeit.

   So ändern Sie einzelne Parameter, während Sie den Rest der Parameter unverändert lassen:

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   Um Ihre vorherigen Einstellungen beizubehalten, müssen Sie einen Verweis auf dasselbe `ABRControlParametersBuilder` -Instanz, die Sie in Schritt 1 erstellt haben.

## Adaptive Bitraten mithilfe von ABRControlParameters konfigurieren {#section_02161FD0A73F40ED9CAE17F9AF850483}

Sie können ABR-Kontrollwerte nur mit `ABRControlParameters`, aber Sie können jederzeit ein neues erstellen.

Diese Möglichkeit, ABR-Parameter festzulegen, wurde vor der Existenz der `ABRControlParametersBuilder` -Klasse, aber diese Fähigkeit ist immer noch für die Festlegung von ABR-Parametern während der Erstellung wirksam. Um jedoch einzelne Parameter nach der Erstellung zu ändern, sollten Sie die `ABRControlParametersBuilder` -Klasse.

Die folgenden Bedingungen gelten für `ABRControlParameters`:

* Sie müssen Werte für alle Parameter zum Zeitpunkt der Erstellung angeben.
* Sie können einzelne Werte nach der Bauzeit nicht mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird ein `ArgumentError` geworfen wird.

1. Entscheiden Sie für die Start-, Mindest- und HöchstBitraten.
1. Bestimmen Sie die ABR-Richtlinie:

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters` und weisen Sie sie dem Media Player zu.

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```
