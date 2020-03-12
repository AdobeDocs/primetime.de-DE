---
description: Wenn TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag in Form eines TimedMetadata-Objekts zu verarbeiten und verfügbar zu machen.
seo-description: Wenn TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag in Form eines TimedMetadata-Objekts zu verarbeiten und verfügbar zu machen.
seo-title: Zeitgesteuerte Metadatenklasse
title: Zeitgesteuerte Metadatenklasse
uuid: c7b1c1d7-48b3-43c7-aa21-f800d894976d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Zeitgesteuerte Metadatenklasse {#timed-metadata-class}

Wenn TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag in Form eines TimedMetadata-Objekts zu verarbeiten und verfügbar zu machen.

Die Klasse stellt die folgenden Elemente bereit:

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
   <td colname="col2"> <p>Eindeutige ID der zeitgesteuerten Metadaten. </p> <p>Dieser Wert wird normalerweise aus dem Attribut cue/Tag-ID extrahiert. Andernfalls wird ein eindeutiger zufälliger Wert angegeben. Verwenden Sie <span class="codeph"> getId </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> metadata </span> </td> 
   <td colname="col02"> Metadaten </td> 
   <td colname="col2"> <p>Die verarbeiteten/extrahierten Informationen aus dem benutzerdefinierten Tag "playlist/manifest". Verwenden Sie <span class="codeph"> getMetadata </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> name </span> </td> 
   <td colname="col02"> Zeichenfolge </td> 
   <td colname="col2"> <p>Der Name der zeitgesteuerten Metadaten. Wenn der Typ <span class="codeph"> TAG ist </span>, stellt der Wert den Cue/Tag-Namen dar. Lautet der Typ <span class="codeph"> ID3 </span>, ist er null. Verwenden Sie <span class="codeph"> getName </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> time </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> <p>Die Zeitposition in Millisekunden relativ zum Beginn des Hauptinhalts, an der diese zeitgesteuerte Metadaten im Stream vorhanden sind. Verwenden Sie <span class="codeph"> getTime </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> type </span> </td> 
   <td colname="col02"> Typ </td> 
   <td colname="col2"> <p>Der Typ der zeitgesteuerten Metadaten. Verwenden Sie <span class="codeph"> getType </span>. 
     <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
      <li id="li_739D30561BFB4D9B97DF212E4880BA2C">TAG: Gibt an, dass die zeitgesteuerte Metadaten aus einem Tag in der Wiedergabeliste/dem Manifest erstellt wurden. </li> 
      <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3: Gibt an, dass die zeitgesteuerten Metadaten aus einem ID3-Tag im Medienstream erstellt wurden. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

Beachten Sie Folgendes:

* TVSDK extrahiert die Attribute-Liste automatisch in Schlüssel/Wert-Paare und speichert die Attribute in der Metadateneigenschaft.

   >[!TIP]
   >
   >Komplexe Daten in benutzerdefinierten Tags im Manifest, z. B. Zeichenfolgen mit Sonderzeichen, müssen in Anführungszeichen gesetzt werden. Beispiel:   >
   >
   >
   ```>
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url= 
   >"www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```  >
   >



* Wenn die Extraktion aufgrund eines benutzerdefinierten Tag-Formats fehlschlägt, ist die Metadateneigenschaft leer und die eigentlichen Informationen müssen von Ihrer Anwendung extrahiert werden. In diesem Fall wird kein Fehler ausgegeben.

<table id="table_1BAE98BF23F641A3A5709EBE37B327F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <b>Element </b></th> 
   <th colname="col2" class="entry"> <b>Beschreibung</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public enum type {TAG, ID3} </span> </td> 
   <td colname="col2"> <p>Mögliche Typen für zeitgesteuerte Metadaten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public TimedMetadata(Type type, long time, long id, String name, Metadata metadata); </span> </td> 
   <td colname="col2"> <p>Standardkonstruktor (time ist die lokale Stream-Zeit). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public long getTime(); </span> </td> 
   <td colname="col2"> <p>Die Zeitposition relativ zum Beginn des Hauptinhalts, an der diese Metadaten in den Stream eingefügt wurden. </p> </td> 
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
   <td colname="col2"> <p>Gibt die ID zurück, die aus den Attributen cue/Tag extrahiert wurde. Andernfalls wird ein eindeutiger zufälliger Wert angegeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public String getName(); </span> </td> 
   <td colname="col2"> <p>Gibt den Namen des Cue zurück, bei dem es sich normalerweise um den HLS-Tag-Namen handelt. </p> </td> 
  </tr> 
 </tbody> 
</table>