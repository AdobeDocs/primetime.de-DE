---
description: HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der verfügbaren Bandbreite auswählen.
seo-description: HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der verfügbaren Bandbreite auswählen.
seo-title: Adaptive Bitraten (ABR) für Videoqualität
title: Adaptive Bitraten (ABR) für Videoqualität
uuid: e3d5ef90-067d-48e0-a025-081de931d842
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 0%

---


# Adaptive Bitraten (ABR) für Videoqualität{#adaptive-bit-rates-abr-for-video-quality}

HLS- und DASH-Streams bieten unterschiedliche Bitratenkodierungen (Profile) für den gleichen kurzen Videoaufruf. TVSDK kann die Qualitätsstufe für jeden Burst auf Basis der verfügbaren Bandbreite auswählen.

TVSDK überwacht ständig die Bitrate, um sicherzustellen, dass der Inhalt mit der optimalen Bitrate für die aktuelle Netzwerkverbindung wiedergegeben wird.

Sie können die Richtlinie zum Wechseln der adaptiven Bitrate (ABR) und die anfänglichen, minimalen und maximalen Bitraten für einen MBR-Stream (multiple bit rate) festlegen. TVSDK wechselt automatisch zur Bitrate, die die beste Wiedergabe in der angegebenen Konfiguration bietet.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Initial-Bitrate </td> 
   <td colname="col2"> <p>Die gewünschte Wiedergabe-Bitrate (in Bit pro Sekunde) für das erste Segment. Bei Wiedergabe-Beginn wird für das erste Segment das nächstgelegene Profil verwendet, das gleich oder größer als die anfängliche Bitrate ist. </p> <p> Wenn eine minimale Bitrate definiert ist und die anfängliche Bitrate niedriger als die minimale Bitrate ist, wählt TVSDK das Profil mit der niedrigsten Bitrate über der minimalen Bitrate aus. Wenn die anfängliche Rate über der maximalen Rate liegt, wählt TVSDK die höchste Rate unter der maximalen Rate aus. </p> <p>Wenn die anfängliche Bitrate null oder nicht definiert ist, wird die anfängliche Bitrate von der ABR-Richtlinie bestimmt. </p> <p> <span class="apiname"> ABRInitialBitRate  </span> gibt einen ganzzahligen Wert zurück, der das Byte-pro-Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale Bitrate </td> 
   <td colname="col2"> <p>Die niedrigste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profil mit einer niedrigeren Bitrate ignoriert. </p> <p> <span class="apiname"> ABRMinBitRate  </span> gibt einen ganzzahligen Wert zurück, der das Bits pro Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale Bitrate </td> 
   <td colname="col2"> <p>Die höchste zulässige Bitrate, zu der die ABR wechseln kann. Beim ABR-Switching werden Profil mit einer höheren Bitrate als dieser ignoriert. </p> <p> <span class="apiname"> ABRMaxBitRate  </span> gibt einen ganzzahligen Wert zurück, der das Bits pro Sekunde-Profil darstellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR-Switching-Richtlinie </td> 
   <td colname="col2"> Die Wiedergabe wechselt nach Möglichkeit schrittweise zum Profil mit der höchsten Bitrate. Sie können die Richtlinie für das ABR-Switching festlegen, die bestimmt, wie schnell TVSDK zwischen Profilen wechselt. Die Standardeinstellung ist <span class="codeph"> MODERATE_POLICY </span>. <p>Wenn TVSDK beschließt, zu einer höheren Bitrate zu wechseln, wählt der Player das ideale Bitrate-Profil, zu dem er je nach der aktuellen ABR-Richtlinie wechseln soll: 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY  </span>: Wechselt zum Profil mit der nächsthöheren Bitrate, wenn die Bandbreite um 50 % höher als die aktuelle Bitrate ist. </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY  </span>: Wechselt zum Profil mit der nächsten höheren Bitrate, wenn die Bandbreite um 20 % höher ist als die aktuelle Bitrate. </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGGRESSIVE_POLICY  </span>: Wechselt sofort zum Profil mit der höchsten Bitrate, wenn die Bandbreite höher als die aktuelle Bitrate ist. </li> 
     </ul> </p> <p>Wenn die anfängliche Bitrate null ist oder nicht angegeben ist, aber eine Richtlinie angegeben ist, werden Beginn mit dem niedrigsten Bitrate-Profil für konservativ wiedergegeben, dem Profil, das der Median-Bitrate der verfügbaren Profil für mäßig gehalten wird, und dem höchsten Bitrate-Profil für aggressiv. </p> <p>Die Richtlinie funktioniert in den Beschränkungen der minimalen und maximalen Bitraten, wenn diese angegeben werden. </p> <p> <span class="codeph"> ABRPopolicy  </span> gibt die aktuelle Einstellung aus dem  <span class="codeph"> ABRControlParameters- </span> Enum zurück: CONSERVATIVE_POLICY, MODERATE_POLICY oder AGGRESSIVE_POLICY. </p> </td> 
  </tr> 
 </tbody> 
