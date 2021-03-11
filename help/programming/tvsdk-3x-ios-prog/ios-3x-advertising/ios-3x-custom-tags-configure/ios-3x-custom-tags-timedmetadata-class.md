---
description: Wenn TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag zu verarbeiten und es in Form eines PTTimedMetadata-Objekts verfügbar zu machen.
title: Zeitgesteuerte Metadatenklasse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Zeitgesteuerte Metadatenklasse {#timed-metadata-class}

Wenn TVSDK ein abonniertes Tag in der Wiedergabeliste/dem Manifest erkennt, versucht der Player automatisch, das Tag zu verarbeiten und es in Form eines PTTimedMetadata-Objekts verfügbar zu machen.

Die Klasse stellt die folgenden Elemente bereit:

<table id="table_FFC56AC5B1E04DA99C9309C0223ABA90"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Eigenschaft</b></th> 
   <th colname="col02" class="entry"><b>Typ</b> </th> 
   <th colname="col2" class="entry"><b>Beschreibung</b></th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> metadataId</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span> </td> 
   <td colname="col2"> Eindeutige ID der zeitgesteuerten Metadaten. Dieser Wert wird normalerweise aus dem Attribut cue/Tag-ID extrahiert. Andernfalls wird ein eindeutiger zufälliger Wert angegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> name</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span></td> 
   <td colname="col2"> Der Name der zeitgesteuerten Metadaten. Wenn der Typ <span class="codeph"> TAG</span> ist, stellt der Wert den Cue/Tag-Namen dar. Wenn der Typ <span class="codeph"> ID3</span> ist, ist er null. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> time</span> </td> 
   <td colname="col02"><span class="codeph"> CMTime</span></td> 
   <td colname="col2"> Die Zeitposition in Millisekunden relativ zum Beginn des Hauptinhalts, an der diese zeitgesteuerte Metadaten im Stream vorhanden sind. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> type</span> </td> 
   <td colname="col02"> <span class="codeph"> PTTimedMetadataType</span></td> 
   <td colname="col2">Der Typ der zeitgesteuerten Metadaten. 
    <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
     <li id="li_739D30561BFB4D9B97DF212E4880BA2C">TAG: Gibt an, dass die zeitgesteuerte Metadaten aus einem Tag in der Wiedergabeliste/dem Manifest erstellt wurden. </li> 
     <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3: Gibt an, dass die zeitgesteuerten Metadaten aus einem ID3-Tag im Medienstream erstellt wurden. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

Beachten Sie Folgendes:

* TVSDK extrahiert die Attribute-Liste automatisch in Schlüssel/Wert-Paare und speichert die Attribute in der Metadateneigenschaft.

   >[!TIP]
   >
   >Komplexe Daten in benutzerdefinierten Tags im Manifest, z. B. Zeichenfolgen mit Sonderzeichen, müssen in Anführungszeichen gesetzt werden. Beispiel:
   >
   >
   ```
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url=
   >"www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```

* Wenn die Extraktion aufgrund eines benutzerdefinierten Tag-Formats fehlschlägt, enthält die content-Eigenschaft immer die Rohdaten des Tags, d. h. die Zeichenfolge nach dem Doppelpunkt. In diesem Fall wird kein Fehler ausgegeben.

| **Element** | **Beschreibung** |
|---|---|
| TAG, ID3 | Mögliche Typen für zeitgesteuerte Metadaten. |
| `@property (nonatomic, assign) CMTime time` | Die Zeitposition relativ zum Beginn des Hauptinhalts, an der diese Metadaten in den Stream eingefügt wurden. |
| `@property (nonatomic, assign) PTTimedMetadataType type` | Gibt den Typ der zeitgesteuerten Metadaten zurück. |
| `@property (nonatomic, retain) NSString *metadataId` | Gibt die ID zurück, die aus den Attributen cue/Tag extrahiert wurde. Andernfalls wird ein eindeutiger zufälliger Wert angegeben. |
| `@property (nonatomic, retain) NSString *name` | Gibt den Namen des Cue zurück, bei dem es sich normalerweise um den HLS-Tag-Namen handelt. |