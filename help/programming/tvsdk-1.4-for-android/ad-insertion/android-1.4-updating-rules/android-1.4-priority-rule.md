---
description: Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.
keywords: priority rule;creative selection rules
seo-description: Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.
seo-title: Prioritätsregeln
title: Prioritätsregeln
uuid: 6aa5822a-a3c0-49b2-b25b-0308a784e405
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Prioritätsregeln{#priority-rules}

Die Prioritätsregel definiert die Prioritätsreihenfolge der Werbeinhalte, die für die Wiedergabe aus einer VAST-/VMAP-Antwort ausgewählt werden.

**Tabelle 1: Eine Prioritätsregel verfügt über die folgenden Attribute und möglichen Werte:**

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"> Schlüssel</th> 
   <th class="entry"> Typ</th> 
   <th class="entry"> Werte</th> 
   <th class="entry"> Beschreibung</th> 
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

