---
description: Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten, Vorwärts- oder Zurückspulen sowie Werbung beeinflusst.
title: Standardmäßige und benutzerdefinierte Wiedergabe-Verhalten mit Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Standardmäßige und benutzerdefinierte Wiedergabe-Verhalten mit Anzeigen{#default-and-customized-playback-behavior-with-ads}

Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten, Vorwärts- oder Zurückspulen sowie Werbung beeinflusst.

Um das Standardverhalten zu überschreiben, verwenden Sie `AdBreakPolicySelector` .

>[!IMPORTANT]
>
>TVSDK bietet keine Möglichkeit, die Suche während Anzeigen zu deaktivieren. Adobe empfiehlt, dass Sie Ihre Anwendung so konfigurieren, dass die Suche während Anzeigen deaktiviert wird.

Hier finden Sie das Wiedergabeverhalten für Live-/Linearinhalte:

* Das Fortsetzen der Wiedergabe nach einer Pause führt zur Wiedergabe des Inhalts, der zum Zeitpunkt der Pause gepuffert wurde.

  Wenn sich die Wiederaufnahmeposition noch im Wiedergabefeld befindet, sollte die Wiedergabe fortgesetzt werden. Andernfalls springt TVSDK zum neuen Live-Punkt. Sie können auch einen Suchvorgang durchführen und einen anderen Wiedergabepunkt auswählen.
* TVSDK löst Anzeigen zwischen Cups nach der Position auf, an der die Anwendung die Live-Wiedergabe startet.

  Die Wiedergabe beginnt, nachdem der erste Cue-Punkt aufgelöst wurde. Der Standardwert für die Eingabe der Live-Wiedergabe ist der Client-Live-Point, Sie können jedoch eine andere Position auswählen. Alle Hinweise vor der ursprünglichen Position werden aufgelöst, nachdem die Anwendung eine Suche im DVR-Fenster durchführt.

In der folgenden Tabelle wird beschrieben, wie TVSDK Anzeigen und Werbeunterbrechungen während der Wiedergabe verarbeitet:

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Videoaktivität </th> 
   <th colname="col2" class="entry"> Standard-TVSDK-Verhaltensrichtlinie </th> 
   <th colname="col3" class="entry">Anpassung verfügbar über <span class="codeph"> AdBreakPolicySelector </span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Während der normalen Wiedergabe tritt eine Werbeunterbrechung auf. </td> 
   <td colname="col2"> 
    <ul id="ul_10D2638676EA4ADDA718E61BD4FDC1D2"> 
     <li id="li_D5CC30F063934C738971E2E8AF00C137"> Bei Live/Linear wird die Werbeunterbrechung wiedergegeben, selbst wenn die Werbeunterbrechung bereits gesehen wurde. </li> 
     <li id="li_D962C0938DA74186AE99D117E5A74E38">Bei VOD wird die Werbeunterbrechung wiedergegeben und die Werbeunterbrechung als angesehen markiert. </li> 
    </ul> </td> 
   <td colname="col3">Geben Sie eine andere Richtlinie für die Werbeunterbrechung an, indem Sie <span class="codeph"> selectPolicyForAdBreak</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Werbeunterbrechungen in Hauptinhalt nach vorn. </td> 
   <td colname="col2"> Gibt die letzte nicht überwachte Werbeunterbrechung wieder, die übersprungen wurde, und setzt die Wiedergabe an der gewünschten Suchposition fort, wenn die Wiedergabe der Werbeunterbrechung(en) abgeschlossen ist. </td> 
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Werbeunterbrechungen in den Hauptinhalt zurück. </td> 
   <td colname="col2"> Wechselt zur gewünschten Suchposition ohne Wiedergabe von Werbeunterbrechungen. </td> 
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay</span>.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht nach einer Werbeunterbrechung. </td> 
   <td colname="col2"> Wird am Anfang der Anzeige wiedergegeben, in der die Suche endete. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung und für die spezifische Anzeige an, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht nach einer Werbeunterbrechung. </td> 
   <td colname="col2"> Wird am Anfang der Anzeige wiedergegeben, in der die Suche endete. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung und für die spezifische Anzeige an, in der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht vorwärts oder rückwärts über überwachte Werbeunterbrechungen in Hauptinhalt. </td> 
   <td colname="col2"> Wenn die letzte übersprungene Werbeunterbrechung bereits gesehen wurde, wird zur vom Benutzer ausgewählten Suchposition übersprungen. </td> 
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay</span> und bestimmen mithilfe von <span class="codeph"> AdBreak.isWatched</span> . <p>Wichtig: TVSDK markiert standardmäßig eine Werbeunterbrechung, wie sie unmittelbar nach Eingabe der ersten Anzeige in der Werbeunterbrechung wiedergegeben wurde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht vorwärts oder rückwärts über eine oder mehrere Werbeunterbrechungen und fällt in eine überwachte Werbeunterbrechung. </td> 
   <td colname="col2"> Überspringt die Werbeunterbrechung und sucht an die Position unmittelbar nach der Werbeunterbrechung. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung (wobei der überwachte Status auf "true"festgelegt ist) und für die spezifische Anzeige an, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Applikation wechselt in den Trick-Play (DVR-Modus). Die Abspielrate kann negativ (zurückspulen) oder größer als 1 (schnell vorwärts) sein. </td> 
   <td colname="col2"> Überspringt alle Anzeigen während der schnellen Vorwärts- oder Rückspaltung, gibt die letzte nach dem Ende der Trick-Wiedergabe übersprungene Pause wieder und überspringt die vom Benutzer ausgewählte Trick-Wiedergabeposition, wenn die Wiedergabe der Pause beendet wird. </td> 
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht nach Anzeigen, die mit benutzerdefinierten Anzeigenmarken eingefügt wurden. </td> 
   <td colname="col2"> Wechselt zur vom Benutzer ausgewählten Suchposition. </td> 
   <td colname="col3">Weitere Informationen finden Sie unter <a href="../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md" format="dita" scope="local"> Anzeigen einer Suchleiste mit der aktuellen Wiedergabeposition ...</a> </td> 
  </tr> 
 </tbody> 
</table>
