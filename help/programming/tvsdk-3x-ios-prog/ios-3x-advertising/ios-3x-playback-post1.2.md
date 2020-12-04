---
description: Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten und die Einbeziehung von Werbung beeinflusst.
seo-description: Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten und die Einbeziehung von Werbung beeinflusst.
seo-title: Standard- und benutzerdefiniertes Wiedergabeverhalten mit Anzeigen
title: Standard- und benutzerdefiniertes Wiedergabeverhalten mit Anzeigen
uuid: 570f6d77-cbb9-4aa7-a935-058003f4ce87
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---


# Standard- und angepasstes Wiedergabeverhalten mit Anzeigen {#default-and-customized-playback-behavior-with-ads}

Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten und die Einbeziehung von Werbung beeinflusst.

Um das Standardverhalten zu überschreiben, verwenden Sie `PTAdPolicySelector`.

>[!IMPORTANT]
>
>Für VOD und Live-/Lineare Streaming können Zeitleistenanpassungen nicht geändert werden. Das bedeutet, dass eine Anzeige nach der Wiedergabe nicht mehr aus der Zeitleiste entfernt werden kann. Wenn der Benutzer die Suche zurückführt, wird dieselbe Anzeige erneut wiedergegeben, selbst wenn die normale Richtlinie darin bestand, sie zu entfernen.

>[!IMPORTANT]
>
>TVSDK bietet keine Möglichkeit, die Suche während der Anzeigen zu deaktivieren. Adobe empfiehlt, Ihre Anwendung so zu konfigurieren, dass die Suche während der Anzeigen deaktiviert wird.

Die folgende Tabelle beschreibt, wie TVSDK Anzeigen und Werbeunterbrechungen während der Wiedergabe handhabt:

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Video-Aktivität</b></th> 
   <th colname="col2" class="entry"><b>Standard-Verhaltensrichtlinie für TVSDK</b></th> 
   <th colname="col3" class="entry"><b>Anpassung über PTAdPolicySelector verfügbar</b></th>
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Während der normalen Wiedergabe tritt eine Werbeunterbrechung auf. </td> 
   <td colname="col2"></td> 
   <td colname="col3">Geben Sie eine andere Richtlinie für die Werbeunterbrechung an, indem Sie <span class="codeph"> selectPolicyForAdBreak</span> verwenden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Werbeunterbrechungen in Hauptinhalt nach vorn. </td> 
   <td colname="col2"> Gibt den letzten nicht überwachten Werbeunterbrechungsvorgang zurück, der übersprungen wurde, und setzt die Wiedergabe an der gewünschten Suchposition fort, wenn die Wiedergabe des Werbeunterbrechungsereignisses abgeschlossen ist. </td> 
   <td colname="col3">Wählen Sie mit <span class="codeph"> selectAdBreaksToPlay</span> aus, welcher Umbruch abgespielt werden soll. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Werbeunterbrechungen in Hauptinhalt nach hinten. </td> 
   <td colname="col2"> Wechselt zur gewünschten Suchposition, ohne Werbeunterbrechungen wiederzugeben. </td> 
   <td colname="col3">Wählen Sie mit <span class="codeph"> selectAdBreaksToPlay</span> aus, welcher Umbruch abgespielt werden soll.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung versucht, in eine Werbeunterbrechung vorzudringen. </td> 
   <td colname="col2"> Wird ab dem Anfang der Anzeige, in der die Suche beendet wurde, wiedergegeben. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung und für die spezifische Anzeige an, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span> endete. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht rückwärts in eine Werbeunterbrechung. </td> 
   <td colname="col2"> Wird ab dem Anfang der Anzeige, in der die Suche beendet wurde, wiedergegeben. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung und für die spezifische Anzeige an, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span> endete. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht vorwärts oder rückwärts über überwachte Werbeunterbrechungen in Hauptinhalt. </td> 
   <td colname="col2"> Wenn der letzte übersprungene Werbeunterbrechung bereits angezeigt wurde, springt zur vom Benutzer ausgewählten Suchposition. </td> 
   <td colname="col3">Wählen Sie aus, welche der übersprungenen Umbrüche mit <span class="codeph"> selectAdBreaksToPlay</span> wiedergegeben werden sollen, und stellen Sie fest, welche Umbrüche bereits mit <span class="codeph"> PTAdBreak.isWatched</span> überwacht wurden. <p> <p>Wichtig:  Standardmäßig markiert TVSDK eine Werbeunterbrechung, wie sie unmittelbar nach Eingabe der ersten Anzeige in der Werbeunterbrechung gesehen wird. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht vorwärts oder rückwärts über einen oder mehrere Werbeunterbrechungen und fällt in eine überwachte Werbeunterbrechung. </td> 
   <td colname="col2"> Überspringt die Werbeunterbrechung und sucht an die Position unmittelbar nach der Werbeunterbrechung. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung (wobei der überwachte Status auf "true"festgelegt ist) und für die spezifische Anzeige, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span> endete, an. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Anzeigen nach, die mit benutzerspezifischen Anzeigenmarken eingefügt wurden. </td> 
   <td colname="col2"> Wechselt zur vom Benutzer ausgewählten Suchposition. </td> 
   <td colname="col3"></td> 
  </tr> 
 </tbody> 
</table>