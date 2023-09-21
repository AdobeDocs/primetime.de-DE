---
description: Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinformationen, die für die Wiedergabe über eine VAST-/VMAP-Antwort ausgewählt werden.
keywords: Prioritätsregel; kreative Auswahlregeln
title: Prioritätsregeln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Prioritätsregeln {#priority-rules}

Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinformationen, die für die Wiedergabe über eine VAST-/VMAP-Antwort ausgewählt werden.

## Eine Prioritätsregel hat die folgenden Attribute und möglichen Werte:

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"><b>Schlüssel</b></th> 
   <th class="entry"><b>Typ</b></th> 
   <th class="entry"><b>Werte</b></th> 
   <th class="entry"><b>Beschreibung</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> priority</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> Ein Array von MIME-Typen in Kleinbuchstaben, die die Priorität definieren, in der kreative Quellelemente für die Wiedergabe ausgewählt werden müssen.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> Host</span></td> 
   <td>Derzeit nur <span class="codeph"> Host</span> wird unterstützt. Dieses Attribut muss vorhanden sein, wenn <span class="codeph"> matches</span> und <span class="codeph"> values</span> -Attribute definiert werden.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> matches</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> multiple</span></td> 
   <td>Mögliche Werte:
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - gleich</li> 
     <li><span class="codeph"> ne</span> - nicht gleich</li> 
     <li><span class="codeph"> co</span> - enthält</li> 
     <li><span class="codeph"> nc</span> - nicht enthält</li> 
     <li><span class="codeph"> sw</span> - beginnt mit</li> 
     <li><span class="codeph"> ew</span> - endet mit</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> priority</span></td> 
   <td>Der Wert muss immer <span class="codeph"> priority</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> <p>TVSDK verwendet die <span class="codeph"> matches</span> -Attribut in der <span class="codeph"> item</span> des Quell-Kreativ und Übereinstimmung mit den in diesem Array definierten Werten</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td></td> 
   <td> <p>Wert kann <span class="codeph"> vod</span> oder <span class="codeph"> live</span></p> </td> 
  </tr> 
 </tbody> 
</table>

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "
<b>type</b>": "
<b>priority</b>",
                    "
<b>stream</b>": "vod",
                    "
<b>priority</b>": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    ...
                },
            ]
        }
    }
}
```
