---
description: Sie können die folgenden Informationen verwenden, um Ihren Player zu entschlüsseln. Für jedes visuelle Konstrukt werden die entsprechenden Verhaltensweisen im Standardverhalten erwähnt.
title: Entschlüsseln des Players
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# Entschlüsseln des Players {#skinning-the-player}

Sie können die folgenden Informationen verwenden, um Ihren Player zu entschlüsseln. Für jedes visuelle Konstrukt werden die entsprechenden Verhaltensweisen im Standardverhalten erwähnt.

>[!IMPORTANT]
>
>Die Entschlüsselungsdetails in diesem Dokument beziehen sich auf die standardmäßigen Elemente der Benutzeroberfläche, die vom UI-Framework erstellt werden. Wenn Ihr Player diese Elemente geändert hat, müssen auch die Skinnelemente geändert werden.

## Container-Divs {#section_99B0D598219D4150B57E97D5381B118F}

Hier finden Sie die Stile für Container-Divs:

>[!TIP]
>
>Diese Divs werden im `common-styles.css` -Datei.

Hier finden Sie die Stile für die div-Hauptversion:

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
   <td colname="col2"> <p>Der Stil des Hauptdiv, in dem das Video wiedergegeben wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .pip-mode-active</span> </td> 
   <td colname="col2"> <p>Wird verwendet, wenn der PIP-Modus aktiv ist. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> videoBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Bild-im-Bild-Modus (PIP)</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-pip-video-div</span> </td> 
   <td colname="col2"> <p>Der Stil des Div, in dem PIP-Videos wiedergegeben werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .view-as-main-video</span> </td> 
   <td colname="col2"> <p>Wird auf die ursprüngliche PIP angewendet, wenn sie getauscht wurde, und wird als Hauptvideo angezeigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Multi-Video-Ansicht</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-view-container</span> </td> 
   <td colname="col2"> <p>Wird in der Multivideo-Ansicht verwendet. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-view</span> </td> 
   <td colname="col2"> <p>Ein gängiger CSS-Stil, der auf jedem Video in der Multiansicht platziert wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multiview</span> </td> 
   <td colname="col2"> <p>Wenn sich der Container, in dem jedes der Videos in der Multiansicht gespeichert ist, in einer Multiansicht befindet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Verschiedene Steuerelemente {#section_E9E4A8E3AEBF4BDC89840B84B3B0E737}

Hier finden Sie die Stile für allgemeine Player-Steuerelemente:

>[!TIP]
>
>Diese Stile werden im `default-controls.css` -Datei.

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
   <td colname="col2"> <p>Gilt für alle Steuerungen auf der Steuerleiste mit Ausnahme von Scrubber und Leerraum </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-input-regler</span> </td> 
   <td colname="col2"> <p>Eingangsregler </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-header</span> </td> 
   <td colname="col2"> <p>Kopfzeile der Bedienfelder </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-vertical-list-menu-item</span> </td> 
   <td colname="col2"> <p>Menüliste im vertikalen Stil </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-fill-Abstand</span> </td> 
   <td colname="col2"> <p>Platz in der Steuerleiste </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-hr-separator</span> </td> 
   <td colname="col2"> <p>Horizontales Regeltrennzeichen </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-title</span> </td> 
   <td colname="col2"> <p>Titel der Bedienfelder </p> </td> 
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

## Kontrollleiste {#section_B683B51EC746484B9AA90CB481D637BD}

Hier finden Sie die Stile für die Steuerleiste:

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
   <td colname="col1"><span class="codeph"> ptp-rubb-bar</span> </td> 
   <td colname="col2"> <p>Scrubbing-Leiste auf der Steuerleiste </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-rubb-bar .ptp-buffer-progress-bar</span> </td> 
   <td colname="col2"> <p>Pufferfortschrittsleiste auf der Scrubbing-Leiste </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-rubb-bar .ptp-search-to-bar</span> </td> 
   <td colname="col2"> <p>Status der Scrubbing-Leiste, wenn der Benutzer darauf sucht </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-rubb-bar .ptp-play-progress-bar</span> </td> 
   <td colname="col2"> <p>Status der Scrubbing-Leiste in normaler Wiedergabe </p> </td> 
  </tr>
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-rubb-bar .ptp-progress-bar-play-head</span> </td>
   <td colname="col2"> <p>Abspielen des Kopfes auf der Scrubbing-Leiste während der Wiedergabe </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-rubb-bar .ptp-ad-marker-bar</span> </td>
   <td colname="col2"> <p>Anzeigenmarkierungsleiste </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-rubb-bar .ptp-ad-marker</span> </td>
   <td colname="col2"> <p>Anzeigenmarkierung </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet:

* `scrubBarBehavior`
* `bufferProgressBarBehavior`
* `playHeadBehavior`
* `playProgressBarBehavior`
* `seekToBarBehavior`

## Wiedergabe-/Pause-Schaltfläche {#section_F1F40A948D0049C5A4D8EA5F2A475CAA}

Hier finden Sie die Stile für die Wiedergabe/Pause-Schaltfläche:

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
   <td colname="col2"> <p>Schaltfläche "Pause abspielen"in der Steuerleiste. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-btn-playpause</span> im Pausenstatus </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td> 
   <td colname="col2"> <p><span class="codeph"> ptp-btn-playpause</span> im Wiedergabestatus </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet `playPauseButtonBehavior`.

## Lautstärke {#section_23E17BD2343948F8A2CEE1C8BEE2F874}

Im Folgenden finden Sie die Stile zum Konfigurieren der Lautstärkeschaltfläche:

<table id="table_8F9831F36A4D427CA31C9FFA4173170D">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil (C) </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><span class="codeph"> .ptp-Volume-control</span>
     <ul id="ul_B12ADDFB83EA40FD8B4E92AF418AA4B4">
      <li id="li_7DA8143A69ED4E7D8A560B9FF75D6BA7"><span class="codeph"> .extended</span> </li>
      <li id="li_D8CCAD45D81C4850B6903FE261833AE6"><span class="codeph"> .vertical</span> </li>
     </ul> </p> </td>
   <td colname="col2"> <p>Lautstärkeregelung für Steuerleiste
     <ul id="ul_2C60F018FDCB458885738AC378C02F61">
      <li id="li_6B19572B504A4BBF9C97DC29C0E92A1D">Wenn das Steuerelement in erweiterter Form ist </li>
      <li id="li_6489E422E1944D5194CBDFC8383D2F30">Wenn die Steuerung in vertikaler Form ist </li>
     </ul> </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volumen</span> </td>
   <td colname="col2"> <p>Lautstärkeschaltfläche in der Steuerleiste </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volumen.min-volumen-state</span> </td>
   <td colname="col2"> <p>Wenn die Lautstärke den Mindestzustand aufweist </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volumen.mute-state</span> </td>
   <td colname="col2"> <p>Wenn die Lautstärke stummgeschaltet ist </p> </td>
  </tr>
 </tbody>
</table>

Die Standardverhaltensweisen sind `volumeBehavior` und `muteButtonBehavior`.

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
   <td colname="col1"><span class="codeph"> .ptp-Volume-hidden</span> </td>
   <td colname="col2"> <p>Der Lautstärkeregler befindet sich in einem ausgeblendeten Zustand. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet `volumeSliderBehavior`.

## Zurückspulen {#section_06EE608FC54A4CF5B5DF9DC743CFC740}

Hier finden Sie den Stil der Zurückspulschaltfläche:

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
   <td colname="col2"> <p>Die Zurückspultaste auf der Steuerleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet `rewindButtonBehavior`.

## Zeit {#section_0E6549B3DF6D4C10947D445A5F8EEA7F}

Im Folgenden finden Sie den Stil zum Anzeigen der verbleibenden Zeit in der Steuerleiste:

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
   <td colname="col2"> <p>Zeigt die verbleibende Zeit in der Symbolleiste an </p> </td>
  </tr>
</tbody>
</table>

Das Standardverhalten lautet `timeRemainingBehavior`.

## Schneller Rücklauf {#section_F6E6C65BD3BD493A89915DF9B92933BA}

Hier finden Sie den Stil für die Schaltfläche zum schnellen Zurückspulen:

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
   <td colname="col2"> <p>Die schnelle Rückspultaste auf der Steuerleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet `fastRewindButtonBehavior`.

## Langsame Rückspaltung {#section_38A22BB8681B430F8C6808C3BD21FB4E}

Hier finden Sie den Stil für die Schaltfläche &quot;Langsames Zurückspulen&quot;:

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
   <td colname="col2"> <p>Die langsame Zurückspultaste auf der Steuerleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet `slowRewindButtonBehavior`.

## Langsam vorwärts {#section_92ACF092EECC4A5EAF6AA090C05E552E}

Hier finden Sie den Stil für die Schaltfläche &quot;Langsam vorwärts&quot;:

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
   <td colname="col2"> <p>Die Schaltfläche "Langsames Vorwärts"in der Steuerleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet `slowForwardButtonBehavior`.

## Schneller Vorwärts {#section_F90ED8B3739B49ACAB1F12DF18F0E4D6}

Hier finden Sie den Stil für die Schaltfläche &quot;Fast Forward&quot;:

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
   <td colname="col2"> <p>Die Vorwärtsschaltfläche auf der Steuerleiste. </p> </td>
  </tr>
 </tbody>
</table>

Das Standardverhalten lautet `fastForwardButtonBehavior`.

## Audiospur {#section_1CDF4FA5A1C14DB6B9C96579FFA1057C}

Im Folgenden finden Sie die Stile zum Konfigurieren des Audio-Tracks:

<table id="table_22FC521D786B45EB84F230894FFECE79">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil </th> 
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Schaltfläche "Audio-Track"(K)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-audio-track</span> </td>
   <td colname="col2"> <p>Die Schaltfläche für den Audio-Track in der Steuerleiste. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> audioTrackButtonBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Auswahlbereich für Audiospuren (L)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-panel</span> </td> 
   <td colname="col2"> <p>Das Bedienfeld zur Auswahl des Audiotracks. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> audioTrackSelectionPanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Kopfzeile zur Audiospur-Auswahl (M)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>Die Kopfzeile für die <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Menü zur Auswahl von Audiospuren (N)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-menu</span> </td>
   <td colname="col2"> <p>Die Menüpunkte in <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
 </tbody>
</table>

## Freigabe {#section_B2ADC76E76304A68AD648A00A12B676E}

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
   <td colname="col1"> <p><b>Social-Media-Freigabe-Schaltfläche (O)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video</span> </td> 
   <td colname="col2"> <p>Die Schaltfläche Social-Media-Freigabe in der Symbolleiste, die geöffnet wird <span class="codeph"> ptp-share-video-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> shareVideoButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Freigeben des Videobereichs (P)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel</span> </td>
   <td colname="col2"> <p>Der Bereich, in dem die Social-Sharing-Optionen angezeigt werden. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> shareVideoPanelBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Menü "Freigeben von Videos"(Q)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>Die Kopfzeile für die <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .share-video-panel-menu</span> </td>
   <td colname="col2"> <p>Das Menü in <span class="codeph"> ptp-share-video-panel</span> , das alle Optionen zum Freigeben von Inhalten in sozialen Medien anzeigt. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel-menu-item</span> </td>
   <td colname="col2"> <p>Das Menüelement im <span class="codeph"> share-video-panel-menu</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-facebook</span> </td>
   <td colname="col2"> <p>Das Menüelement, über das Sie Inhalte in Facebook freigeben können. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-twitter</span> </td>
   <td colname="col2"> <p>Das Menüelement, mit dem Sie Inhalte auf Twitter freigeben können. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-google-plus</span> </td>
   <td colname="col2"> <p>Das Menüelement, über das Sie Inhalte auf Google Plus freigeben können. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-linkedin</span> </td>
   <td colname="col2"> <p>Das Menüelement, über das Sie Inhalte in LinkedIn freigeben können. </p> </td>
  </tr>
 </tbody>
</table>

## Geschlossene Untertitel {#section_A01BA68218564DA0B7D6BF51F045D7AB}

Hier finden Sie die Stile zum Konfigurieren von Untertiteln:

<table id="table_777C7034C9424F8C841DABD480FFAC47">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stil </th>
   <th colname="col2" class="entry"> Beschreibung </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Schaltfläche "Geschlossene Untertitel"(R)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-closed-caption</span> </td>
   <td colname="col2"> <p>Die <span class="uicontrol"> Geschlossene Untertitel</span> in der Symbolleiste. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> closedCaptionButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .on-state</span> </td>
   <td colname="col2"> <p>Die Untertitel wurden für ein Video aktiviert. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Bedienfeld "Geschlossene Untertitel"(S)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-panel</span> </td>
   <td colname="col2"> <p>Der Bereich für geschlossene Untertitel. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> closedCaptionLanguagePanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Sprachen mit verdeckten Untertiteln (T)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-language-panel:</span> </td>
   <td colname="col2"> <p>Die Kopfzeile für die <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-language-menu: </span> </td>
   <td colname="col2"> <p>Das Menü im Bedienfeld "Untertitel". </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Optionen für geschlossene Untertitel (U)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-btn</span> </td>
   <td colname="col2"> <p>Die <span class="uicontrol"> Optionen</span> im Optionsfeld "Untertitel schließen". </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-panel</span> </td>
   <td colname="col2"> <p>Das Bedienfeld "Optionen"im Bedienfeld "Untertitel". </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-menu-item</span> </td>
   <td colname="col2"> <p>Das Menüelement im Bedienfeld "Untertitel". </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .selected</span> </td>
   <td colname="col2"> <p>Im ausgewählten Status. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-done-btn</span> </td> 
   <td colname="col2"> <p>Die <span class="uicontrol"> Fertig</span> in der Kopfzeile des Optionsfelds "Untertitel". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-menu</span> </td> 
   <td colname="col2"> <p>Das Menü Optionen in geschlossenen Untertiteln. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-main-menu</span> </td> 
   <td colname="col2"> <p>Das Hauptmenü für die Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-sub-menu</span> </td> 
   <td colname="col2"> <p>Das Untermenü für die Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-opacity-regler</span> </td> 
   <td colname="col2"> <p>Der Deckkraft-Regler für Optionen für geschlossene Beschriftungen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-menu-separator</span> </td> 
   <td colname="col2"> <p>Trennzeichen für Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-menu-item</span> </td> 
   <td colname="col2"> <p>Die geschlossene Beschriftung <span class="uicontrol"> Optionen</span> Menüelement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-preview-panel</span> </td> 
   <td colname="col2"> <p>Das Vorschaufenster für geschlossene Beschriftungen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-footer</span> </td> 
   <td colname="col2"> <p>Die Fußzeile für Untertiteloptionen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-reset-button</span> </td> 
   <td colname="col2"> <p>Die <span class="uicontrol"> Zurücksetzen</span> in der Fußzeile des Bereichs mit Optionen für geschlossene Beschriftungen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-apply-button</span> </td> 
   <td colname="col2"> <p>Die <span class="uicontrol"> Anwenden</span> in der Fußzeile des Bereichs mit Optionen für geschlossene Beschriftungen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> closedCaptionOptionsPanelBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## Weitere Optionen (V) {#section_18E25CF8A8964FFD9026A8A833089CE3}

Im Folgenden finden Sie die Stile zum Konfigurieren zusätzlicher Optionen:
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
   <td colname="col2"> <p>Die <span class="uicontrol"> Weitere Optionen</span> Schaltfläche. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-more-options.ptp-control-bar-btn</span> </td> 
   <td colname="col2"> <p>Die <span class="codeph"> ptp-btn-more-options</span> die in der Steuerleiste verwendet werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel</span> </td> 
   <td colname="col2"> <p>Das Control Panel Weitere Optionen . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu</span> </td> 
   <td colname="col2"> <p>Das Menü des Control Panels Mehr Optionen . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu-item</span> </td> 
   <td colname="col2"> <p>Das Menüelement Mehr Optionen im Control Panel . </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten lautet `moreOptionsButtonBehavior`.

## PIP-Schaltfläche (W) {#section_1EE039DEA99541D391B30BD1DF72A83E}

Hier finden Sie den Stil für die [!UICONTROL PIP<] Schaltfläche:

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
   <td colname="col2"> <p>Die PIP-Schaltfläche in der Symbolleiste. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> pipButtonBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## Vollbild (X) {#section_158A19DFB30E4432A67E4A74A7CBA563}

Hier finden Sie den Stil zum Konfigurieren des Vollbildmodus:

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
   <td colname="col2"> <p>Die <span class="uicontrol"> Vollbild</span> in der Steuerleiste. </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten lautet `fullScreenButtonBehavior`.

## Trick Play (Y) {#section_AE6F83BB7EE2497FB13CD94A8316192D}

Hier finden Sie den Stil zum Konfigurieren der Trickwiedergabe:

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
   <td colname="col2"> <p>Die Komponente zur Anzeige der Trickrate in der Steuerleiste. </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten lautet `trickPlayRateDisplayBehavior`.

## Multiview (Z) {#section_58EFAE7263BA45D3A4E2AB7309A9CAA7}

Hier finden Sie den Stil zum Konfigurieren der Multiansicht:

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
   <td colname="col2"> <p>Die <span class="uicontrol"> MultiView</span> Schaltfläche in der Steuerleiste und der Anfangsstatus von <span class="uicontrol"> Multiview</span> Schaltfläche. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Das Standardverhalten lautet <span class="codeph"> multiViewButtonBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
 </tbody> 
</table>

## Miniatur {#section_0AFD932975634BB08387EEE7D3BFC438}

Hier finden Sie den Stil zum Konfigurieren von Miniaturansichten:

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
   <td colname="col2"> <p>Der Fortschrittsbalken der Miniaturansichten. </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten lautet `thumbnailPreviewBehavior`.

## Fehlermeldungen {#section_AC9858EE1B5A4FF4947E383C663B6AB5}

Hier finden Sie den Stil zum Konfigurieren von Fehlermeldungen:

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
   <td colname="col2"> <p>Das Bedienfeld, in dem die Fehlermeldungen vom Player angezeigt werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-icon</span> </td> 
   <td colname="col2"> <p>Das Symbol, das im Bereich angezeigt wird, wenn eine Fehlermeldung vorliegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-message</span> </td> 
   <td colname="col2"> <p>Die angezeigte Fehlermeldung. </p> </td> 
  </tr> 
 </tbody> 
</table>

Das Standardverhalten lautet `errorMessagePanelBehavior`.

## Pufferüberlagerung {#section_2FE8FDE2599E42BAA7411D0D38FA0A88}

Hier finden Sie den Stil zum Konfigurieren von Miniaturansichten:

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
   <td colname="col2"> <p>Das Steuerelement für Pufferüberlagerungen. </p> </td> 
  </tr> 
 </tbody> 
</table>

Die standardmäßige Überlagerung ist `bufferingOverlayBehavior`.

## Spezifische Selektoren {#section_51F735AEF82E41E890FF59E031A0DB89}

Hier finden Sie den Stil für die Schaltfläche &quot;Fast Forward&quot;:

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
   <td colname="col2"> <p>Der Status des Control Panels während der Anzeige. </p> <p>Gilt für Folgendes: 
     <ul id="ul_D5076303DCD94D968682289823D1A9F2"> 
      <li id="li_4290C4B2D48546E3AD023BED6CAAE395"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_72A3D3E916E44A55BA170407EAB0527D"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_A0BAEBB0E01B402EB83E3CE9B92B15CC"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_FDF2CEDB0A854098907FF9CBCF1A61C1"><span class="codeph"> .ptp-btn-slow-forward</span> </li> 
      <li id="li_CD2E14DB3DD64C10A253DA23FBE04A04"><span class="codeph"> .ptp-btn-slow-forward</span> </li> 
      <li id="li_A230359E8F7F4571A9EBFF0E4C2462D7"><span class="codeph"> .ptp-btn-slowRewind</span> </li> 
      <li id="li_5711A315872F4FA59FDDF0EF0AFD03C6"><span class="codeph"> .ptp-btn-more-options </span> </li> 
      <li id="li_71C8E76077A84ED590160AB5ABFCC0D7"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_4A3113C0360F4F708AAA96AB316FA057"><span class="codeph"> .ptp-btn-closed-caption </span> </li> 
      <li id="li_901A0186D65A48A1B774DC555CEC5367"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
      <li id="li_2331583C01C2482B8EE72979FBF111DB"><span class="codeph"> .ptp-btn-pip </span> </li> 
      <li id="li_7BB39BDF5E294AEB8FA3DCD9F9A29468"><span class="codeph"> .ptp-btn-rewind</span> </li> 
      <li id="li_E4FEF5A7486A40F6A5FE1119BD63AFEF"><span class="codeph"> .ptp-rubb-bar</span> </li> 
      <li id="li_12153547558A4871842EE0416BCCA8B2"><span class="codeph"> .ptp-search-to-bar</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multi-view</span> </td> 
   <td colname="col2"> <p>Der Status des Steuerelements während der Multiansicht. </p> <p>Gilt für Folgendes: 
     <ul id="ul_A8AC653C30814AC49041F3B58A2106F4"> 
      <li id="li_0407167DA21647A8A6960DFE55A33F42"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_EA71CAF41CDC41DE859A85CE482BE97C"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_F3A998C51A034C22A914EAEFF19FFEA7"><span class="codeph"> .ptp-btn-closed-caption</span> </li> 
      <li id="li_022F871ABC894C9BA879B3AF3D341202"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .fullscreen-state</span> </td> 
   <td colname="col2"> <p>Der Player befindet sich im Vollbildmodus. </p> <p>Gilt für Folgendes: 
     <ul id="ul_B235C1D339F64B2FAC6BC72F03807616"> 
      <li id="li_6E050EE74C604FDAB4C9C0447F547A9D"><span class="codeph"> .ptp-control-bar </span> </li> 
      <li id="li_67D54B1A41764B2DA544479CDA1C901C"><span class="codeph"> .ptp-btn-fullscreen</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
