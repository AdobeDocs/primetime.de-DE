---
description: Die Regel "Normalisieren"definiert eine URL-Transformation, die auf eine Quell-URL angewendet wird, die aus einer VAST-/VMAP-Antwort stammt.
keywords: Normalisierungsregel;kreative Auswahlregeln
title: Regeln normalisieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Normalisieren von Regeln {#normalize-rules}

Die Regel &quot;Normalisieren&quot;definiert eine URL-Transformation, die auf eine Quell-URL angewendet wird, die aus einer VAST-/VMAP-Antwort stammt.

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
   <td>Der Wert muss immer <span class="codeph"> normalize</span> sein.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Zeichenfolge</span></td> 
   <td><span class="codeph"> host</span></td> 
   <td>Derzeit wird nur der Eintrag <span class="codeph"> host</span> unterstützt. Dieses Attribut muss vorhanden sein, wenn <span class="codeph"> Übereinstimmungen</span> und <span class="codeph"> Werte</span>-Attribute definiert sind.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> match</span></td> 
   <td></td> 
   <td></td> 
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
   <td><span class="codeph"> Werte</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td>TVSDK verwendet das Attribut <span class="codeph"> stimmt mit</span> im <span class="codeph">-Element</span> des Quellkreativs überein und stimmt mit den in diesem Array definierten Werten überein.</td> 
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

