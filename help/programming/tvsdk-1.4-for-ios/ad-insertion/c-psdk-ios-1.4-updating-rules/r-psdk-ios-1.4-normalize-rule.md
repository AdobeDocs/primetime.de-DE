---
description: Die Normalisierungsregel definiert eine URL-Transformation, die auf eine Quell-Kreativ-URL angewendet wird, die von einer VAST-/VMAP-Antwort erhalten wurde.
keywords: Normalisierungsregel; kreative Auswahlregeln
title: Regeln normalisieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Regeln normalisieren{#normalize-rules}

Die Normalisierungsregel definiert eine URL-Transformation, die auf eine Quell-Kreativ-URL angewendet wird, die von einer VAST-/VMAP-Antwort erhalten wurde.

## Die Regel &quot;Normalisieren&quot;verfügt über die folgenden Attribute und möglichen Werte:

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
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> normalisieren</span></td> 
   <td>Der Wert muss immer <span class="codeph"> normalisieren</span>.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> Host</span></td> 
   <td>Derzeit nur <span class="codeph"> Host</span> wird unterstützt. Dieses Attribut muss vorhanden sein, wenn <span class="codeph"> matches</span> und <span class="codeph"> values</span> -Attribute definiert werden.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> matches</span></td> 
   <td></td> 
   <td></td> 
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
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td>TVSDK verwendet die <span class="codeph"> matches</span> -Attribut in der <span class="codeph"> item</span> des Quell-Kreativelements erstellen und mit den in diesem Array definierten Werten übereinstimmen.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> find</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Ein regulärer Ausdruck, der auf die zu vergleichende Quell-Kreativ-URL angewendet wird.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> replace</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Ein regulärer Ausdruck, der auf die Quell-Kreativ-URL angewendet wird, die basierend auf der Übereinstimmung ersetzt werden soll.</td> 
  </tr> 
 </tbody> 
</table>

```
{
    "ads": {
        "rules": {
            "default": [
                {
                ...
                }
                {
                    "
<b>type</b>": "
<b>normalize</b>",
                    "
<b>item</b>": "host",
                    "
<b>matches</b>": "ew",
                    "
<b>values</b>": [
                        "redirector.gvt1.com"
                    ],
                    "
<b>find</b>": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "
<b>replace</b>": "videoplayback/$1/expire//$2/signature//"
                }                
            ]
        }
    }
}
```
