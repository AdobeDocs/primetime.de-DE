---
description: Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
seo-description: Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
seo-title: Verfolgen auf Fragmentebene mithilfe der Ladeinformationen
title: Verfolgen auf Fragmentebene mithilfe der Ladeinformationen
uuid: a6572823-d525-4ce0-806a-3feb20678cb0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Verfolgen auf Fragmentebene mithilfe der Ladeinformationen{#track-at-the-fragment-level-using-load-information}

Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

TVSDK bietet außerdem Informationen zu den folgenden heruntergeladenen Ressourcen:

1. Playlist-/Manifestdateien
1. Dateifragmente
1. Dateiverfolgung

   Sie können Servicequalitätsinformationen (QoS) zu heruntergeladenen Ressourcen wie Fragmenten und Spuren von der `LoadInfo`-Klasse lesen.

1. Implementieren Sie den `onLoadInfo`-Callback-Ereignis-Listener.
1. Registrieren Sie den Ereignis-Listener, den TVSDK jedes Mal aufruft, wenn ein Fragment heruntergeladen wurde.
1. Lesen Sie die Daten von Interesse aus dem Parameter `LoadInfo`, der an den Rückruf übergeben wird.

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
      <td colname="col01"> <span class="codeph"> downloadDuration  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> <p>Die Dauer des Downloads in Millisekunden. </p> <p>TVSDK unterscheidet nicht zwischen der Zeit, die der Client für die Verbindung mit dem Server benötigt hat, und der Zeit, die es zum Herunterladen des vollständigen Fragments dauerte. Wenn das Herunterladen eines Segments mit 10 MB z. B. 8 Sekunden in Anspruch nimmt, gibt TVSDK diese Informationen an, teilt Ihnen jedoch nicht mit, dass es bis zum ersten Byte 4 Sekunden und bis zum Herunterladen des gesamten Fragments weitere 4 Sekunden dauerte. </p> </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> Die Mediendauer der heruntergeladenen Fragmente in Millisekunden. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> periodIndex  </span> </td> 
      <td colname="col1"> <span class="codeph"> int  </span> </td> 
      <td colname="col2"> Der mit der heruntergeladenen Ressource verknüpfte Timeline-Zeitraum. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> size  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> Die Größe der heruntergeladenen Ressource in Byte. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex  </span> </td> 
      <td colname="col1"> <span class="codeph"> int  </span> </td> 
      <td colname="col2"> der Index der entsprechenden Spur, sofern bekannt; andernfalls 0. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackName  </span> </td> 
      <td colname="col1"> <span class="codeph"> Zeichenfolge  </span> </td> 
      <td colname="col2"> Name der entsprechenden Spur, sofern bekannt; ansonsten null. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackType  </span> </td> 
      <td colname="col1"> <span class="codeph"> Zeichenfolge  </span> </td> 
      <td colname="col2"> Typ der entsprechenden Strecke, sofern bekannt; ansonsten null. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> type  </span> </td> 
      <td colname="col1"> <span class="codeph"> Zeichenfolge  </span> </td> 
      <td colname="col2"> Was TVSDK heruntergeladen hat. Eine der folgenden Möglichkeiten: 
      <ul id="ul_9C3BDEBD878544DA95C7FF81114F9B5C"> 
      <li id="li_A093552B492A44FD8B30785E465F6886">MANIFEST - Eine Wiedergabeliste/ein Manifest </li> 
      <li id="li_DEF9AC71AA564F9BB4C5D4E834432EE5">FRAGMENT - Ein Fragment </li> 
      <li id="li_57821F47B6F04CD38570BCE6447A01B8">TRACK - Ein mit einer bestimmten Spur verknüpftes Fragment </li> 
      </ul> Manchmal ist es möglicherweise nicht möglich, den Typ der Ressource zu erkennen. In diesem Fall wird die DATEI zurückgegeben. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> url  </span> </td> 
      <td colname="col1"> <span class="codeph"> Zeichenfolge  </span> </td> 
      <td colname="col2"> Die URL, die auf die heruntergeladene Ressource verweist. </td> 
      </tr> 
    </tbody> 
   </table>
