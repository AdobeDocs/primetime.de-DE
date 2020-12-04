---
description: Sie können Servicequalitätsinformationen (QoS) zu heruntergeladenen Ressourcen wie Fragmenten und Spuren aus der LoadInformation-Klasse lesen.
seo-description: Sie können Servicequalitätsinformationen (QoS) zu heruntergeladenen Ressourcen wie Fragmenten und Spuren aus der LoadInformation-Klasse lesen.
seo-title: Verfolgen auf Fragmentebene mithilfe der Ladeinformationen
title: Verfolgen auf Fragmentebene mithilfe der Ladeinformationen
uuid: 41fb2b90-3531-4cc5-bf9b-01ccae04d2fd
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Verfolgen auf Fragmentebene mithilfe der Ladeinformationen{#track-at-the-fragment-level-using-load-information}

Sie können Servicequalitätsinformationen (QoS) zu heruntergeladenen Ressourcen wie Fragmenten und Spuren aus der LoadInformation-Klasse lesen.

1. Implementieren Sie den `onLoadInformationAvailable`-Callback-Ereignis-Listener.

   ```
   private function onLoadInformationAvailable(event:LoadInformationEvent):void { 
       var loadInformation:LoadInformation = event.loadInformation; 
       // process the load information here     
   }
   ```

1. Registrieren Sie den Ereignis-Listener, den TVSDK jedes Mal aufruft, wenn ein Fragment heruntergeladen wurde.

   ```
   player.addEventListener(LoadInformationEvent.LOAD_INFORMATION_AVAILABLE,  
                                    onLoadInformationAvailable);
   ```

1. Lesen Sie die Daten von Interesse aus dem `LoadInformation`, das an den Rückruf übergeben wird.

   <table id="table_75E61A2EB25E435DB631166A7FF64757"> 
   <thead> 
   <tr> 
      <th colname="col01" class="entry"> Eigenschaft </th> 
      <th colname="col1" class="entry"> Typ </th> 
      <th colname="col2" class="entry"> Beschreibung </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration  </span> </td> 
      <td colname="col1"> <p>Nummer </p> </td> 
      <td colname="col2"> <p>Die Dauer des Downloads in Millisekunden. </p> <p>TVSDK unterscheidet nicht zwischen der Zeit, die der Client für die Verbindung mit dem Server benötigt hat, und der Zeit, die es zum Herunterladen des vollständigen Fragments dauerte. Wenn das Herunterladen eines Segments mit 10 MB z. B. 8 Sekunden in Anspruch nimmt, gibt TVSDK diese Informationen an, teilt Ihnen jedoch nicht mit, dass es bis zum ersten Byte 4 Sekunden und bis zum Herunterladen des gesamten Fragments weitere 4 Sekunden dauerte. </p> </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration  </span> </td> 
      <td colname="col1"> <p>Nummer </p> </td> 
      <td colname="col2"> Die Mediendauer der heruntergeladenen Fragmente in Millisekunden. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> size  </span> </td> 
      <td colname="col1"> <p>Nummer </p> </td> 
      <td colname="col2"> Die Größe der heruntergeladenen Ressource in Byte. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex  </span> </td> 
      <td colname="col1"> <p>int </p> </td> 
      <td colname="col2"> der Index der entsprechenden Spur, sofern bekannt; andernfalls 0. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackName  </span> </td> 
      <td colname="col1"> <p>Zeichenfolge </p> </td> 
      <td colname="col2"> Name der entsprechenden Spur, sofern bekannt; ansonsten null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackType  </span> </td> 
      <td colname="col1"> <p>Zeichenfolge </p> </td> 
      <td colname="col2"> Typ der entsprechenden Strecke, sofern bekannt; ansonsten null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> type  </span> </td> 
      <td colname="col1"> <p>Zeichenfolge </p> </td> 
      <td colname="col2"> Was TVSDK heruntergeladen hat. Eine der folgenden Möglichkeiten: 
      <ul id="ul_FA02F42D109344F4866073908CA4E835"> 
      <li id="li_0E2D3EBCAB58477FB5EA526C54FACFFB">MANIFEST - Eine Wiedergabeliste/ein Manifest </li> 
      <li id="li_D7894C2F0CB64C909C6398288EA5683A">FRAGMENT - Ein Fragment </li> 
      <li id="li_4D4FEDB7704C411B80891B5028B0C20E">TRACK - Ein mit einer bestimmten Spur verknüpftes Fragment </li> 
      </ul> Manchmal ist es möglicherweise nicht möglich, den Typ der Ressource zu erkennen. In diesem Fall wird die DATEI zurückgegeben. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> url  </span> </td> 
      <td colname="col1"> <p>Zeichenfolge </p> </td> 
      <td colname="col2"> Die URL, die auf die heruntergeladene Ressource verweist. </td> 
   </tr> 
   </tbody> 
   </table>
