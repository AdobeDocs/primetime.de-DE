---
description: Die Primetime-Referenzimplementierung verwendet ein JSON-basiertes Feed-Format für Antworten. Dieses Format wird mithilfe einer Implementierung der IFeedItemAdapter-Schnittstelle analysiert.
title: Katalogformat
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---


# Katalogformat {#catalog-format}

Die Primetime-Referenzimplementierung verwendet ein JSON-basiertes Feed-Format für Antworten. Dieses Format wird mithilfe einer Implementierung der IFeedItemAdapter-Schnittstelle analysiert.

>[!NOTE]
>
>Dieses Feed-Format ist das Musterformat, das die Referenz-Implementierung verwendet, und dient als Beispiel dafür, wie das Format analysiert und der Feed-Schnittstelle zugeordnet werden kann. Sie können Ihr eigenes Eingabefeed-Format mit Ihren eigenen Implementierungen der Feed-Oberfläche verwenden.

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
| `id` | Eine eindeutige Kennung/Anleitung für den Inhalt, wie vom Feed-Veröffentlichungssystem festgelegt. |
| `title` | Ein Titel für den Inhalt. |
| `description` | Eine Beschreibung des Inhalts. |
| `categories` | Eine Liste von Kategorien, die für den Inhalt getaggt sind und von der Anwendung verwendet werden können, um das Benutzererlebnis zu verbessern. Lesen Sie in die Eigenschaften für den Inhalt. |
| `keywords` | Eine Liste von durch Kommas getrennten Suchbegriffen kann von der Anwendung verwendet werden, um das Benutzererlebnis zu verbessern. Lesen Sie in die Eigenschaften für den Inhalt. |
| `isLive` | &quot;true&quot;oder &quot;false&quot;, was angibt, ob es sich um einen Live- oder VOD-Stream handelt. |
| `content` | Ein Array von JSON-Objekten mit alternativen Formaten für den Inhalt zusammen mit den entsprechenden URLs. Beispielsweise könnten URLs für die Formate f4m und m3u8 vorhanden sein. Die JSON-Objektattribute werden weiter unten beschrieben. |
| `thumbnails` | Ein Array von JSON-Objekten mit URLs für verschiedene Miniaturansichten. Die JSON-Objektattribute werden unten definiert. |
| `metadata` | Ein JSON-Objekt, das Metadaten für den Inhalt definiert. Derzeit sind diese Metadaten auf adbezogene Metadaten beschränkt. Das Metadatenobjekt wird unten definiert. |

Der folgende Codeblock definiert die JSON-Objekte, die das Array von **content-Objekten** bilden:

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
| format | Muss das Format m3u8 für Android haben. |
| url | Die URL zum Videostream für das angegebene Format. |

Der folgende Codeblock definiert die JSON-Objekte, die das Array von **Miniaturansichtsobjekten** bilden:

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
| format | Eine Zeichenfolge, die das Format der Miniaturansichtsdatei angibt, z. B. JPEG, PNG usw. |
| height | Die Höhe der Miniaturansicht. In der Referenzanwendung wird die Miniaturansicht mit der kleinsten Höhe und Breite als kleine Miniaturansicht und die Miniaturansicht mit der größten Breite und Höhe als große Miniaturansicht zurückgegeben. |
| width | Die Breite der Miniaturansicht. In der Referenzanwendung wird die Miniaturansicht mit der kleinsten Höhe und Breite als kleine Miniaturansicht und die Miniaturansicht mit der größten Breite und Höhe als große Miniaturansicht zurückgegeben. |
| url | Die URL zur Miniaturansicht-Datei. |

Der folgende Codeblock definiert das **Metadatenobjekt**:

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
| ad | Anzeigenbezogene Metadaten. |
| type | Der Wert kann Primetime Ads, Direct Ad Breaks oder Custom Ad Markers sein. <br/><br/>Das PSDK bietet integrierte Unterstützung für die folgenden Metadatentypen: Auditude-bezogene Metadaten für Primetime Ad Serving (Primetime Ads), direkte Werbeunterbrechungen mit Anzeigen-URLs (Direct Ad Breaks) und benutzerdefinierte Anzeigenmarken, die den TimeRange für jede Anzeigenmarke bereitstellen (benutzerdefinierte Anzeigenmarken). Jeder Typ verfügt über einen integrierten AdProvider im PSDK, der die Metadaten verarbeitet.  <br/><br/>Das JSON-Format für diese beiden wurden nachfolgend definiert. |
| details | Umfasst die Attribute der Anzeigenmetadaten. Beide Arten von Anzeigenmetadaten haben ihren eigenen Satz von Attributen, der unten definiert wird. Für die integrierten Typen definieren die enthaltenen Attribute die vom PSDK für diesen Typ erwarteten Daten. |
| Berechtigung | Berechtigungsbezogene Metadaten |
| id | Medienressource-ID, die für Autorisierungsanfragen gegen den Adobe Primetime Pay-TV-Pass-Dienst verwendet wird. Die ID kann entweder eine Textzeichenfolge oder eine HTML-kodierte mRSS-Zeichenfolge sein. Medieninhalte, für die eine Autorisierung erforderlich ist, müssen eine gültige Ressourcen-ID enthalten. |

