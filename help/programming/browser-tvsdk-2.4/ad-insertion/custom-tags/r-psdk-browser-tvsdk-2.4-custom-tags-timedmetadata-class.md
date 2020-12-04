---
description: Wenn Browser TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag zu verarbeiten und es als TimedMetadata-Objekt verfügbar zu machen.
seo-description: Wenn Browser TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag zu verarbeiten und es als TimedMetadata-Objekt verfügbar zu machen.
seo-title: Zeitgesteuerte Metadatenklasse
title: Zeitgesteuerte Metadatenklasse
uuid: 3f276618-5f61-4b41-bd2d-78e7f32178d9
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Zeitgesteuerte Metadatenklasse{#timed-metadata-class}

Wenn Browser TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag zu verarbeiten und es als TimedMetadata-Objekt verfügbar zu machen.

Die `TimedMetadata`-Klasse stellt die folgenden Elemente bereit:

<table id="table_5827A0626EDC45F68DC3E7644F3EFF69"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Eigenschaft </th> 
   <th colname="col02" class="entry"> Typ </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>type </p> </td> 
   <td colname="col02"> <p><span class="codeph"> TimedMetadataType</span> </p> </td> 
   <td colname="col2"> <p>Im Folgenden finden Sie die Metadatentypen mit Timing: 
     <ul id="ul_E79C375A54C64BF09A927EE8983E98E3"> 
      <li id="li_F1907521CDBE47E282A87AF0A7A1477A">TAG - Die zeitgesteuerten Metadaten wurden aus einem Tag in der Wiedergabeliste/dem Manifest erstellt. </li> 
      <li id="li_5B0C0B0F247144709F86E6654A5AB500">ID3: Die zeitgesteuerten Metadaten wurden aus einem ID3-Tag im Medienstream erstellt. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>time </p> </td> 
   <td colname="col02"> <p>Nummer </p> </td> 
   <td colname="col2"> <p>Die lokale Zeitposition (Millisekunden) relativ zum Beginn des Hauptinhalts, an der diese zeitgesteuerten Metadaten im Stream vorhanden sind. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>id </p> </td> 
   <td colname="col02"> <p>Zeichenfolge </p> </td> 
   <td colname="col2"> <p>Die eindeutige Kennung der zeitgesteuerten Metadaten. </p> <p>Wird normalerweise aus dem Attribut cue/Tag-ID extrahiert, wenn vorhanden. Andernfalls handelt es sich um einen eindeutigen zufälligen Wert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>name </p> </td> 
   <td colname="col02"> <p>Nummer </p> </td> 
   <td colname="col2"> <p>Der Name der zeitgesteuerten Metadaten. </p> <p>Wenn der Typ TAG ist, stellt der Wert den Cue/Tag-Namen dar. Wenn der Typ ID3 ist, ist der Wert null. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>content </p> </td> 
   <td colname="col02"> <p>Zeichenfolge </p> </td> 
   <td colname="col2"> <p>Der Rohinhalt der zeitgesteuerten Metadaten. </p> <p>Wenn der Typ TAG ist, stellt der Wert die gesamte Attribut-Liste des Cue/Tags dar. Wenn der Typ ID3, ist der Wert null. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>metadata </p> </td> 
   <td colname="col02"> <p><span class="codeph"> Metadaten</span> </p> </td> 
   <td colname="col2"> <p>Die verarbeiteten/extrahierten Informationen aus dem benutzerdefinierten Tag "playlist/manifest". </p> </td> 
  </tr> 
 </tbody> 
</table>

