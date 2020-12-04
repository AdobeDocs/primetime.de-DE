---
description: Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.
keywords: priority rule;creative selection rules
seo-description: Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.
seo-title: Prioritätsregeln
title: Prioritätsregeln
uuid: 20dd0ded-06dd-427d-8dd3-79f9f8a3390c
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Prioritätsregeln {#priority-rules}

Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.

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
   <td><span class="codeph"> Priorität</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> Ein Array mit Kleinbuchstaben-MIME-Typen, die die Priorität festlegen, in der Quellkreative für die Wiedergabe ausgewählt werden müssen.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> host</span></td> 
   <td>Derzeit wird nur der Eintrag <span class="codeph"> host</span> unterstützt. Dieses Attribut muss vorhanden sein, wenn <span class="codeph"> Übereinstimmungen</span> und <span class="codeph"> Werte</span>-Attribute definiert sind.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> match</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> multiple</span></td> 
   <td>Mögliche Werte:
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - gleich</li> 
     <li><span class="codeph"> ne</span> - nicht gleich</li> 
     <li><span class="codeph"> co</span> - enthält</li> 
     <li><span class="codeph"> nc</span> - enthält nicht</li> 
     <li><span class="codeph"> sw</span>  - Beginn mit</li> 
     <li><span class="codeph"> new</span>  - endet mit</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> Priorität</span></td> 
   <td>Der Wert muss immer <span class="codeph"> Priorität</span> haben</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> Werte</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> <p>TVSDK verwendet das Attribut <span class="codeph"> stimmt mit </span> überein mit dem <span class="codeph">-Element</span> des Quellkreativen und stimmt mit den in diesem Array definierten Werten überein</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td></td> 
   <td> <p>Der Wert kann <span class="codeph"> vod</span> oder <span class="codeph"> live</span> sein.</p> </td> 
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
