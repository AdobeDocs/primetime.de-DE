---
title: Vermeiden Sie die Verwendung von '&'reg_code in /authenticate request
description: Vermeiden Sie die Verwendung von '&'reg_code in /authenticate request
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Vermeiden Sie die Verwendung von &#39;&amp;&#39;reg_code in /authenticate request {#clientless-avoid-using-reg_code-in-authenticate-request}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

</br>



## Problem

Der IE 9-Browser interpretiert &quot;\®&quot;als speziellen Befehl und konvertiert ihn in ®. 

## Erklärung

Wenn die Variable `/authenticate` -Anfrage stellt sich wie folgt zusammen...

 

```
    <FQDN>authenticate? requestor_id=someRequestor&reg_code=EKAFMFI&domain_name=someRequestor.com&noflash=true&mso_id=someMvpd&redirect_url=someRequestor.redirect.url.html
```
 

...wird wie unten gezeigt vom IE-Browser interpretiert und in diesem Format an Adobe gesendet:

 

```
    <FQDN>authenticate?requestor_id=someRequestor&reg;_code=EKAFMFI&domain_name=someRequestor.com&noflash=true&mso_id=someMvpd&redirect_url=someRequestor.redirect.url.html
```
 

Der Anforderer\_id wird als univision®\_code=EKAFMFI interpretiert, da es kein &quot;&amp;&quot;gibt und die Adobe keine `regCode` param , mit dem das Token verknüpft werden soll.  Es besteht die Möglichkeit, dass das AuthN-Token überhaupt nicht erstellt wird. In diesem Fall `/checkauthn` -Aufrufe können keine Token finden.



## Lösung

Eine der folgenden Optionen sollte dieses Problem beheben:

1. Vermeiden Sie die Verwendung der `&reg_code` -Parameter zwischen den anderen Abfragezeichenfolgen-Parametern.  Verschieben Sie sie stattdessen in den ersten Abfragezeichenfolgenparameter in der Anforderungs-URL, sodass die Anforderungs-URL wie folgt lautet:\
    

       &lt;fqdn>authenticate?reg_code =EKAFMFI&amp;requestor_id=someRequestor&amp;domain_name=someRequestor.com&amp;noflash=true&amp;mso_id=someMvpd&amp;redirect_url=someRequestor.redirect.url.html
   

   Auf diese Weise wird die `&reg` param wird nicht falsch interpretiert.

1. Normalisieren `&reg_code` Verwendung `&amp;reg_code`.

1. Adobe könnte eine neue Funktion einführen, mit der ein Fehlercode als Reaktion auf einen Authentifizierungsaufruf an den zweiten Bildschirm zurückgesendet werden kann, wenn die AuthN-Token-Erstellung fehlgeschlagen ist.

