---
description: Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten, Vorspulen oder Zurückspulen (Trick Play-Modus) und die Einbeziehung der Werbung beeinflusst.
seo-description: Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten, Vorspulen oder Zurückspulen (Trick Play-Modus) und die Einbeziehung der Werbung beeinflusst.
seo-title: Standard- und benutzerdefiniertes Wiedergabeverhalten mit Anzeigen
title: Standard- und benutzerdefiniertes Wiedergabeverhalten mit Anzeigen
uuid: 58f11167-a764-4647-8490-05ca66eb6c47
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Standard- und angepasstes Wiedergabeverhalten mit Anzeigen{#default-and-customized-playback-behavior-with-ads}

Das Verhalten der Medienwiedergabe wird durch Suchen, Anhalten, Vorspulen oder Zurückspulen (Trick Play-Modus) und die Einbeziehung der Werbung beeinflusst.

Um das Standardverhalten zu überschreiben, verwenden Sie `AdBreakPolicySelector`.

>[!IMPORTANT]
>
>Browser TVSDK bietet keine Möglichkeit, die Suche während der Anzeigen zu deaktivieren. Adobe empfiehlt, Ihre Anwendung so zu konfigurieren, dass die Suche während der Anzeigen deaktiviert wird.

In der folgenden Tabelle wird beschrieben, wie Browser TVSDK Anzeigen und Werbeunterbrechungen während der Wiedergabe verarbeitet:

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Video-Aktivität </th> 
   <th colname="col2" class="entry"> Standard-Browser-TVSDK-Verhaltensrichtlinie </th> 
   <th colname="col3" class="entry">Anpassung verfügbar über <span class="codeph"> AdBreakPolicySelector </span> </th> 
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
   <td colname="col3">Wählen Sie aus, welche der übersprungenen Umbrüche mit <span class="codeph"> selectAdBreaksToPlay</span> wiedergegeben werden sollen, und stellen Sie fest, welche Umbrüche mit <span class="codeph"> isWatched</span> bereits überwacht wurden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht vorwärts oder rückwärts über einen oder mehrere Werbeunterbrechungen und fällt in eine überwachte Werbeunterbrechung. </td> 
   <td colname="col2"> Überspringt die Werbeunterbrechung und sucht an die Position unmittelbar nach der Werbeunterbrechung. </td> 
   <td colname="col3">Geben Sie eine andere Anzeigenrichtlinie für die Werbeunterbrechung (wobei der überwachte Status auf "true"festgelegt ist) und für die spezifische Anzeige, bei der die Suche mit <span class="codeph"> selectPolicyForSeekIntoAd</span> endete, an. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ihre Anwendung sucht über Anzeigen nach, die mit benutzerspezifischen Anzeigenmarken eingefügt wurden. </td> 
   <td colname="col2"> Wechselt zur vom Benutzer ausgewählten Suchposition. </td> 
   <td colname="col3">Weitere Informationen finden Sie unter <a href="../../browser-tvsdk-2.4/content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-seek-scrub-bar-display.md" format="dita" scope="local"> Suchen bei Verwendung der Suchleiste</a> bearbeiten </td> 
  </tr> 
 </tbody> 
</table>

## Einrichten von benutzerdefiniertem Anzeigenverhalten {#section_custom_ad_behaviors}

Sie können Ihr bevorzugtes Verhalten in der Factory für Anzeigeninhalte mit der Methode `retrieveAdPolicySelectorCallbackFunc` festlegen. Sie können die Methoden `selectPolicyForAdBreak`, `selectWatchedPolicyForAdBreak`, `selectPolicyForSeekIntoAd` und `selectAdBreaksToPlay` in der Inhaltsfactory verwenden, um eine Richtlinie auszuwählen.
