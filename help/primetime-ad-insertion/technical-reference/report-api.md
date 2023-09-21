---
title: Berichts-API
description: Auditude-Bericht-API
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 1%

---

# Berichts-API {#report-api}

Die Benutzeroberfläche verfügt über verwaltete Rollen für Kunden und für das Aktivierungs-(Adobe-)Team. Kunden können auf das Portal zugreifen und dann ihre Konfigurationen erstellen und bearbeiten. Sie können die Berichte auch nach ihren Anzeigenimpressionen auf der Benutzeroberfläche sehen.

APIs helfen Kunden und Administratoren bei der Kommunikation mit der Backend-Infrastruktur.

Erkunden Sie die [!DNL Primetime Ad Insertion] APIs siehe [Ad Insertion-API-Endpunkte in der aggregierten Benutzeroberfläche](https://adconfigservice-va6.cloud.adobe.io/swagger-ui/index.html#/).

## API-Endpunkt {#report-api-endpoint}

### Produktion {#production}

`https://dai-primetime.adobe.io/report`

### Sandbox {#sandbox}

`https://dai-sandbox1-primetime.adobe.io/report`

## Abfrageparameter


| Name | Bedeutung | Werttyp | Erforderlich? | Standardwert | Einschränkungen | Beispiel-/gültige Beispielwerte |
|----------|-----------------------------------------------------------------------------------------------|----------------|----------------|---------------------|------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| endDate | Enddatum für die Berichtsdaten | date | Y | KEINE | nicht neuer als gestern in UTC-8 | ######## |
| Filter | eine oder mehrere Spalten filtern | Zeichenfolge | N | KEINE | ad_config_id , zone_id | ad_config_id=990,900;state=active |
|          |                                                                                               |                |                |                     | Wenn metaData in der Anfrage auf &quot;true&quot;gesetzt ist, können Sie auch nach Namen filtern. |                                                                         |
|          |                                                                                               |                |                |                     |                                                                                    | Mehrere Filterschlüssel sind durch Semikolon getrennt. |
|          |                                                                                               |                |                |                     |                                                                                    | Verwenden Sie kommagetrennte Werte, um eine Liste von Werten für den Filterschlüssel bereitzustellen |
| groupBy | Gruppieren nach Zeit ( Jahr \| Monat \| Tag) oder ad_config_id. Adconfig ist ein Synonym für AdRule. | Zeichenfolge | N | KEINE | y \| m \| d , ad_config_id | m , ad_config_id |
|          |                                                                                               |                |                |                     |                                                                                    |                                                                         |
|          |                                                                                               |                |                |                     |                                                                                    | Geben Sie für groupBy pünktlich entweder y oder m oder d an |
|          |                                                                                               |                |                |                     |                                                                                    |                                                                         |



## Kopfzeilen {#headers}

| Name | Werttyp | Obligatorisch | Beispielwert | Bedeutung |
|-----------------------|----------------|---------------|-------------------------------------|------------------------------------|
| Accept | Zeichenfolge | Y | text/csv für CSV | Von der API erwartete Antwortart |
|                       |                |               | application/json oder &#39;*/*&quot; für JSON |                                    |
| Autorisierungstoken | Zeichenfolge | Y | xyz | Autorisierungstoken |
| x-api-key | Zeichenfolge | Y | xyz | API-Schlüssel |
| x-gw-ims-org-id | Zeichenfolge | Y | xyz12345 | Kennung der IMS-Organisation Ihres Kontos |

* Sie können das Autorisierungstoken (auch als Zugriffstoken bezeichnet) generieren, indem Sie die auf der Hilfeseite zur JWT-Authentifizierung von Adobe.io beschriebenen Schritte ausführen.
  >>
  [!NOTE]
  >Das Autorisierungstoken hat eine Gültigkeit von 24 Stunden. Wenn Sie also die Berichts-API mit einem wiederkehrenden Skript verwenden, stellen Sie sicher, dass Sie ein Authentifizierungstoken vor dessen Ablauf generieren oder einen OAuth-Fehler bezüglich der ungültigen Token erhalten.

* Um die richtigen Werte im Anfrageheader festzulegen und (mithilfe der JWT-Authentifizierung) Autorisierungstoken zu generieren, müssen Sie die folgenden Konfigurationen für Ihr Konto kennen. Wenden Sie sich an den Primetime-Support, um diese Werte zu erhalten.
Technische Konto-ID

   * Organisations-ID
   * api_key
   * Client_secret

## Ausgabe {#output}

Das Ergebnis der Report API-Abfrage liegt standardmäßig im JSON-Format vor, das Impressionen gegen die verschiedenen Werte der angeforderten Dimensionen (groupby param) angibt. Die Beispielausgabe ist unten aufgeführt:

```JSON
[
    {
        "dates": "07-2020",
        "total_impressions": 213007041
    },
    {
        "dates": "08-2020",
        "total_impressions": 174711626
    },
    {
        "dates": "09-2020",
        "total_impressions": 102863153
    }
]
```

## Fehlercodes und -zeichenfolgen {#error-codes-strings}

### Fehlerreaktionsformat {#error-response-format}

Fehler beim Rendern des Makros &quot;code&quot;: ungültiger Wert für Parameter angegeben `com.atlassian.confluence.ext.code.render.InvalidValueException`

```Shell
{
"error_code": "<ERROR_CODE>",
"message": "<ERROR_MESSAGE>"
}
```

In der folgenden Tabelle sind die Fehler-Codes und -Meldungen aufgeführt, die die Report API zurückgeben kann. Informationen zu Fehlern im Zusammenhang mit der Autorisierungsschicht finden Sie im Abschnitt [Fehlercode-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/landing/troubleshooting.html?lang=en#errors-and-troubleshooting) von Adobe.io.

| Fehler-Code | Fehlermeldung |
|-----------------------|------------------------------------------|
| 4001007 | Benutzerdetails sind ungültig. |
| 4001008 | Alle Zonen sind nicht vom selben Konto. |
| 5001010 | Es ist ein interner Fehler aufgetreten. |
| 4001011 | Daten werden nicht im erforderlichen Format gesendet. |
| 4001012 | Datumsangaben liegen außerhalb des Bereichs. |
| 4001013 | Obligatorischer Parameter fehlt. |
| 4001014 | Die Bereichsliste für das Konto ist leer. |
| 4001015 | Ungültige Filterschlüssel in Anfrage. |
| 4001016 | Ungültige GroupBy -Option in Anfrage. |
| 4001017 | Ungültige ID wird in der Anfrage angegeben |

## Beispielaufrufe und erwartete Ergebnisse {#sample-calls-expected-results}

Im Folgenden finden Sie den Befehl curl , um mithilfe des Zugriffstokens monatliche Impressions-Zählungen zwischen 2020-07-01 und 2021-06-30 zu erhalten:

**Beispiel für einen API-Aufruf**

```shell
curl --location --request GET 'https://dai-sandbox1-primetime.adobe.io/report?startDate=2020-07-01&endDate=2021-06-30&groupBy=m&unpaged=true' \
--header 'x-api-key: <API_KEY>' \
--header 'x-gw-ims-org-id: <ORG_ID>' \
--header 'Authorization: Bearer <ACCESS_TOKEN_STRING>' \
--header 'Accept: application/json'
```

| Beispielaufruf/Anwendungsfall | Erwartetes Ergebnis |
|---|---|
| Bericht mit Start- und Enddatum abrufen - GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2021-01-01 header : Accept = application/json. oder */* | JSON mit den folgenden Parametern mit allen Anzeigen, die zu diesem Konto gehören total_impressions |
| Bericht mit GroupBy abrufen = d \| m \| y GET: [API_ENDPOINT]//report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=d \| m \| y header : Accept = application/json. oder */* | JSON mit den folgenden Parametern mit allen Anzeigen, die zu diesen Kontodaten gehören (TT-MM-JJJJ \| MM-JJJJ \| JJJ-Format) total_impressions |
| Bericht mit GroupBy = ad_config_id-GET abrufen: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=ad_config_id header : Accept = application/json. oder */* | JSON mit den folgenden Parametern mit allen Anzeigen, die zu diesem Konto gehören, ad_config_id total_impressions |
| Bericht mit GroupBy = d \| m \| y und ad_config_id GET abrufen: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=d,ad_config_id header : Accept = application/json. oder */* | JSON mit den folgenden Parametern mit allen Anzeigen, die zu diesem Konto gehören ad_config_id date (mm-dd-yyy \| mm-yyy \| yyy format) total_impressions |
| Bericht mit metaData=true und groupBy=d \| m \| y GET abrufen: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;metaData=true&amp;groupBy=ad_config_id header : Accept = application/json. oder */* | JSON mit den folgenden Parametern mit allen Anzeigen, die zu diesem Konto gehören, ad_config_id name total_impressions |
| Bericht mit groupBy=d \| m \| y und ad_config_id abrufen: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;metaData=true&amp;groupBy=d \| m \| y,ad_config_id header : Accept = application/json. oder */* | JSON mit den folgenden Parametern mit allen Anzeigen, die zu diesem Konto gehören, ad_config_id Name total_impressions date (TT-MM-JJJJ \| MM-JJJJ \| JJJ-Format) |
| Bericht abrufen , um alle Zeilen für einen bestimmten Datumsbereich (mit nicht paged = true) GET zu erhalten: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-31&amp;groupBy=d&amp;unpaged=true | 31 Einträge im zurückgegebenen JSON-Array |
| Bericht mit gültigen Seitenabfrageparametern abrufen GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-31&amp;page=0&amp;size=5&amp;groupBy=d | 5 Einträge im zurückgegebenen Array |
| Abrufen des Berichts mit CSV-Format-GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10 header : Accept = text/csv | CSV-Zeichenfolge wird zurückgegeben, mit der Kopfzeile: total_impressions |
| Abrufen von Berichten mit CSV-Format und groupBy = d \| m \| y GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;groupBy=d\|m\|y header : Accept = text/csv | CSV-Zeichenfolge wird zurückgegeben, mit der Kopfzeile: total_impressions date (TT-MM-JJJJ \| MM-JJJJ \| JJJ-Format) |
| Abrufen von Berichten mit CSV-Format und Metadaten = true -GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;metaData=true header : Accept = text/csv | CSV-Zeichenfolge wird zurückgegeben, mit der Kopfzeile: total_impressions |
| Abrufen von Berichten mit CSV-Format , Metadaten = true und groupBy = d \| m \| y GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;metaData=true&amp;groupBy=d\|m\|y header : Accept = text/csv | CSV-Zeichenfolge wird zurückgegeben, mit der Kopfzeile: total_impressions date (TT-MM-JJJJ \| MM-JJJJ \| JJJ-Format) |


## Report API-Einschränkungsrichtlinie {#report-api-throttling-policy}

* Während eines 5-Sekunden-Fensters sind für jeden Benutzer fünf API-Anfragen zulässig.
* Wenn ein Benutzer diese Grenze überschreitet, wird die Antwort um 5 Sekunden verzögert.
* Wenn ein Benutzer innerhalb von 5 Sekunden mehr als 10 Aufrufe tätigt, wird er mit der Antwort &quot;429 Zu viele Anfragen&quot;abgelehnt.
