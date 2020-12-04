---
seo-title: JSON-Objekt für Berechtigungsressourcen-ID
title: JSON-Objekt für Berechtigungsressourcen-ID
uuid: f5b659da-1732-404c-bf00-d32a0ae39aa1
description: Der folgende Codeblock enthält ein Beispiel für ein JSON-Objekt, wenn die Berechtigungsressourcen-ID eine einfache Textzeichenfolge ist.
seo-description: Der folgende Codeblock enthält ein Beispiel für ein JSON-Objekt, wenn die Berechtigungsressourcen-ID eine einfache Textzeichenfolge ist.
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# JSON-Objekt für Berechtigungsressourcen-ID {#json-object-for-entitlement-resource-id}

Der folgende Codeblock enthält ein Beispiel für ein JSON-Objekt, wenn die Berechtigungsressourcen-ID eine einfache Textzeichenfolge ist. In diesem Fall ist die Ressourcen-ID die Zeichenfolge &quot;resource&quot;.

```
"metadata" : { 
"entitlement" : { 
"id" : "resource" 
} 
}
```

Der folgende Codeblock enthält ein Beispiel für ein JSON-Objekt, wenn die Berechtigungsressourcen-ID eine HTML-kodierte mRSS-Zeichenfolge ist.

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
