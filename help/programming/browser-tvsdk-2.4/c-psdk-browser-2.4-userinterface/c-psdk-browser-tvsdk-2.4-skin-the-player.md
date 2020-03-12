---
description: Mithilfe der folgenden Informationen können Sie Ihren Player per Skin gestalten. Für jedes visuelle Konstrukt werden die entsprechenden Verhaltensweisen im Standardverhalten erwähnt.
seo-description: Mithilfe der folgenden Informationen können Sie Ihren Player per Skin gestalten. Für jedes visuelle Konstrukt werden die entsprechenden Verhaltensweisen im Standardverhalten erwähnt.
seo-title: Entwerfen des Players
title: Entwerfen des Players
uuid: 516ff846-d76d-4062-b64b-3032f7a70470
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Entwerfen des Players {#skinning-the-player}

Mithilfe der folgenden Informationen können Sie Ihren Player per Skin gestalten. Für jedes visuelle Konstrukt werden die entsprechenden Verhaltensweisen im Standardverhalten erwähnt.

>[!IMPORTANT]
>
>Die Skin-Details in diesem Dokument beziehen sich auf die Standardelemente der Benutzeroberfläche, die vom UI-Framework erstellt werden. Wenn Ihr Player diese Elemente geändert hat, müssen auch die Skin-Elemente geändert werden.

## Container-Divs {#section_99B0D598219D4150B57E97D5381B118F}

Hier finden Sie die Stile für die Container-Divs:

>[!TIP]
>
>Diese divs werden in der `common-styles.css` Datei aufgeführt.

Im Folgenden finden Sie die Stile für das div-Hauptformat:

<table id="table_AC5745DF725543ADBBCD68BA6130DF12"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Hauptdiv</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-main-video-div-style</span> </td> 
   <td colname="col2"> <p>Der Stil des div-Hauptvideos, in dem Videos wiedergegeben werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .pip-mode-active</span> </td> 
   <td colname="col2"> <p>Wird verwendet, wenn der PIP-Modus aktiv ist. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> videoBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Picture in Picture (PIP)</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-pip-video-div</span> </td> 
   <td colname="col2"> <p>Der Stil des div, in dem PIP-Videos wiedergegeben werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .Ansicht-as-main-video</span> </td> 
   <td colname="col2"> <p>Wird auf das ursprüngliche PIP angewendet, wenn es getauscht wurde und als Hauptvideo angezeigt wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Ansicht für mehrere Videos</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-Ansicht-Container</span> </td> 
   <td colname="col2"> <p>Wird in der Ansicht für mehrere Videos verwendet. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-Ansicht-Ansicht</span> </td> 
   <td colname="col2"> <p>Ein gewöhnlicher CSS-Stil, der auf jedem Video in der Multiansicht platziert wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multiview</span> </td> 
   <td colname="col2"> <p>Wenn der Container, in dem sich die Videos in einem Multiview befinden, in einem Multiview angezeigt wird. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Verschiedene Steuerelemente {#section_E9E4A8E3AEBF4BDC89840B84B3B0E737}

Im Folgenden finden Sie die Stile für allgemeine Player-Steuerelemente:

>[!TIP]
>
>Diese Stile werden in der `default-controls.css` Datei aufgeführt.

<table id="table_0ACB6BAB5DAD42DBBD18CA7C0385A261"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-control</span> </td> 
   <td colname="col2"> <p>Gilt für alle Steuerungen auf der Steuerleiste mit Ausnahme von Gummi und Leerzeichen </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-input-regler</span> </td> 
   <td colname="col2"> <p>Einzugsregler </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-header</span> </td> 
   <td colname="col2"> <p>Kopfzeile der Bedienfelder </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-vertical-Liste-menu-item</span> </td> 
   <td colname="col2"> <p>Menü-Liste im vertikalen Stil </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-fill-Platzhalter</span> </td> 
   <td colname="col2"> <p>Leerzeichen in der Steuerleiste </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-hr-separator</span> </td> 
   <td colname="col2"> <p>Horizontales Regeltrennzeichen </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-title</span> </td> 
   <td colname="col2"> <p>Titel der Bereiche </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-close-btn</span> </td> 
   <td colname="col2"> <p>Schaltfläche zum Schließen des Bedienfelds </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-button-background</span> </td> 
   <td colname="col2"> <p>Hintergrund aller Schaltflächen </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-txt-control</span> </td> 
   <td colname="col2"> <p>Standardstile für Textsteuerelemente. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Steuerungsleiste {#section_B683B51EC746484B9AA90CB481D637BD}

Die folgenden Stile gelten für die Steuerungsleiste:

<table id="table_681E13F264674F849FAA2523EB65F094"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-control-bar</span> (Standardverhalten)</td>
   <td colname="col2"> <p>Gilt für die Steuerleiste </p> </td> 
  </tr> 
 </tbody> 
</table>

## Funktionsschaltflächen {#section_57FFD242FF674EA2867BCF6CA7F6B855}

>[!NOTE]
>
>Die Buchstaben in den folgenden Tabellen entsprechen den Buchstaben in dieser Abbildung.

Hier finden Sie die Stile für die Scrubbing-Leiste:

<table id="table_2207AD72E72A47FFA03AC748F06A54FD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil (A) </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-crub-bar</span> </td> 
   <td colname="col2"> <p>Navigationsleiste auf der Steuerleiste </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-crub-bar .ptp-buffer-progress-bar</span> </td> 
   <td colname="col2"> <p>Pufferfortschrittsleiste auf der Scrubbing-Leiste </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-crub-bar .ptp-search-to-bar</span> </td> 
   <td colname="col2"> <p>Status der Scrubbing-Leiste, wenn der Benutzer danach sucht </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-crubbing-bar .ptp-play-progress-bar</span> </td> 
   <td colname="col2"> <p>Status der Scrubbing-Leiste bei normaler Wiedergabe </p> </td> 
  </tr>
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-crubbing-bar .ptp-progress-bar-play-head</span> </td>
   <td colname="col2"> <p>Abspielen von Kopf auf Scrubbing-Leiste während der Wiedergabe </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-crubbing-bar .ptp-ad-marker-bar</span> </td>
   <td colname="col2"> <p>Anzeigenmarkierungsleiste </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-crubbing-bar .ptp-ad-marker</span> </td>
   <td colname="col2"> <p>Anzeigenmarke </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet:

* `scrubBarBehavior`
* `bufferProgressBarBehavior`
* `playHeadBehavior`
* `playProgressBarBehavior`
* `seekToBarBehavior`

## Schaltfläche &quot;Abspielen/Anhalten&quot; {#section_F1F40A948D0049C5A4D8EA5F2A475CAA}

Hier finden Sie die Stile für die Schaltfläche &quot;Abspielen/Anhalten&quot;:

<table id="table_975C2293222A4782A8C75A6149C1AD27">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (B) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause</span> </td>
   <td colname="col2"> <p>Schaltfläche zum Abspielen der Pause in der Steuerungsleiste. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-btn-playpause</span> im Pausenzustand </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td> 
   <td colname="col2"> <p><span class="codeph"> ptp-btn-playpause</span> im Abspielstatus </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten ist `playPauseButtonBehavior`.

## Volumen {#section_23E17BD2343948F8A2CEE1C8BEE2F874}

Im Folgenden finden Sie die Stile zum Konfigurieren der Schaltfläche &quot;Lautstärke&quot;:

<table id="table_8F9831F36A4D427CA31C9FFA4173170D">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (C) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><span class="codeph"> .ptp-volume-control</span>
     <ul id="ul_B12ADDFB83EA40FD8B4E92AF418AA4B4">
      <li id="li_7DA8143A69ED4E7D8A560B9FF75D6BA7"><span class="codeph"> .extended</span> </li>
      <li id="li_D8CCAD45D81C4850B6903FE261833AE6"><span class="codeph"> .vertical</span> </li>
     </ul> </p> </td>
   <td colname="col2"> <p>Lautstärkeregler in der Steuerleiste
     <ul id="ul_2C60F018FDCB458885738AC378C02F61">
      <li id="li_6B19572B504A4BBF9C97DC29C0E92A1D">Wenn die Steuerung im erweiterten Formular vorliegt </li>
      <li id="li_6489E422E1944D5194CBDFC8383D2F30">Wenn Steuerelement in vertikaler Form </li>
     </ul> </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-Volume</span> </td>
   <td colname="col2"> <p>Lautstärkeschaltfläche in der Steuerungsleiste </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume.min-volume-state</span> </td>
   <td colname="col2"> <p>Bei Volumen im Minimalzustand </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume.mute-state</span> </td>
   <td colname="col2"> <p>Wenn die Lautstärke im Stummzustand ist </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet `volumeBehavior` und `muteButtonBehavior`.

Hier finden Sie die Stile für den Lautstärkeregler:

<table id="table_E3DC93F8FC614C30AADAE259D18F10EF">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (D) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-Volume-Regler</span> </td>
   <td colname="col2"> <p>Der Lautstärkeregler. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-volume-hidden</span> </td>
   <td colname="col2"> <p>Der Lautstärkeregler im ausgeblendeten Status. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten ist `volumeSliderBehavior`.

## Zurückspulen {#section_06EE608FC54A4CF5B5DF9DC743CFC740}

Der Stil für die Schaltfläche &quot;Zurückspulen&quot;lautet:

<table id="table_0ACB116582D54B188E9F5B5C03D3A615">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (E) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>Die Zurückspultaste auf der Steuerungsleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten ist `rewindButtonBehavior`.

## Zeit {#section_0E6549B3DF6D4C10947D445A5F8EEA7F}

Hier ist der Stil zum Anzeigen der verbleibenden Zeit in der Steuerungsleiste:

<table id="table_CEE62BFF5FB04FDCBBE1331E0D727EBA">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (F) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-txt-display-time</span> </td>
   <td colname="col2"> <p>Zeigt die verbleibende Zeit in der Steuerungsleiste an </p> </td>
  </tr>
</tbody>
</table>

Das Standardverhalten ist `timeRemainingBehavior`.

## Schnelles Zurückspulen {#section_F6E6C65BD3BD493A89915DF9B92933BA}

Hier ist der Stil für die Taste zum schnellen Zurückspulen:

<table id="table_25BB4966B709402383AB6A6822FC1999">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (G) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>Die Taste zum schnellen Zurückspulen auf der Steuerleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten ist `fastRewindButtonBehavior`.

## Langsamer Rücklauf {#section_38A22BB8681B430F8C6808C3BD21FB4E}

Hier ist der Stil für die Schaltfläche &quot;Langsames Zurückspulen&quot;:

<table id="table_E623C374622A497C91E22333D77AF8F6">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (H) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slowRewind</span> </td>
   <td colname="col2"> <p>Die langsame Zurückspultaste auf der Steuerungsleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten ist `slowRewindButtonBehavior`.

## Vorwärts langsam {#section_92ACF092EECC4A5EAF6AA090C05E552E}

Hier ist der Stil für die Schaltfläche &quot;Langsam vorwärts&quot;:

<table id="table_88C1CF5DB2D84EDBA01AC62B70509B08">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (I) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slow-forward</span> </td>
   <td colname="col2"> <p>Die Schaltfläche "Langsam vorwärts"in der Steuerungsleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten ist `slowForwardButtonBehavior`.

## Schnelle Weiterleitung {#section_F90ED8B3739B49ACAB1F12DF18F0E4D6}

Hier ist der Stil für die Schaltfläche &quot;Vorwärts schnell&quot;:

<table id="table_F166BD1E8B934B34AF3690BBBAD894B7">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (J) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastforward</span> </td>
   <td colname="col2"> <p>Die Schaltfläche "Vorwärts schnell"auf der Steuerleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten ist `fastForwardButtonBehavior`.

## Audiospur {#section_1CDF4FA5A1C14DB6B9C96579FFA1057C}

Im Folgenden finden Sie die Stile zum Konfigurieren der Audiospur:

<table id="table_22FC521D786B45EB84F230894FFECE79">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Schaltfläche "Audiospur"(K)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-audio-track</span> </td>
   <td colname="col2"> <p>Die Schaltfläche für die Audiospur in der Steuerungsleiste. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> audioTrackButtonBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Auswahl der Audiospur (L)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-panel</span> </td> 
   <td colname="col2"> <p>Das Bedienfeld zur Auswahl der Audiospur. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> audioTrackSelectionPanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Kopfzeile für Audiospur-Auswahl (M)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>Die Kopfzeile für das <span class="codeph"> Bedienfeld</span>"ptp-audio-track-selection-panel". </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Menü "Audiospur auswählen"(N)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-menu</span> </td>
   <td colname="col2"> <p>Die Menüelemente im <span class="codeph"> Bedienfeld</span>"ptp-audio-track-selection". </p> </td>
  </tr>
 </tbody>
</table>

## Freigeben {#section_B2ADC76E76304A68AD648A00A12B676E}

Hier finden Sie die Stile zum Konfigurieren der Freigabe:

<table id="table_3264C472809D462B8FC16680B96B1AC9">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Schaltfläche "Freigeben in sozialen Medien"(O)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video</span> </td> 
   <td colname="col2"> <p>Über die Schaltfläche "Freigeben in sozialen Medien"in der Steuerungsleiste wird das <span class="codeph"> Bedienfeld</span>"ptp-share-video"geöffnet. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> "shareVideoButtonBehavior"</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Freigeben des Videobedienfelds (P)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel</span> </td>
   <td colname="col2"> <p>Der Bereich, in dem die Optionen für Social Sharing angezeigt werden. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> "shareVideoPanelBehavior"</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Menü "Freigeben von Videos"(Q)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>Die Kopfzeile für das <span class="codeph"> Bedienfeld</span>"ptp-audio-track-selection-panel". </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .share-video-panel-menu</span> </td>
   <td colname="col2"> <p>Das Menü im <span class="codeph"> Bedienfeld</span> "ptp-share-video", das alle Optionen zum Freigeben von Inhalten in sozialen Medien anzeigt. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel-menu-item</span> </td>
   <td colname="col2"> <p>Das Menüelement im Menü des <span class="codeph"> Freigabe-Video-Bedienfelds</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-facebook</span> </td>
   <td colname="col2"> <p>Das Menüelement, mit dem Sie Inhalte auf Facebook freigeben können. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-twitter</span> </td>
   <td colname="col2"> <p>Das Menüelement, mit dem Sie Inhalte auf Twitter freigeben können. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-google-plus</span> </td>
   <td colname="col2"> <p>Das Menüelement, mit dem Sie Inhalte auf Google Plus freigeben können. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-linkedin</span> </td>
   <td colname="col2"> <p>Das Menüelement, mit dem Sie Inhalte auf LinkedIn freigeben können. </p> </td>
  </tr>
 </tbody>
</table>

## Untertitel {#section_A01BA68218564DA0B7D6BF51F045D7AB}

Im Folgenden finden Sie die Stile zum Konfigurieren von Untertiteln:

<table id="table_777C7034C9424F8C841DABD480FFAC47">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Schaltfläche "Untertitel"(R)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-close-caption</span> </td>
   <td colname="col2"> <p>Die Schaltfläche " <span class="uicontrol"> Untertitel</span> "in der Steuerungsleiste. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> closeCaptionButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .on-Status</span> </td>
   <td colname="col2"> <p>Die Untertitel wurden für ein Video aktiviert. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Untertitel-Bedienfeld (S)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-panel</span> </td>
   <td colname="col2"> <p>Der Bereich für Untertitel. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> closeCaptionLanguagePanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Sprachen mit Untertiteln (T)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-language-panel:</span> </td>
   <td colname="col2"> <p>Die Kopfzeile für das <span class="codeph"> Bedienfeld</span>"ptp-audio-track-selection-panel". </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-language-menu: </span> </td>
   <td colname="col2"> <p>Das Menü im Untertitel-Bedienfeld. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Optionen für Untertitel (U)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-options-btn</span> </td>
   <td colname="col2"> <p>Die Schaltfläche " <span class="uicontrol"> Optionen</span> "im Optionsfeld "Untertitel". </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-options-panel</span> </td>
   <td colname="col2"> <p>Der Bereich "Optionen"im Bereich "Untertitel". </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-menu-item</span> </td>
   <td colname="col2"> <p>Das Menüelement im Untertitel-Bedienfeld. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .selected</span> </td>
   <td colname="col2"> <p>Im ausgewählten Status. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-done-btn</span> </td> 
   <td colname="col2"> <p>Die Schaltfläche " <span class="uicontrol"> Fertig</span> "in der Kopfzeile des Optionsfelds "Untertitel". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-close-caption-options-menu</span> </td> 
   <td colname="col2"> <p>Das Menü "Optionen"in Untertiteln. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-main-menu</span> </td> 
   <td colname="col2"> <p>Das Hauptmenü für die Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-sub-menu</span> </td> 
   <td colname="col2"> <p>Das Untermenü für die Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-opacity-regler</span> </td> 
   <td colname="col2"> <p>Der Schieberegler für die Deckkraft für Untertitel. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-menu-separator</span> </td> 
   <td colname="col2"> <p>Das Trennzeichen für Untertitel-Optionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-menu-item</span> </td> 
   <td colname="col2"> <p>Das Menüelement <span class="uicontrol"> "Untertiteloptionen</span> ". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-Vorschau-panel</span> </td> 
   <td colname="col2"> <p>Das Bedienfeld für die Vorschau von Bildunterschriften. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-footer</span> </td> 
   <td colname="col2"> <p>Die Fußzeile der Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-reset-button</span> </td> 
   <td colname="col2"> <p>Die Schaltfläche " <span class="uicontrol"> Zurücksetzen</span> "in der Fußzeile des Bereichs mit den Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-apply-button</span> </td> 
   <td colname="col2"> <p>Die Schaltfläche " <span class="uicontrol"> Anwenden</span> "in der Fußzeile des Bereichs mit den Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> closeCaptionOptionsPanelBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## Weitere Optionen (V) {#section_18E25CF8A8964FFD9026A8A833089CE3}

Hier sind die Stile zum Konfigurieren weiterer Optionen:
<table id="table_EC6EF88E2EDE4B8EBB1C14F87A6161FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-more-options</span> </td> 
   <td colname="col2"> <p>Die Schaltfläche <span class="uicontrol"> Mehr Optionen</span> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-more-options.ptp-control-bar-btn</span> </td> 
   <td colname="col2"> <p>Die <span class="codeph"> ptp-btn-more-Optionen</span> , die in der Steuerleiste verwendet werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel</span> </td> 
   <td colname="col2"> <p>Das Bedienfeld Mehr Optionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu</span> </td> 
   <td colname="col2"> <p>Das Bedienfeldmenü Mehr Optionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu-item</span> </td> 
   <td colname="col2"> <p>Das Menüelement Mehr Optionen im Bedienfeld. </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten ist `moreOptionsButtonBehavior`.

## PIP-Taste (W) {#section_1EE039DEA99541D391B30BD1DF72A83E}

Der Stil für die [!UICONTROL PIP<] Schaltfläche:

<table id="table_EE2E882C87E24D39B8D5347686F29E55"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-pip</span> </td> 
   <td colname="col2"> <p>Die PIP-Schaltfläche in der Steuerungsleiste. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> "pipButtonBehavior"</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## Vollbild (X) {#section_158A19DFB30E4432A67E4A74A7CBA563}

Im Folgenden finden Sie den Stil zum Konfigurieren des Vollbildschirms:

<table id="table_5941835F31AC4E9CBA9702AB8D813B8F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-fullscreen</span> </td> 
   <td colname="col2"> <p>Die Schaltfläche " <span class="uicontrol"> Vollbild</span> "in der Steuerungsleiste. </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten ist `fullScreenButtonBehavior`.

## Trick Play (Y) {#section_AE6F83BB7EE2497FB13CD94A8316192D}

Im Folgenden finden Sie den Stil zum Konfigurieren der Trick-Wiedergabe:

<table id="table_F1ADAC0A4B4E48669828690BDEB4BC09"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-control-bar-trick-play-rate</span> </td> 
   <td colname="col2"> <p>Die Komponente zur Darstellung der Trickrate in der Steuerungsleiste. </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten ist `trickPlayRateDisplayBehavior`.

## Multiview (Z) {#section_58EFAE7263BA45D3A4E2AB7309A9CAA7}

Im Folgenden finden Sie den Stil zum Konfigurieren der Mehrfachansicht:

<table id="table_84B37D7410EE40DFA7A8BB8431C6DCF0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-multiview</span> </td> 
   <td colname="col2"> <p>Die <span class="uicontrol"> Schaltfläche "MultiView</span> "in der Steuerleiste und der Anfangsstatus der Schaltfläche " <span class="uicontrol"> Multiview</span> ". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Das Standardverhalten ist <span class="codeph"> multiViewButtonBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
 </tbody> 
</table>

## Miniaturansicht {#section_0AFD932975634BB08387EEE7D3BFC438}

Im Folgenden finden Sie den Stil zum Konfigurieren von Miniaturansichten:

<table id="table_968136A8BBA042A7A8E79739B8F92F55"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-progress-bar-thumb-nail</span> </td> 
   <td colname="col2"> <p>Die Fortschrittsleiste der Miniaturansichten. </p> </td> 
  </tr> 
 </tbody> 
</table>

Die Standardeinstellung ist `thumbnailPreviewBehavior`das Standardverhalten.

## Fehlermeldungen {#section_AC9858EE1B5A4FF4947E383C663B6AB5}

Der folgende Stil dient zum Konfigurieren von Fehlermeldungen:

<table id="table_7F4C156170DB4AFFA7DEE06F00449506"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel</span> </td> 
   <td colname="col2"> <p>Der Bereich, in dem die Fehlermeldungen des Players angezeigt werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-icon</span> </td> 
   <td colname="col2"> <p>Das Symbol, das im Bereich angezeigt wird, wenn eine Fehlermeldung angezeigt wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-message</span> </td> 
   <td colname="col2"> <p>Die angezeigte Fehlermeldung. </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten ist `errorMessagePanelBehavior`.

## Pufferüberlagerung {#section_2FE8FDE2599E42BAA7411D0D38FA0A88}

Im Folgenden finden Sie den Stil zum Konfigurieren von Miniaturansichten:

<table id="table_1FECE1DC29B8434B886751A29455F004"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-buffering-overlay</span> </td> 
   <td colname="col2"> <p>Die Steuerung der Pufferüberlagerung. </p> </td> 
  </tr> 
 </tbody> 
</table>

Die Standardüberlagerung ist `bufferingOverlayBehavior`.

## Spezifische Selektoren {#section_51F735AEF82E41E890FF59E031A0DB89}

Hier ist der Stil für die Schaltfläche &quot;Vorwärts schnell&quot;:

<table id="table_E77EDC7D227348E79C7E73FB5D46F992"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ad-break</span> </td> 
   <td colname="col2"> <p>Der Status des Bedienfelds während der Wiedergabe der Anzeige. </p> <p>Gilt für Folgendes: 
     <ul id="ul_D5076303DCD94D968682289823D1A9F2"> 
      <li id="li_4290C4B2D48546E3AD023BED6CAAE395"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_72A3D3E916E44A55BA170407EAB0527D"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_A0BAEBB0E01B402EB83E3CE9B92B15CC"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_FDF2CEDB0A854098907FF9CBCF1A61C1"><span class="codeph"> .ptp-btn-slow-forward</span> </li> 
      <li id="li_CD2E14DB3DD64C10A253DA23FBE04A04"><span class="codeph"> .ptp-btn-slow-forward</span> </li> 
      <li id="li_A230359E8F7F4571A9EBFF0E4C2462D7"><span class="codeph"> .ptp-btn-slowRewind</span> </li> 
      <li id="li_5711A315872F4FA59FDDF0EF0AFD03C6"><span class="codeph"> .ptp-btn-more-options </span> </li> 
      <li id="li_71C8E76077A84ED590160AB5ABFCC0D7"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_4A3113C0360F4F708AAA96AB316FA057"><span class="codeph"> .ptp-btn-close-caption </span> </li> 
      <li id="li_901A0186D65A48A1B774DC555CEC5367"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
      <li id="li_2331583C01C2482B8EE72979FBF111DB"><span class="codeph"> .ptp-btn-pip </span> </li> 
      <li id="li_7BB39BDF5E294AEB8FA3DCD9F9A29468"><span class="codeph"> .ptp-btn-rewind</span> </li> 
      <li id="li_E4FEF5A7486A40F6A5FE1119BD63AFEF"><span class="codeph"> .ptp-crubbing-bar</span> </li> 
      <li id="li_12153547558A4871842EE0416BCCA8B2"><span class="codeph"> .ptp-search-to-bar</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multi-Ansicht</span> </td> 
   <td colname="col2"> <p>Der Status des Steuerelements während der Mehrfachansicht. </p> <p>Gilt für Folgendes: 
     <ul id="ul_A8AC653C30814AC49041F3B58A2106F4"> 
      <li id="li_0407167DA21647A8A6960DFE55A33F42"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_EA71CAF41CDC41DE859A85CE482BE97C"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_F3A998C51A034C22A914EAEFF19FFEA7"><span class="codeph"> .ptp-btn-close-caption</span> </li> 
      <li id="li_022F871ABC894C9BA879B3AF3D341202"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .fullscreen-Status</span> </td> 
   <td colname="col2"> <p>Der Player befindet sich im Vollbildmodus. </p> <p>Gilt für Folgendes: 
     <ul id="ul_B235C1D339F64B2FAC6BC72F03807616"> 
      <li id="li_6E050EE74C604FDAB4C9C0447F547A9D"><span class="codeph"> .ptp-control-bar </span> </li> 
      <li id="li_67D54B1A41764B2DA544479CDA1C901C"><span class="codeph"> .ptp-btn-fullscreen</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>