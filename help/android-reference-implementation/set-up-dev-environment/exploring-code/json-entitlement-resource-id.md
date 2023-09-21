---
title: JSON-Objekt für Kennung der Berechtigungsressource
description: Der folgende Codeblock bietet ein Beispiel für ein JSON-Objekt, wenn die Kennung der Berechtigungsressource eine einfache Textzeichenfolge ist.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# JSON-Objekt für Kennung der Berechtigungsressource {#json-object-for-entitlement-resource-id}

Der folgende Codeblock bietet ein Beispiel für ein JSON-Objekt, wenn die Kennung der Berechtigungsressource eine einfache Textzeichenfolge ist. In diesem Fall ist die Ressourcen-ID die Zeichenfolge &quot;resource&quot;.

```
"metadata" : { 
"entitlement" : { 
"id" : "resource" 
} 
}
```

Der folgende Codeblock bietet ein Beispiel für ein JSON-Objekt, wenn die Kennung der Berechtigungsressource eine HTML-kodierte mRSS-Zeichenfolge ist.

```
<rss version="2.0" xmlns:media="https://search.yahoo.com/mrss/"> 
<channel> 
<title>REF_ADOBE</title> 
<item> 
<title>Adobe Primetime Reference</title> 
<guid>1234</guid> 
<media:rating scheme="urn:v-chip">TV-PG</media:rating> 
</item> 
</channel> 
</rss>
```

Die folgende mRSS-Zeichenfolge wird als Ressourcen-ID verwendet.

```
"metadata" : { 
    "entitlement" : { 
        "id" : "<rss version=&quot;2.0&quot; 
        xmlns:media=&quot; 
        https://search.yahoo.com/mrss/&quot; 
        ><channel><title>REF_ADOBE</title><item> 
        <title>Adobe Primetime Reference</title><guid> 
        1234</guid><media:rating scheme=&quot;urn:v-chip&quot;> 
        TV-PG</media:rating></item></channel></rss>" 
        } 
} 
```
