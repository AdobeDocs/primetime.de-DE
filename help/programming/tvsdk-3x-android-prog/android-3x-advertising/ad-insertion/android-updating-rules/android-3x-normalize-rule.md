---
description: Die Regel "Normalisieren"definiert eine URL-Transformation, die auf eine Quell-URL angewendet wird, die aus einer VAST-/VMAP-Antwort stammt.
keywords: normalize rule;creative selection rules
seo-description: Die Regel "Normalisieren"definiert eine URL-Transformation, die auf eine Quell-URL angewendet wird, die aus einer VAST-/VMAP-Antwort stammt.
seo-title: Regeln normalisieren
title: Regeln normalisieren
uuid: 8511000e-3a8a-42f3-b4be-d069d09112b0
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Regeln normalisieren {#normalize-rules}

Die Regel &quot;Normalisieren&quot;definiert eine URL-Transformation, die auf eine Quell-URL angewendet wird, die aus einer VAST-/VMAP-Antwort stammt.

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
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> normalisieren</span></td> 
   <td>Der Wert muss immer <span class="codeph"> normalisiert</span>sein.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> host</span></td> 
   <td>Derzeit wird nur der <span class="codeph"> Host</span> unterstützt. Dieses Attribut muss vorhanden sein, wenn <span class="codeph"> Übereinstimmungen</span> und <span class="codeph"> Wertattribute</span> definiert sind.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> match</span></td> 
   <td></td> 
   <td></td> 
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
   <td><span class="codeph"> Werte</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td>TVSDK verwendet das Attribut <span class="codeph"> match</span> für das <span class="codeph"> Element</span> des Quell-kreativen Elements und stimmt mit den in diesem Array definierten Werten überein.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> finden</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Ein regulärer Ausdruck, der auf die passende kreative Quell-URL angewendet werden soll.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> ersetzen</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Ein regulärer Ausdruck, der auf die kreative Quellcode-URL angewendet wird, die basierend auf der Übereinstimmung ersetzt werden soll.</td> 
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
