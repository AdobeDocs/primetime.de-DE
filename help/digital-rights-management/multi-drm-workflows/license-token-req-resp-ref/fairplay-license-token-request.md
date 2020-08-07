---
description: Die Benutzeroberfläche des FairPlay-Lizenz-Tokens bietet Produktions- und Testdienste.
seo-description: Die Benutzeroberfläche des FairPlay-Lizenz-Tokens bietet Produktions- und Testdienste.
seo-title: FairPlay-LizenzToken-Anforderung/Antwort
title: FairPlay-LizenzToken-Anforderung/Antwort
uuid: 10d4a760-8895-4fb3-8288-1c3a640df587
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 5%

---


# Anforderung und Antwort des FairPlay-Lizenz-Tokens {#fairplay-license-token-request-response}

Die Benutzeroberfläche des FairPlay-Lizenz-Tokens bietet Produktions- und Testdienste. Diese Anforderung gibt ein Token zurück, das für eine FairPlay-Lizenz eingelöst werden kann.

**Methode: GET, POST** (mit einem www-url-kodierten Textkörper, der Parameter für beide Methoden enthält)

**URLs:**

* **Production:** `https://fp-gen.{prod_domain}/hms/fp/token`

* **Test:** `https://fp-gen.test.expressplay.com/hms/fp/token`

* **Sample request:**

```<xref href="https: pr-gen.test.expressplay.com="" hms="" pr="" token?customerAuthenticator="201722,1ad8eed133edf43cbcc185f0236828ae&kid=b366360da82e9c6e0b0984002a362cf2&contentKey=b366360da82e9c6e0b0984002a362cf2&rightsType=BuyToOwn&analogVideoOPL=0&compressedDigitalAudioOPL=0&compressedDigitalVideoOPL=0&uncompressedDigitalAudioOPL=0&uncompressedDigitalVideoOPL=0&quot; format=&quot;html&quot; scope=&quot;external&quot;">
  https://fp-gen.test.expressplay.com/hms/fp/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier> 
   &kid=<CEKSID> 
   &contentKey=<CEK> 
   &rightsType=BuyToOwn 
   &analogVideoOPL=0 
   &compressedDigitalAudioOPL=0 
   &compressedDigitalVideoOPL=0 
   &uncompressedDigitalAudioOPL=0 
   &uncompressedDigitalVideoOPL=0
```

* **Sample Response:**

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

**Request Query Parameters**

**Tabelle 3: Token-Abfragen-Parameter**

