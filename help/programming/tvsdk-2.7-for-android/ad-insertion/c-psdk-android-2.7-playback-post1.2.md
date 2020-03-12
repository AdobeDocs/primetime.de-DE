---
description: Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten, schnellen Vor- oder Zurückspulen und Anzeigen beeinträchtigt.
seo-description: Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten, schnellen Vor- oder Zurückspulen und Anzeigen beeinträchtigt.
seo-title: Standard- und benutzerdefiniertes Wiedergabeverhalten mit Anzeigen
title: Standard- und benutzerdefiniertes Wiedergabeverhalten mit Anzeigen
uuid: 272cdfd0-799f-41e5-bf41-1620d48c992a
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Standard- und benutzerdefiniertes Wiedergabeverhalten mit Anzeigen{#default-and-customized-playback-behavior-with-ads}

Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten, schnellen Vor- oder Zurückspulen und Anzeigen beeinträchtigt.

Um das Standardverhalten zu überschreiben, verwenden Sie `AdBreakPolicySelector` .

>[!IMPORTANT]
>
>TVSDK bietet keine Möglichkeit, die Suche während der Anzeigen zu deaktivieren. Adobe empfiehlt, dass Sie Ihre Anwendung so konfigurieren, dass die Suche während der Anzeigen deaktiviert wird.

Hier ist das Wiedergabeverhalten für Live-/Lineare Inhalte:

* Das Wiederaufnehmen der Wiedergabe nach einer Pause führt zur Wiedergabe des Inhalts, der zum Zeitpunkt der Pause gepuffert wurde.

   Wenn sich die Wiederaufnahmeposition weiterhin im Wiedergabebereich befindet, sollte die Wiedergabe kontinuierlich erfolgen. Andernfalls springt TVSDK zum neuen Live-Point. Sie können auch einen Suchvorgang durchführen und einen anderen Wiedergabepunkt auswählen.
* TVSDK löst Anzeigen zwischen den Hinweisen nach der Position, an der die Anwendung die Live-Wiedergabe aufruft.

   Die Wiedergabe beginnt, nachdem der erste Cue aufgelöst wurde. Der Standardwert für die Eingabe der Live-Wiedergabe ist der Live-Point des Clients, Sie können jedoch eine andere Position wählen. Alle Hinweise vor der ursprünglichen Position werden aufgelöst, nachdem die Anwendung eine Suche im DVR-Fenster durchführt.

Die folgende Tabelle beschreibt, wie TVSDK Anzeigen und Werbeunterbrechungen während der Wiedergabe handhabt:

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Video-Aktivität </th> 
   <th colname="col2" class="entry"> Standard-Verhaltensrichtlinie für TVSDK </th> 
   <th colname="col3" class="entry">Anpassung über <span class="codeph"> AdBreakPolicySelector verfügbar </span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Während der normalen Wiedergabe tritt eine Werbeunterbrechung auf. </td> 
   <td colname="col2"> 
    <ul id="ul_10D2638676EA4ADDA718E61BD4FDC1D2"> 
     <li id="li_D5CC30F063934C738971E2E8AF00C137"> Gibt für live/linear die Werbeunterbrechung aus, selbst wenn die Werbeunterbrechung bereits beobachtet wurde. </li> 
     <li id="li_D962C0938DA74186AE99D117E5A74E38">Bei VOD wird die Werbeunterbrechung abgespielt und die Werbeunterbrechung wie angezeigt markiert. </li> 
    </ul> </td> 
   <td colname="col3">Geben Sie mithilfe von <span class="codeph"> selectPolicyForAdBreak</span>eine andere Richtlinie für die Werbeunterbrechung an. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Werbeunterbrechungen in Hauptinhalt nach vorn. </td> 
   <td colname="col2"> Gibt den letzten nicht überwachten Werbeunterbrechungsvorgang zurück, der übersprungen wurde, und setzt die Wiedergabe an der gewünschten Suchposition fort, wenn die Wiedergabe des Werbeunterbrechungsereignisses abgeschlossen ist. </td> 
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay aus, welcher Umbruch wiedergegeben werden soll</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Werbeunterbrechungen in Hauptinhalt nach hinten. </td> 
   <td colname="col2"> Wechselt zur gewünschten Suchposition, ohne Werbeunterbrechungen wiederzugeben. </td> 
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay aus, welcher Umbruch wiedergegeben werden soll</span>.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung versucht, in eine Werbeunterbrechung vorzudringen. </td> 
   <td colname="col2"> Wird ab dem Anfang der Anzeige, in der die Suche beendet wurde, wiedergegeben. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung und für die spezifische Anzeige an, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span>endete. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht rückwärts in eine Werbeunterbrechung. </td> 
   <td colname="col2"> Wird ab dem Anfang der Anzeige, in der die Suche beendet wurde, wiedergegeben. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung und für die spezifische Anzeige an, in der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span>endete. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht vorwärts oder rückwärts über überwachte Werbeunterbrechungen in Hauptinhalt. </td> 
   <td colname="col2"> Wenn der letzte übersprungene Werbeunterbrechung bereits angezeigt wurde, springt zur vom Benutzer ausgewählten Suchposition. </td> 
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay</span> aus, welche der übersprungenen Umbrüche wiedergegeben werden sollen, und stellen Sie fest, welche Umbrüche mit <span class="codeph"> AdBreak.isWatched</span> bereits angezeigt wurden. <p>Wichtig:  Standardmäßig markiert TVSDK eine Werbeunterbrechung, wie sie unmittelbar nach Eingabe der ersten Anzeige in der Werbeunterbrechung gesehen wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht vorwärts oder rückwärts über einen oder mehrere Werbeunterbrechungen und fällt in eine überwachte Werbeunterbrechung. </td> 
   <td colname="col2"> Überspringt die Werbeunterbrechung und sucht an die Position unmittelbar nach der Werbeunterbrechung. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung (wobei der überwachte Status auf true festgelegt ist) und für die spezifische Anzeige, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span>endete, an. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung wird in den Trick-play-Modus (DVR-Modus) versetzt. Die Abspielrate kann negativ (zurückspulen) oder größer als 1 (schnell vorwärts) sein. </td> 
   <td colname="col2"> Überspringt alle Anzeigen während des schnellen Vorwärts- oder Rückspuls, gibt den letzten nach dem Ende der Trick-Wiedergabe übersprungenen Umbruch wieder und springt zur vom Benutzer ausgewählten Trick-Wiedergabeposition, wenn die Wiedergabe mit diesem Umbruch abgeschlossen ist. </td> 
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay aus, welche der übersprungenen Pausen nach dem Ende der Trick-Wiedergabe wiedergegeben werden sollen</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Anzeigen, die mit benutzerspezifischen Anzeigenmarken eingefügt wurden, nach Weiterleitungen. </td> 
   <td colname="col2"> Wechselt zur vom Benutzer ausgewählten Suchposition. </td> 
   <td colname="col3">Weitere Informationen finden Sie unter <a href="../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md" format="dita" scope="local"> Anzeigen einer Scrubbing-Leiste mit der aktuellen Wiedergabeposition...</a> </td> 
  </tr> 
 </tbody> 
</table>