</table>

Beachten Sie die folgenden Informationen:

* Der TVSDK-Failover-Mechanismus kann Ihre Einstellungen außer Kraft setzen, da TVSDK eine kontinuierliche Wiedergabe bevorzugt, anstatt strikt Ihre Steuerungsparameter einzuhalten.
* Wenn sich die Bitrate ändert, sendet TVSDK `ProfileEvent.PROFILE_CHANGED`.
* Sie können Ihre ABR-Einstellungen jederzeit ändern und der Player wechselt zur Verwendung des Profils, das den neuesten Einstellungen am ehesten entspricht.

Wenn ein Stream beispielsweise die folgenden Profile hat:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Wenn Sie einen Bereich von 300000 bis 2000000 angeben, berücksichtigt TVSDK nur die Profil 1, 2 und 3. Dadurch können Anwendungen an verschiedene Netzwerkbedingungen angepasst werden, z. B. an den Wechsel von Wi-Fi zu 3G oder zu verschiedenen Geräten wie einem Telefon, einem Tablet oder einem Desktop-Computer.

Führen Sie einen der folgenden Schritte aus, um ABR-Steuerungsparameter festzulegen:

* Verwenden Sie die Helper-Klasse `ABRControlParameterBuilder`, um eine beliebige Untergruppe der Parameter festzulegen (funktioniert hinter den Kulissen auf `ABRControlParameter`)

* Legen Sie die Parameter für die Klasse `ABRControlParameter` fest.

## Adaptive Bitraten mit ABRControlParametersBuilder {#section_3DDE397A7CE445E1832EBAA46CE5C069} konfigurieren

Die Verwendung der Helper-Klasse ist die einfachste und effizienteste Methode zum Festlegen von ABR-Parametern.`ABRControlParametersBuilder`

* Der Konstruktor `ABRControlParametersBuilder` stellt alle ABR-Parameter auf Standardwerte für das zugrunde liegende `ABRControlParameters`-Objekt ein.

* Sie können einzelne ABR-Parameter während der Laufzeit zurücksetzen, solange Sie einen Verweis auf dieselbe `ABRControlParametersBuilder`-Instanz beibehalten.

Diese Klasse enthält auch die Helper-Methode `toABRControlParameters()`. Verwenden Sie diese Methode, um eine Instanz von `ABRControlParameters` abzurufen und sie für die `mediaPlayer.ABRControlParameters`-Eigenschaft festzulegen. Dadurch werden Ihre Einstellungen im Player wirksam.

1. Instanziieren Sie die Helper-Klasse `ABRControlParametersBuilder` und legen Sie die Parameter für den Media Player fest.

   >[!NOTE]
   >
   >Im folgenden Beispiel werden alle Parameter auf die Standardwerte initialisiert, dann wird nur die Richtlinie auf konservativ eingestellt und die maximale Bitrate auf 1000000 beschränkt:
   >
   >
   ```
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```

1. Ändern Sie einzelne ABR-Parameter zur Laufzeit.

   So ändern Sie einzelne Parameter, während die übrigen Parameter unverändert bleiben:

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   Um Ihre vorherigen Einstellungen beizubehalten, müssen Sie einen Verweis auf dieselbe `ABRControlParametersBuilder`-Instanz beibehalten, die Sie in Schritt 1 erstellt haben.

## Adaptive Bitraten mit ABRControlParameters {#section_02161FD0A73F40ED9CAE17F9AF850483} konfigurieren

Sie können ABR-Steuerungswerte nur mit `ABRControlParameters` festlegen, aber Sie können jederzeit eine neue erstellen.

Diese Möglichkeit zum Festlegen von ABR-Parametern wurde vor dem Vorhandensein der `ABRControlParametersBuilder`-Klasse unterstützt, aber diese Fähigkeit ist zum Festlegen von ABR-Parametern zur Bauzeit noch immer effektiv. Um jedoch einzelne Parameter nach der Erstellung zu ändern, sollten Sie die `ABRControlParametersBuilder`-Klasse verwenden.

Die folgenden Bedingungen gelten für `ABRControlParameters`:

* Sie müssen Werte für alle Parameter zur Bauzeit angeben.
* Sie können nach der Bauzeit keine individuellen Werte mehr ändern.
* Wenn die von Ihnen angegebenen Parameter außerhalb des zulässigen Bereichs liegen, wird ein `ArgumentError` ausgelöst.

1. Entscheiden Sie sich für die anfänglichen, minimalen und maximalen Bitraten.
1. Legen Sie die ABR-Richtlinie fest:

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. Legen Sie die ABR-Parameterwerte im `ABRControlParameters`-Konstruktor fest und weisen Sie sie dem Media Player zu.

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```