| Abfrage-Parameter | Beschreibung | Erforderlich? |
|--- |--- |--- |
| customerAuthenticator-Kundenauthentifizierer als Abfrage-Parameter customerAuthenticator FairPlay | This is your customer API key, one each for your production and test environments. You can find this on the ExpressPlay Admin Dashboard tab. | Yes |
| errorFormat | Either html or json. If html  (the default) an HTML representation of any errors is provided in the entity body of the response. If json is specified, a structured response in JSON format is returned. See [JSON Errors](https://www.expressplay.com/developer/restapi/#json-errors) for details. The mime type of the response is either text/uri-list on success, text/html for HTML error format, or application/json for JSON error format. | No |

**Tabelle 4: Lizenzparameter für Abfragen**

| **Abfrage-Parameter** | **Beschreibung** | **Required?** |
|---|---|---|
| `generalFlags` | A 4 byte hexadecimal string representing the license flags. ‘0000&#39; is the only allowed value. | No |
| `kek` | Key Encryption Key (KEK). Schlüssel werden verschlüsselt mit einem KEK mit einem Schlüsselumbruch-Algorithmus (AES Key Wrap, RFC3394) gespeichert. If `kek` is supplied, either one of the `kid` or the `ek` parameters needs to be supplied, *but not both*. | No |
| `kid` | A 16 byte hexadecimal string representation of the content encryption key or a string `'^somestring'`. Die Länge der Zeichenfolge gefolgt vom Zeichen `'^'` darf 64 Zeichen nicht überschreiten. | No |
| `ek` | A hex string representation of the encrypted content key. | Nein |
| `contentKey` | A 16 byte hexadecimal string representation of the content encryption key | Yes, unless the `kek` and `ek` or `kid` are provided. |
| `iv` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung der Inhaltsverschlüsselung IV | Ja |
| `rentalDuration` | Duration of the rental in seconds (default - 0) | No |
| `fpExtension` | A short form wrapping `extensionType` and `extensionPayload`, as a comma separated string. Beispiel: […] `&fpExtension=wudo,AAAAAA==&`[…] | Nein, eine beliebige Zahl kann verwendet werden |

**Table 5: Token Restriction Query Parameters**

<table id="table_ar3_lsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Query Parameter</b> </th> 
   <th class="entry"> <b>Description</b> </th> 
   <th class="entry"> <b>Required?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> expirationTime </span> </td> 
   <td> Ablaufzeit dieses Tokens. Dieser Wert MUSS eine Zeichenfolge im <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> Datums-/Uhrzeitformat im Z-Zonenbezeichner ("Zulu-Zeit") oder eine Ganzzahl mit vorangestelltem "+"-Zeichen sein. Ein Beispiel für einen RFC 3339 Datum/Uhrzeit ist <span class="codeph"> 2006-04-14T12:01:10Z </span>. <p>If the value is a string in <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> date/time format, then it represents an absolute expiration date/time for the token. If the value is an integer preceded by a '+' sign, then it is interpreted as a relative number of seconds, from issuance, that the token is valid. </p> For example, <span class="codeph"> +60 </span> specifies one minute. The maximum and default (if not specified) token lifetime is 30 days. </td> 
   <td> No </td> 
  </tr> 
 </tbody> 
</table>

**Table 6: Correlation Query Parameters**

| **Query Parameter** | **Description** | **Required?** |
|---|---|---|
| `cookie` | Eine beliebige Zeichenfolge mit einer Länge von bis zu 32 Zeichen, die im Token gespeichert und vom Token-Einlösungsserver protokolliert wird. Auf diese Weise können Protokolleinträge auf dem Einlöseserver und auf den Servern des Dienstleisters korreliert werden. | Nein |

**Reaktion**

**Tabelle 7: HTTP-Antworten**

| **HTTP-Statuscode** | **Description** | **Content-Type** | **Entitätstext enthält** |
|---|---|---|---|
| `200 OK` | Kein Fehler. | `text/uri-list` | License acquisition URL + token |
| `400 Bad Request` | Ungültige Artikel | `text/html` oder `application/json` | Error description |
| `401 Unauthorized` | Auth failed | `text/html` or `application/json` | Error description |
| `404 Not found` | Bad URL | `text/html` or `application/json` | Error description |
| `50x Server Error` | Serverfehler | `text/html` or `application/json` | Error description |

**Table 8: Event Error Codes**

<table id="table_i2c_zsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Code</b> </th> 
   <th class="entry"> <b>Description</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> -2002 </td> 
   <td> Invalid token expiration time: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2003 </td> 
   <td> Invalid IP address </td> 
  </tr> 
  <tr> 
   <td> -2005 </td> 
   <td> Invalid content encryption key: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2008 </td> 
   <td> Invalid output control flags specified: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> Authentication token must be supplied </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td> Authentication token invalid: &lt;details&gt; <p>Note:  This can happen if the authenticator is wrong or when accessing the test API at <span class="filepath"> *.test.expressplay.com </span> using the production authenticator and vice versa. </p> <p importance="high">Note:  The Test SDK and Advanced Test Tool (ATT) only work with <span class="filepath"> *.test.expressplay.com </span>, whereas production devices must use <span class="filepath"> *.service.expressplay.com </span>. </p> </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> Insufficient tokens available </td> 
  </tr> 
  <tr> 
   <td> -2020 </td> 
   <td> Missing rights type </td> 
  </tr> 
  <tr> 
   <td> -2021 </td> 
   <td> Invalid rights type </td> 
  </tr> 
  <tr> 
   <td> -2022 </td> 
   <td> Missing rental period end time </td> 
  </tr> 
  <tr> 
   <td> -2023 </td> 
   <td> Missing rental play duration </td> 
  </tr> 
  <tr> 
   <td> -2025 </td> 
   <td> Invalid rental play duration </td> 
  </tr> 
  <tr> 
   <td> -2027 </td> 
   <td> Content encryption key must be 32-hexadecimal digits long </td> 
  </tr> 
  <tr> 
   <td> -2030 </td> 
   <td> ExpressPlay Admin error: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td> Service Account Disabled </td> 
  </tr> 
  <tr> 
   <td> -2033 </td> 
   <td> Invalid cookie </td> 
  </tr> 
  <tr> 
   <td> -2034 </td> 
   <td> Invalid Output Control, values out of specified range </td> 
  </tr> 
  <tr> 
   <td> -2035 </td> 
   <td> No corresponding value specified </td> 
  </tr> 
  <tr> 
   <td> -2036 </td> 
   <td> Extension type should be 4 characters </td> 
  </tr> 
  <tr> 
   <td> -2037 </td> 
   <td> Die Nutzlast der Erweiterung sollte Base64-kodiert sein </td> 
  </tr> 
  <tr> 
   <td> -2040 </td> 
   <td> <span class="codeph"> OutputControlFlag </span> muss 4 Byte kodieren </td> 
  </tr> 
  <tr> 
   <td> -3004 </td> 
   <td> Ungültiges Fehlerformat angegeben: &lt;format&gt; </td> 
  </tr> 
  <tr> 
   <td> -4001 </td> 
   <td> Gerät konnte nicht authentifiziert werden </td> 
  </tr> 
  <tr> 
   <td> -4010 </td> 
   <td> Ungültiges Token </td> 
  </tr> 
  <tr> 
   <td> -4018 </td> 
   <td> Fehlende ID </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Inhaltsschlüssel konnte nicht vom wichtigen Datenspeicherung-Dienst abgerufen werden </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> Kind </span> muss 32 Hexadezimalzeichen lang sein </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> kid </span> must be 64 characters long after the ^ </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> Ungültiges <span class="codeph"> Kind </span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td> Invalid encrypted key or <span class="codeph"> kek </span> </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Invalid general flags </td> 
  </tr> 
  <tr> 
   <td> -6001 </td> 
   <td> Invalid <span class="codeph"> FPExtension </span> parameters specified </td> 
  </tr> 
  <tr> 
   <td> -6002 </td> 
   <td> Ungültiger FP-Token-Typ </td> 
  </tr> 
  <tr> 
   <td> -6003 </td> 
   <td> Ungültiger <span class="codeph"> iv- </span> Parameter angegeben </td> 
  </tr> 
  <tr> 
   <td> -6004 </td> 
   <td> Failed to generate CKC for FP </td> 
  </tr> 
  <tr> 
   <td> -6005 </td> 
   <td> Invalid key data specified </td> 
  </tr> 
  <tr> 
   <td> -6006 </td> 
   <td> Service not authorized for FairPlay support </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> Ungültige Mietdauer angegeben </td> 
  </tr> 
  <tr> 
   <td> -6008 </td> 
   <td> Die Bindung der Geräte-ID wird für FairPlay nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td> -6009 </td> 
   <td> FairPlay option disabled </td> 
  </tr> 
 </tbody> 
</table>