---
description: Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten und Einbeziehung von Werbung beeinflusst.
title: Standardmäßige und benutzerdefinierte Wiedergabe-Verhalten mit Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# Standardmäßige und benutzerdefinierte Wiedergabe-Verhalten mit Anzeigen{#default-and-customized-playback-behavior-with-ads}

Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten und Einbeziehung von Werbung beeinflusst.

Um das Standardverhalten zu überschreiben, verwenden Sie `PTAdPolicySelector`.

>[!IMPORTANT]
>
>Für VOD und Live-/Linear-Streaming können Zeitleistenanpassungen nicht geändert werden. Das bedeutet, dass eine Anzeige nach der Wiedergabe nicht mehr aus der Timeline entfernt werden kann. Wenn der Benutzer die Suche wiederholt, wird dieselbe Anzeige erneut wiedergegeben, selbst wenn die normale Richtlinie darin bestanden hätte, sie zu entfernen.

>[!IMPORTANT]
>
>TVSDK bietet keine Möglichkeit, die Suche während Anzeigen zu deaktivieren. Adobe empfiehlt, dass Sie Ihre Anwendung so konfigurieren, dass die Suche während Anzeigen deaktiviert wird.

In der folgenden Tabelle wird beschrieben, wie TVSDK Anzeigen und Werbeunterbrechungen während der Wiedergabe verarbeitet:

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Videoaktivität </th> 
   <th colname="col2" class="entry"> Standard-TVSDK-Verhaltensrichtlinie </th> 
   <th colname="col3" class="entry">Anpassung verfügbar über <span class="codeph"> PTAdPolicySelector</span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Während der normalen Wiedergabe tritt eine Werbeunterbrechung auf. </td> 
   <td colname="col2"></td> 
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
   <td colname="col3">Wählen Sie mithilfe von <span class="codeph"> selectAdBreaksToPlay</span> und bestimmen mithilfe von <span class="codeph"> PTAdBreak.isWatched</span>. <p> <p>Wichtig: TVSDK markiert standardmäßig eine Werbeunterbrechung, wie sie unmittelbar nach Eingabe der ersten Anzeige in der Werbeunterbrechung wiedergegeben wurde. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht vorwärts oder rückwärts über eine oder mehrere Werbeunterbrechungen und fällt in eine überwachte Werbeunterbrechung. </td> 
   <td colname="col2"> Überspringt die Werbeunterbrechung und sucht an die Position unmittelbar nach der Werbeunterbrechung. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung (wobei der überwachte Status auf "true"festgelegt ist) und für die spezifische Anzeige an, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht nach Anzeigen, die mit benutzerdefinierten Anzeigenmarken eingefügt wurden. </td> 
   <td colname="col2"> Wechselt zur vom Benutzer ausgewählten Suchposition. </td> 
   <td colname="col3"></td> 
  </tr> 
 </tbody> 
</table>
