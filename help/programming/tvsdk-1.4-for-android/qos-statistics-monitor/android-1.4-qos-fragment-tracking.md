---
description: Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
title: Auf Fragmentebene mithilfe von Ladeinformationen verfolgen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Auf Fragmentebene mithilfe von Ladeinformationen verfolgen{#track-at-the-fragment-level-using-load-information}

Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

TVSDK bietet außerdem Informationen zu den folgenden heruntergeladenen Ressourcen:

1. Wiedergabelisten-/Manifestdateien
1. Dateifragmente
1. Tracking-Informationen für Dateien

   Sie können Informationen zur Servicequalität (QoS) über heruntergeladene Ressourcen, wie Fragmente und Tracks, aus dem `LoadInfo` -Klasse.

1. Implementieren des `onLoadInfo` Callback-Ereignis-Listener.
1. Registrieren Sie den Ereignis-Listener, den TVSDK jedes Mal aufruft, wenn ein Fragment heruntergeladen wurde.
1. Lesen Sie die interessanten Daten aus der `LoadInfo` -Parameter, der an den Rückruf übergeben wird.

   <table id="table_06BD536A23AB4A73B510998426BAE143"> 
    <thead> 
      <tr> 
      <th colname="col01" class="entry"> Eigenschaft </th> 
      <th colname="col1" class="entry"> Typ </th> 
      <th colname="col2" class="entry"> Beschreibung </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col01"> <span class="codeph"> downloadDauer </span> </td> 
      <td colname="col1"> <span class="codeph"> long </span> </td> 
      <td colname="col2"> <p>Die Dauer des Downloads in Millisekunden. </p> <p>TVSDK unterscheidet nicht zwischen der Zeit, die der Client für die Verbindung mit dem Server benötigt hat, und der Zeit, die zum Herunterladen des vollständigen Fragments erforderlich war. Wenn das Herunterladen eines 10-MB-Segments beispielsweise 8 Sekunden dauert, stellt TVSDK diese Informationen bereit, teilt Ihnen jedoch nicht mit, dass der Download des gesamten Fragments 4 Sekunden bis zum ersten Byte und weitere 4 Sekunden dauerte. </p> </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration </span> </td> 
      <td colname="col1"> <span class="codeph"> long </span> </td> 
      <td colname="col2"> Die Mediendauer der heruntergeladenen Fragmente in Millisekunden. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> periodIndex </span> </td> 
      <td colname="col1"> <span class="codeph"> int </span> </td> 
      <td colname="col2"> Der Timeline-Zeitraumindex, der mit der heruntergeladenen Ressource verknüpft ist. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> size </span> </td> 
      <td colname="col1"> <span class="codeph"> long </span> </td> 
      <td colname="col2"> Die Größe der heruntergeladenen Ressource in Byte. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex </span> </td> 
      <td colname="col1"> <span class="codeph"> int </span> </td> 
      <td colname="col2"> Der Index der entsprechenden Spur, sofern bekannt; andernfalls 0. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackName </span> </td> 
      <td colname="col1"> <span class="codeph"> Zeichenfolge </span> </td> 
      <td colname="col2"> Der Name des entsprechenden Tracks, sofern bekannt; andernfalls null. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackType </span> </td> 
      <td colname="col1"> <span class="codeph"> Zeichenfolge </span> </td> 
      <td colname="col2"> Der Typ des entsprechenden Tracks, sofern bekannt; andernfalls null. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> type </span> </td> 
      <td colname="col1"> <span class="codeph"> Zeichenfolge </span> </td> 
      <td colname="col2"> Was TVSDK heruntergeladen hat. Eine der folgenden Optionen: 
      <ul id="ul_9C3BDEBD878544DA95C7FF81114F9B5C"> 
      <li id="li_A093552B492A44FD8B30785E465F6886">MANIFEST - Eine Wiedergabeliste/ein Manifest </li> 
      <li id="li_DEF9AC71AA564F9BB4C5D4E834432EE5">FRAGMENT - Ein Fragment </li> 
      <li id="li_57821F47B6F04CD38570BCE6447A01B8">TRACK - Ein Fragment, das mit einem bestimmten Track verknüpft ist </li> 
      </ul> Manchmal ist es möglicherweise nicht möglich, den Ressourcentyp zu erkennen. Tritt dies ein, wird die DATEI zurückgegeben. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> url </span> </td> 
      <td colname="col1"> <span class="codeph"> Zeichenfolge </span> </td> 
      <td colname="col2"> Die URL, die auf die heruntergeladene Ressource verweist. </td> 
      </tr> 
    </tbody> 
   </table>
