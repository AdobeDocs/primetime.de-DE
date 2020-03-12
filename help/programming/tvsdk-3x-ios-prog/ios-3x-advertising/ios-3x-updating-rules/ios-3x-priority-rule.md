---
description: Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.
keywords: priority rule;creative selection rules
seo-description: Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.
seo-title: Prioritätsregeln
title: Prioritätsregeln
uuid: 86b9d654-c85c-45de-a512-969234c56bef
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Prioritätsregeln {#priority-rules}

Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.

## Eine Prioritätsregel verfügt über die folgenden Attribute und möglichen Werte:

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
   <td>Derzeit wird nur der <span class="codeph"> Host</span> unterstützt. Dieses Attribut muss vorhanden sein, wenn <span class="codeph"> Übereinstimmungen</span> und <span class="codeph"> Wertattribute</span> definiert sind.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> match</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> multiple</span></td> 
   <td>Mögliche Werte:
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - gleich</li> 
     <li><span class="codeph"> ne</span> - nicht gleich</li> 
     <li><span class="codeph"> co</span> - contains</li> 
     <li><span class="codeph"> nc</span> - nicht enthält</li> 
     <li><span class="codeph"> sw</span> - Beginn mit</li> 
     <li><span class="codeph"> new</span> - endet mit</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> Priorität</span></td> 
   <td>Der Wert muss immer <span class="codeph"> Priorität haben</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> Werte</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> <p>TVSDK verwendet das Attribut <span class="codeph"> match</span> für das <span class="codeph"> Element</span> des Quellkrekrekrekrekreativen und stimmt mit den in diesem Array definierten Werten überein.</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td></td> 
   <td> <p>Wert kann <span class="codeph"> vod</span> oder <span class="codeph"> live sein</span></p> </td> 
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
