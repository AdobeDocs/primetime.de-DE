---
description: Die Primetime-Referenzimplementierung verwendet ein JSON-basiertes Feed-Format für Antworten. Dieses Format wird mithilfe einer Implementierung der IFeedItemAdapter-Schnittstelle analysiert.
title: Katalogformat
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Katalogformat {#catalog-format}

Die Primetime-Referenzimplementierung verwendet ein JSON-basiertes Feed-Format für Antworten. Dieses Format wird mithilfe einer Implementierung der IFeedItemAdapter-Schnittstelle analysiert.

>[!NOTE]
>
>Dieses Feed-Format ist das Beispielformat, das die Referenzimplementierung verwendet und dient als Beispiel dafür, wie das Format analysiert und der Feed-Oberfläche zugeordnet werden kann. Sie können Ihr eigenes Eingabe-Feed-Format mit Ihren eigenen Implementierungen der Feed-Oberfläche verwenden.

Auf hoher Ebene besteht das Format aus einem Array von Inhaltseinträgen. Jeder Eintrag stellt einen Live- oder VOD-veröffentlichten Videoinhalt dar:

```
{
    "entries": [
        {
        },
        {
        },
        ...
    ]
}
```

Jeder Feed-Eintrag ist ein JSON-Objekt mit einem bestimmten Satz von Attributen:

```
{
    "entries": [
        
            "id": "episode1",
            "title": "My episode1",
            "description": "This is an episode.",
            "categories": "documentary, educational, children",
            "keywords": "List, of, comma, separated, keywords",
            "isLive": false,
            "content":  [
                
                },
                
                },
            ],
            "thumbnails": [
                
                },
                
                }
            ]
            "metadata": 
            } 
        }
    ]
}
```

| Eigenschaft | Beschreibung |
|---|---|
| `id` | Eine eindeutige Kennung/Anleitung für den Inhalt, wie vom Feed-Publishing-System festgelegt. |
| `title` | Ein Titel für den Inhalt. |
| `description` | Eine Beschreibung des Inhalts. |
| `categories` | Eine Liste der Kategorien, die mit dem Inhalt getaggt sind und von der Anwendung zur Verbesserung des Benutzererlebnisses verwendet werden können. Lesen Sie die Eigenschaften für den Inhalt. |
| `keywords` | Eine Liste mit durch Kommas getrennten Keywords kann von der Anwendung verwendet werden, um das Benutzererlebnis zu verbessern. Lesen Sie die Eigenschaften für den Inhalt. |
| `isLive` | &quot;true&quot;oder &quot;false&quot;, was angibt, ob es sich um einen Live- oder VOD-Stream handelt. |
| `content` | Ein Array von JSON-Objekten mit alternativen Formaten für den Inhalt zusammen mit den entsprechenden URLs. Beispielsweise könnte es URLs für die Formate f4m und m3u8 geben. Die JSON-Objektattribute werden weiter unten beschrieben. |
| `thumbnails` | Ein Array von JSON-Objekten mit URLs für unterschiedliche Größe von Miniaturansichten. Die JSON-Objektattribute sind unten definiert. |
| `metadata` | Ein JSON-Objekt, das Metadaten für den Inhalt definiert. Derzeit sind diese Metadaten auf anzeigenbezogene Metadaten beschränkt. Das Metadatenobjekt wird unten definiert. |

Der folgende Codeblock definiert die JSON-Objekte, aus denen das Array von **Content-Objekte**:

```
"content":  [
    {
        "format": "M3U8",
        "url": "https://adobeprimetime-f.akamaihd.net/i/
<i>longstringofcharacters</i>/
                 Episode_,640x360_1000,640x360_700,_b.mp4.csmil/master.m3u8",
        "language": "en"
    }  
],
```

| Eigenschaft | Beschreibung |
|--- |--- |
| format | Muss das m3u8-Format für Android sein. |
| url | Die URL zum Videostream für das angegebene Format. |

Der folgende Codeblock definiert die JSON-Objekte, aus denen das Array von **Miniaturansichtsobjekte**:

```
"thumbnails": [
    {
        "format": "JPEG",
        "height":  "90",
        "width": "160",
        "url": "https://example.com/small.jpg"
    },
    {
        "format": "JPEG",
        "height": "450",
        "width": "800",
        "url": "https://example.com/large.jpg"
    }
],
```

| Eigenschaft | Beschreibung |
|---|---|
| format | Eine Zeichenfolge, die das Format der Miniaturdatei angibt, z. B. JPEG, PNG usw. |
| height | Die Höhe der Miniaturansicht. In der Referenzanwendung wird die Miniaturansicht mit der kleinsten Höhe und Breite als kleine Miniaturansicht zurückgegeben und die Miniaturansicht mit der größten Breite und Höhe wird als große Miniaturansicht zurückgegeben. |
| width | Die Breite der Miniaturansicht. In der Referenzanwendung wird die Miniaturansicht mit der kleinsten Höhe und Breite als kleine Miniaturansicht zurückgegeben und die Miniaturansicht mit der größten Breite und Höhe wird als große Miniaturansicht zurückgegeben. |
| url | Die URL zur Miniaturansicht-Datei. |

Der folgende Codeblock definiert die **Metadatenobjekt**:

```
"metadata" : {
    "ad" : {
        "type" : "",
        "details" : {
        }
    }
    "entitlement" : {
        "id" : ""
    }
}
```

| Eigenschaft | Beschreibung |
|--- |--- |
| Anzeige | Anzeigenbezogene Metadaten. |
| type | Der Wert kann Primetime Ads, Direct Ad Breaks oder Custom Ad Markers sein. <br/><br/>Das PSDK bietet integrierte Unterstützung für die folgenden Metadatentypen: Auditude-bezogene Metadaten für Primetime Ad Serving (Primetime Ads), direkte Werbeunterbrechungen mit Anzeigen-URLs (Direct Ad Breaks) und benutzerdefinierte Anzeigenmarken, die den TimeRange für jede Anzeigenmarke (Custom Ad Markers) bereitstellen. Jeder Typ verfügt über einen integrierten AdProvider im PSDK, der die Metadaten verarbeitet.  <br/><br/>Das JSON-Format für jede dieser beiden wurde unten definiert. |
| details | Umfasst die Attribute der Anzeigenmetadaten. Beide Arten von Anzeigenmetadaten verfügen über einen eigenen Satz von Attributen, der unten definiert ist. Für die integrierten Typen definieren die enthaltenen Attribute die Daten, die vom PSDK für diesen Typ erwartet werden. |
| Berechtigung | Berechtigungsbezogene Metadaten |
| id | Media resource ID, die für Autorisierungsanfragen für den Pay-TV-Pass-Dienst von Adobe Primetime verwendet wird. Die ID kann entweder eine Textzeichenfolge oder eine HTML-kodierte mRSS-Zeichenfolge sein. Medieninhalte, für die eine Autorisierung erforderlich ist, müssen eine gültige Ressourcen-ID enthalten. |
