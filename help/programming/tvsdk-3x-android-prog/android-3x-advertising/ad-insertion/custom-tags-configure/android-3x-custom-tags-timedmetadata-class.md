---
description: Wenn TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag in Form eines TimedMetadata-Objekts zu verarbeiten und anzuzeigen.
title: Zeitgesteuerte Metadatenklasse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Zeitgesteuerte Metadatenklasse {#timed-metadata-class}

Wenn TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag in Form eines TimedMetadata-Objekts zu verarbeiten und anzuzeigen.

Die -Klasse stellt die folgenden Elemente bereit:

<table id="table_FFC56AC5B1E04DA99C9309C0223ABA90"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b> Eigenschaft </b></th> 
   <th colname="col02" class="entry"> <b> Typ </b></th> 
   <th colname="col2" class="entry"> <b> Beschreibung </b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> id </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> <p>Eindeutige Kennung der zeitgesteuerten Metadaten. </p> <p>Dieser Wert wird normalerweise aus dem Cue-/Tag-ID-Attribut extrahiert. Andernfalls wird ein eindeutiger zufälliger Wert bereitgestellt. Verwendung <span class="codeph"> getId </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> Metadaten </span> </td> 
   <td colname="col02"> Metadaten </td> 
   <td colname="col2"> <p>Die verarbeiteten/extrahierten Informationen aus dem benutzerdefinierten Tag "playlist/manifest". Verwendung <span class="codeph"> getMetadata </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> name </span> </td> 
   <td colname="col02"> Zeichenfolge </td> 
   <td colname="col2"> <p>Der Name der zeitgesteuerten Metadaten. Wenn der Typ <span class="codeph"> TAG </span>, stellt der Wert den Cue-/Tag-Namen dar. Wenn der Typ <span class="codeph"> ID3 </span>, ist es null. Verwendung <span class="codeph"> getName </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> time </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> <p>Die Zeitposition in Millisekunden relativ zum Anfang des Hauptinhalts, in dem diese zeitgesteuerten Metadaten im Stream vorhanden sind. Verwendung <span class="codeph"> getTime </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> type </span> </td> 
   <td colname="col02"> Typ </td> 
   <td colname="col2"> <p>Der Typ der zeitgesteuerten Metadaten. Verwendung <span class="codeph"> getType </span>. 
     <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
      <li id="li_739D30561BFB4D9B97DF212E4880BA2C">TAG - gibt an, dass die zeitgesteuerten Metadaten aus einem Tag in der Wiedergabeliste/dem Manifest erstellt wurden. </li> 
      <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3: Gibt an, dass die zeitgesteuerten Metadaten aus einem ID3-Tag im Medien-Stream erstellt wurden. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

Beachten Sie Folgendes:

* TVSDK extrahiert die Attributliste automatisch in Schlüssel-Wert-Paare und speichert die Attribute in der Metadateneigenschaft.

  >[!TIP]
  >
  >Komplexe Daten in benutzerdefinierten Tags im Manifest, z. B. Zeichenfolgen mit Sonderzeichen, müssen in Anführungszeichen gesetzt werden. Beispiel:
  >
  >```
  >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url= 
  >"www.example.com:8090?parameter1=xyz&parameter2=abc"
  >```
  >

* Wenn die Extraktion aufgrund eines benutzerdefinierten Tag-Formats fehlschlägt, ist die Metadateneigenschaft leer, und Ihre Anwendung muss die tatsächlichen Informationen extrahieren. In diesem Fall wird kein Fehler ausgegeben.

<table id="table_1BAE98BF23F641A3A5709EBE37B327F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <b>Element </b></th> 
   <th colname="col2" class="entry"> <b>Beschreibung</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public enum Type {TAG, ID3} </span> </td> 
   <td colname="col2"> <p>Mögliche Typen für die zeitgesteuerten Metadaten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public TimedMetadata(Type, long time, long id, String name, Metadata metadata); </span> </td> 
   <td colname="col2"> <p>Standardkonstruktor (Zeit ist die lokale Stream-Zeit). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public long getTime(); </span> </td> 
   <td colname="col2"> <p>Die Zeitposition, relativ zum Anfang des Hauptinhalts, an der diese Metadaten in den Stream eingefügt wurden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public Metadata getMetadata(); </span> </td> 
   <td colname="col2"> <p>Die im Stream eingefügten Metadaten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public Type getType(); </span> </td> 
   <td colname="col2"> <p>Gibt den Typ der zeitgesteuerten Metadaten zurück. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public long getId(); </span> </td> 
   <td colname="col2"> <p>Gibt die ID zurück, die aus den Cue/Tag-Attributen extrahiert wurde. Andernfalls wird ein eindeutiger zufälliger Wert bereitgestellt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public String getName(); </span> </td> 
   <td colname="col2"> <p>Gibt den Namen des Cue-Point zurück, bei dem es sich normalerweise um den HLS-Tag-Namen handelt. </p> </td> 
  </tr> 
 </tbody> 
</table>
