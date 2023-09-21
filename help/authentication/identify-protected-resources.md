---
title: Ermitteln geschützter Ressourcen
description: Ermitteln geschützter Ressourcen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Ermitteln geschützter Ressourcen {#identifying-protected-resources}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Übersicht {#overview}

Jede Autorisierungsanfrage (oder Anforderung der Autorisierung) muss eine eindeutige Kennung für die geschützte Ressource enthalten, für die der Benutzer Zugriff anfordert. Eine geschützte Ressource kann eine beliebige Ebene autorisierter Inhalte sein, wie zwischen einem MVPD und teilnehmenden Programmierern vereinbart. Potenzielle geschützte Ressourcen müssen in diese Baumstruktur mit zunehmend spezifischer Granularität passen:

- Netzwerk
   - Kanal
      - Anzeigen
         - Folge
            - Asset

</br>

## Medien-RSS-Format {#media_rss}

Ressourcen können durch eine einfache Zeichenfolge (eine eindeutige Kennung für einen Kanal) identifiziert oder im Media RSS-Format (MRSS) dargestellt werden, wie zwischen der Adobe (oder einem autorisierten Adobe Primetime-Authentifizierungspartner) und den teilnehmenden MVPDs und Programmierern vereinbart. Die als Ressourcenspezifikator verwendete RSS-Zeichenfolge kann zusätzliche Informationen wie Bewertungen und Metadaten zur elterlichen Kontrolle enthalten.


Wenn Sie eine einfache Ressourcenkennung wie &quot;TNT&quot;verwenden, wird angenommen, dass diese einen Kanal darstellt und in diesen RSS-Ressourcenbezeichner übersetzt wird:

```RSS
    <rss version="2.0"> 
        <channel>
            <title>TNT</title>
        </channel>
    </rss>
```


Ein komplexerer Bezeichner kann beispielsweise zusätzliche Bewertungsinformationen enthalten. Sie können die gesamte RSS-Zeichenfolge an Access Enabler-Funktionen übergeben, für die eine Ressourcen-ID erforderlich ist, z. B. [`getAuthorization()`](/help/authentication/rest-api-reference.md):

```rss
    var resource = 
        '<rss version="2.0" xmlns:media="http://search.yahoo.com/mrss/"> 
             <channel>
                 <title>TNT</title>
                 <media:rating scheme="urn:mpaa">pg</media:rating>
             </channel>
         </rss>'; 
    getAuthorization(resource);
```

Ressourcenspezifikatoren sind für die Adobe Primetime-Authentifizierung opak und werden einfach an den MVPD weitergeleitet. Wenn der MVPD Ihren Ressourcenbezeichner nicht erkennt oder nicht analysieren kann, wird ein Fehler an die Adobe Primetime-Authentifizierung zurückgegeben, der den Fehler an Ihre `tokenRequestFailed()` Callback.

<!--
## Related Information {#related}

-  User Metadata
-  Preflight Authorization
-->
