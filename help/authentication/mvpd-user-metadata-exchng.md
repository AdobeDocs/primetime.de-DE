---
title: MVPD-Benutzermetadaten-Exchange
description: MVPD-Benutzermetadaten-Exchange
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---


# MVPD-Benutzermetadaten-Exchange

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Einführung {#intro-user-metadata-exchange}

MVPDs verwalten benutzerspezifische Metadaten über ihre Kunden, die in einigen Fällen für Programmierer freigegeben werden. Ziel der Adobe Primetime-Authentifizierung ist es, einen Austausch dieser &quot;Benutzermetadaten&quot;zu vermitteln, aber keine Regeln für den Austausch durchzusetzen. Die Austauschregeln sollen es MVPDs ermöglichen, mit ihren Programmierungspartnern zusammenzuarbeiten.

Zu den für den Austausch verfügbaren Metadatentypen für Benutzer gehören derzeit die folgenden:

* Postleitzahl
* Maximale Bewertung (VChip oder MPAA)
* Benutzer-ID
* Haushalts-ID
* Kanal-ID

Mithilfe dieser Funktion können MVPDs und Programmierer spezielle Anwendungsfälle wie die elterliche Kontrolle implementieren. Beispielsweise kann ein MVPD elterliche Bewertungsdaten an einen Programmierer übergeben, der diese Daten verwendet, um verfügbare Anzeigeoptionen für einen Benutzer zu filtern.

Wichtige Punkte zu Benutzermetadaten:

* Der MVPD übergibt Benutzermetadaten während der Authentifizierungs- und Autorisierungsflüsse an die Anwendung des Programmierers.
* Die Adobe Primetime-Authentifizierung speichert die Metadatenwerte in den AuthN- und AuthZ-Token
* Die Adobe Primetime-Authentifizierung kann Werte für MVPDs normalisieren, die Benutzermetadaten in verschiedenen Formaten bereitstellen
* Einige Parameter können mit dem Schlüssel des Programmierers verschlüsselt werden
* Spezifische Werte werden von Adobe über eine Konfigurationsänderung zur Verfügung gestellt

>[!NOTE]
>
>Benutzermetadaten sind eine Erweiterung der statischen Metadaten (Authentifizierungstoken TTL, Autorisierungstoken TTL und Geräte-ID), die zuvor in der Adobe Primetime-Authentifizierung verfügbar waren.

## Beispiele {#example-mvpd-user-metadata-exch}

### Elternkontrolle {#example-parental-control}

Dieses Beispiel zeigt den Austausch der folgenden Elemente:

* [Programming to MVPD Metadata Exchange](#progr-mvpd-metadata-exch)

* [MVPD-to-Programmierer-Metadatenaustauschfluss](#mvpd-progr-exchange-flow)

### Programming to MVPD Metadata Exchange {#progr-mvpd-metadata-exch}

Derzeit unterstützen die Programmierer-API, die Adobe Primetime-Authentifizierung und MVPD-Autorisierer nur die Autorisierung auf Kanalebene. Der Kanal wird als Nur-Text-Zeichenfolge im getAuthorization() -API-Aufruf des Programmierers angegeben. Diese Zeichenfolge wird bis zum autorisierenden Backend des MVPD übertragen:

Aus der App oder Site des Programmierers wählt der Benutzer einen XACML-fähigen MVPD (in diesem Beispiel &quot;TNT&quot;). Informationen zu XACML finden Sie unter [eXtensible Access Control Markup Language](https://en.wikipedia.org/wiki/XACML){target=_blank}.
Das Programm des Programmierers erstellt eine AuthZ-Anfrage, die die Ressource und ihre Metadaten enthält.  Dieses Beispiel enthält eine MPAA-Bewertung von &quot;pg&quot;im Medienattribut des Kanalelements:

```XML
var resource = '<rss version="2.0" xmlns:media="http://video.search.yahoo.com/mrss/">
                    <channel> 
                        <title>TNT</title> 
                        <media:rating scheme="urn:mpaa">pg</media:rating>
                    </channel>
                </rss>';
getAuthorization(resource);
```

Die Adobe Primetime-Authentifizierung unterstützt eine detailliertere Autorisierung bis hin zur Asset-Ebene, wenn sie sowohl vom MVPD als auch vom Programmierer unterstützt wird. Die Ressource und ihre Metadaten sind für die Adobe opak. Ziel ist es, ein Standardformat für die normalisierte Angabe der Ressourcen-ID und Metadaten festzulegen, um Ressourcen-IDs an verschiedene MVPDs zu senden.

>[!NOTE]
>
>Wenn der Benutzer einen nur kanalfähigen MVPD auswählt, extrahiert die Adobe Primetime-Authentifizierung NUR den Kanaltitel (&quot;TNT&quot;im obigen Beispiel) und übergibt nur den Titel an den MVPD.

### MVPD-to-Programmierer-Metadatenaustauschfluss {#mvpd-progr-exchange-flow}

Bei der Adobe Primetime-Authentifizierung werden die folgenden Annahmen getroffen:

* Der MVPD sendet die maximale Bewertung als Teil der SAML-Antwort
* Diese Informationen werden als Teil des Authentifizierungstokens gespeichert.
* Eine API wird durch die Adobe Primetime-Authentifizierung bereitgestellt, damit Programmierer diese Informationen abrufen können
* Programmierer implementieren diese Funktion auf ihrer Website oder in ihrer App (um beispielsweise Videos auszublenden, die über der maximalen Bewertung für den Benutzer liegen)

```XML
<saml:Assertion ID="pfxec5f92e0-8589-3fc3-c708-f4fb8e2fad59"
                 IssueInstant="2010-07-20T10:05:41Z" Version="2.0"
                 xmlns:xs="http://www.w3.org/2001/XMLSchema"
                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <saml:AttributeStatement>
        <saml:Attribute
                Name="MaxTVRating"
                NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
            <saml:AttributeValue xsi:type="xs:string">tv-ma</saml:AttributeValue>
        </saml:Attribute>
        <saml:Attribute
                Name="MaxMovieRating"
                NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
            <saml:AttributeValue xsi:type="xs:string">nc-17</saml:AttributeValue>
        </saml:Attribute>
    </saml:AttributeStatement>
</saml:Assertion>
```

### Hinweise {#notes-mvpd-progr-metadata-exch-flow}

**Ressourcennormalisierung und -validierung.** Ressourcen-IDs können als einfache Zeichenfolge oder als MRSS-Zeichenfolge übergeben werden. Ein Programmierer kann entweder das Nur-String-Format oder das MRSS verwenden, benötigt jedoch eine vorherige Vereinbarung mit dem MVPD, damit der MVPD weiß, wie diese Ressource zu behandeln ist.

**Ressourcen-ID und Metadatenspezifikation.** Die Adobe Primetime-Authentifizierung verwendet den RSS-Standard mit der Media RSS-Erweiterung, um eine Ressource und deren Metadaten anzugeben. In Verbindung mit der Media RSS-Erweiterung unterstützt die Adobe Primetime-Authentifizierung eine Vielzahl von Metadaten, z. B. elterliche Steuerelemente (über `<media:rating>`) oder Geolocation (`<media:location>`).

Die Adobe Primetime-Authentifizierung kann auch eine transparente Konvertierung von der Legacy-Kanalzeichenfolge in die entsprechende RSS-Ressource für MVPDs unterstützen, die RSS erfordern. Andernfalls unterstützt die Adobe Primetime-Authentifizierung die Konvertierung von RSS+MRSS in den reinen Kanaltitel für nur kanalübergreifende MVPDs.

**Die Adobe Primetime-Authentifizierung stellt eine vollständige Abwärtskompatibilität mit bestehenden Integrationen sicher.** Das heißt, für Programmierer, die eine Authentifizierung auf Kanalebene verwenden, sorgt die Adobe Primetime-Authentifizierung dafür, die Kanalkennung im erforderlichen Format zu verpacken, bevor sie an ein MVPD gesendet wird, das dieses Format versteht. Das Gegenteil gilt auch: Wenn ein Programmierer alle seine Ressourcen in einem neuen Format angibt, übersetzt die Adobe Primetime-Authentifizierung das neue Format in eine einfache Kanalzeichenfolge, wenn sie für eine MVPD autorisiert wird, die nur eine Kanalebenenautorisierung durchführt.

## Anwendungsfälle für Benutzermetadaten {#user-metadata-use-cases}

Anwendungsfälle ändern sich ständig und erweitern sich, da mehr MVPDs rechtliche Vorkehrungen treffen und Funktionen hinzufügen. Im Folgenden finden Sie Beispiele dafür, wofür Benutzermetadaten verwendet werden können.

* [MVPD-Benutzer-ID](#mvpd-user-id)
* [Haushalts-ID](#household-user-id)
* [Postleitzahl](#zip-code)
* [Max Rating (Elternkontrolle)](#max-rating-parental-control)
* [Kanalverbindung](#channel-line-up)

### MVPD-Benutzer-ID {#mvpd-user-id}

* Wie vom MVPD bereitgestellt
* Nicht die tatsächlichen Anmeldeinformationen des Benutzers, da sie vom MVPD gehasht werden
* Kann verwendet werden, um Probleme mit oder für bestimmte Benutzer anzuzeigen
* Verschlüsselt
* MVPD-Unterstützung: Alle MVPDs

### Haushalts-Benutzer-ID {#household-user-id}

* Ermöglicht gute Metrikinformationen
* Verschlüsselt
* MVPD-Unterstützung: Einige MVPDs

### Postleitzahl {#zip-code}

* Postleitzahl der Rechnungsstellung des Benutzers
* Wird hauptsächlich verwendet, um die Regeln zum Einfrieren von Ereignissen zu erzwingen.
* Kann mit der AuthZ-Antwort für schnelle Aktualisierungen bereitgestellt werden
* MVPD-Unterstützung: Einige MVPDs

### Max Rating (Elternkontrolle) {#max-rating-parental-control}

* AuthN anfangs, plus AuthZ-Aktualisierung
* Inhalt aus der Benutzeroberfläche filtern
* MPAA- oder VChip-Bewertungen
* MVPD-Unterstützung: Einige MVPDs

### Kanalverbindung {#channel-line-up}

* MVPDs können eine Liste von Kanälen bereitstellen, die der Benutzer anzeigen darf
* Ermöglicht schnelles Zeichnen in der Benutzeroberfläche
* Die OLCA-Spezifikation ermöglicht dies als AttributeStatement in der AuthN-Antwort
* Unterstützende MVPDs: Einige MVPDs

<!--
>[!RELATEDINFORMATION]
>
>* [Proxy MVPD Web Service](/help/authentication/proxy-mvpd-webserv.md)
>* [Content Metadata Exhange](/help/authentication/mvpd-content-metadata-exchange.md)
>* [OLCA AuthN / AuthZ Specification](https://www.cablelabs.com/specifications/CL-SP-AUTH1.0-I04-120621.pdf){target=_blank}
>* [User Metadata (Programmer Integration Guide)](/help/authentication/user-metadata-feature.md)
-->
