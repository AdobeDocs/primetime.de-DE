---
description: Die Benutzeroberfläche des FairPlay-Lizenz-Tokens bietet Produktions- und Testdienste.
title: FairPlay-LizenzToken-Anforderung/Antwort
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 5%

---


# FairPlay-Lizenztoken-Anforderung und -Antwort {#fairplay-license-token-request-response}

Die Benutzeroberfläche des FairPlay-Lizenz-Tokens bietet Produktions- und Testdienste. Diese Anforderung gibt ein Token zurück, das für eine FairPlay-Lizenz eingelöst werden kann.

**Methode: GET, POST**  (mit einem www-url-kodierten Textkörper, der Parameter für beide Methoden enthält)

**URLs:**

* **Produktion:** `https://fp-gen.{prod_domain}/hms/fp/token`

* **Test:** `https://fp-gen.test.expressplay.com/hms/fp/token`

* **Beispielanforderung:**

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

* **Beispielantwort:**

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

**Anforderungsparameter für Abfragen**

**Tabelle 3: Token-Abfragen-Parameter**

| Abfrage-Parameter | Beschreibung | Erforderlich? |
|--- |--- |--- |
| customerAuthenticator-Kundenauthentifizierer als Abfrage-Parameter customerAuthenticator FairPlay | Dies ist Ihr Kunde-API-Schlüssel, einer für Ihre Produktions- und Testing-Umgebung. Sie finden dies auf der Registerkarte &quot;ExpressPlay Admin-Dashboard&quot;. | Ja |
| errorFormat | Entweder HTML oder JSON. Wenn html (Standard), wird eine HTML-Darstellung aller Fehler im Entitätstext der Antwort bereitgestellt. Wenn json angegeben ist, wird eine strukturierte Antwort im JSON-Format zurückgegeben. Weitere Informationen finden Sie unter [JSON-Fehler](https://www.expressplay.com/developer/restapi/#json-errors). Der Mime-Typ der Antwort ist entweder text/uri-Liste bei Erfolg, text/html bei HTML-Fehlerformat oder application/json bei JSON-Fehlerformat. | Nein |

**Tabelle 4: Lizenzparameter für Abfragen**

| **Abfrage-Parameter** | **Beschreibung** | **Erforderlich?** |
|---|---|---|
| `generalFlags` | Eine Hexadezimalzeichenfolge mit 4 Byte, die die Lizenzflags darstellt. &quot;0000&quot;ist der einzige zulässige Wert. | Nein |
| `kek` | Schlüssel-Verschlüsselungsschlüssel (KEK). Schlüssel werden verschlüsselt mit einem KEK mit einem Schlüsselumbruch-Algorithmus (AES Key Wrap, RFC3394) gespeichert. Wenn `kek` angegeben wird, muss entweder einer der Parameter `kid` oder `ek` angegeben werden, *jedoch nicht beide.* | Nein |
| `kid` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels oder eine Zeichenfolge `'^somestring'`. Die Länge der Zeichenfolge gefolgt von `'^'` darf 64 Zeichen nicht überschreiten. | Nein |
| `ek` | Eine Hex-String-Darstellung des verschlüsselten Inhaltsschlüssels. | Nein |
| `contentKey` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels | Ja, es sei denn, die Variablen `kek` und `ek` oder `kid` werden bereitgestellt. |
| `iv` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung der Inhaltsverschlüsselung IV | Ja |
| `rentalDuration` | Mietdauer in Sekunden (Standard - 0) | Nein |
| `fpExtension` | Ein kurzer Formularumbruch `extensionType` und `extensionPayload` als kommagetrennte Zeichenfolge. Beispiel: […] `&fpExtension=wudo,AAAAAA==&`[…] | Nein, eine beliebige Zahl kann verwendet werden |

**Tabelle 5: Token-Zugriffsparameter für Abfragen**

<table id="table_ar3_lsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Abfrage-Parameter</b> </th> 
   <th class="entry"> <b>Beschreibung</b> </th> 
   <th class="entry"> <b>Erforderlich?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> expirationTime  </span> </td> 
   <td> Ablaufzeit dieses Tokens. Dieser Wert MUSS eine Zeichenfolge im Format <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> Datum-/Uhrzeitformat im Z-Zonenbezeichner ("Zulu-Zeit") oder eine Ganzzahl mit vorangestelltem "+"-Zeichen sein. Ein Beispiel für eine RFC 3339-Datum/Uhrzeit ist <span class="codeph"> 2006-04-14T12:01:10Z </span>. <p>Wenn der Wert eine Zeichenfolge im Format <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> ist, stellt er ein absolutes Ablaufdatum/eine absolute Ablaufzeit für das Token dar. Wenn der Wert eine Ganzzahl ist, der ein "+"-Zeichen vorangestellt ist, wird als relative Anzahl von Sekunden ab Ausgabe interpretiert, dass das Token gültig ist. </p> Beispiel: <span class="codeph"> +60 </span> gibt eine Minute an. Die Gültigkeitsdauer des Tokens beträgt maximal 30 Tage (sofern nicht angegeben). </td> 
   <td> Nein </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 6: Korrelationsparameter für Abfragen**

| **Abfrage-Parameter** | **Beschreibung** | **Erforderlich?** |
|---|---|---|
| `cookie` | Eine beliebige Zeichenfolge mit einer Länge von bis zu 32 Zeichen, die im Token gespeichert und vom Token-Einlösungsserver protokolliert wird. Auf diese Weise können Protokolleinträge auf dem Einlöseserver und auf den Servern des Dienstleisters korreliert werden. | Nein |

**Reaktion**

**Tabelle 7: HTTP-Antworten**

| **HTTP-Statuscode** | **Beschreibung** | **Content-Type** | **Entitätstext enthält** |
|---|---|---|---|
| `200 OK` | Kein Fehler. | `text/uri-list` | Lizenzakquise-URL + Token |
| `400 Bad Request` | Ungültige Artikel | `text/html` oder  `application/json` | Fehlerbeschreibung |
| `401 Unauthorized` | Autom fehlgeschlagen | `text/html` oder  `application/json` | Fehlerbeschreibung |
| `404 Not found` | Ungültige URL | `text/html` oder  `application/json` | Fehlerbeschreibung |
| `50x Server Error` | Serverfehler | `text/html` oder  `application/json` | Fehlerbeschreibung |

**Tabelle 8: Ereignis-Fehlercodes**

<table id="table_i2c_zsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Code</b> </th> 
   <th class="entry"> <b>Beschreibung</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> -2002 </td> 
   <td> Ungültige Token-Ablaufzeit: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2003 </td> 
   <td> Ungültige IP-Adresse </td> 
  </tr> 
  <tr> 
   <td> -2005 </td> 
   <td> Ungültiger Schlüssel zur Inhaltsverschlüsselung: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2008 </td> 
   <td> Ungültige Ausgabesteuerungs-Flags angegeben: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> Authentifizierungstoken muss angegeben werden </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td> Authentifizierungstoken ungültig: &lt;details&gt; <p>Hinweis:  Dies kann vorkommen, wenn der Authentifizierer falsch ist oder wenn der Zugriff auf die Test-API unter <span class="filepath"> *.test.expressplay.com </span> mit dem Produktionsauthentifizierer erfolgt und umgekehrt. </p> <p importance="high">Hinweis:  Das Test SDK und das Advanced Test Tool (ATT) funktionieren nur mit <span class="filepath"> *.test.expressplay.com </span>, während Produktionsgeräte <span class="filepath"> *.service.expressplay.com </span> verwenden müssen. </p> </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> Nicht genügend Token verfügbar </td> 
  </tr> 
  <tr> 
   <td> -2020 </td> 
   <td> Typ der fehlenden Rechte </td> 
  </tr> 
  <tr> 
   <td> -2021 </td> 
   <td> Ungültiger Berechtigungstyp </td> 
  </tr> 
  <tr> 
   <td> -2022 </td> 
   <td> Fehlende Endzeit des Mietzeitraums </td> 
  </tr> 
  <tr> 
   <td> -2023 </td> 
   <td> Fehlende Wiedergabedauer </td> 
  </tr> 
  <tr> 
   <td> -2025 </td> 
   <td> Ungültige Wiedergabedauer </td> 
  </tr> 
  <tr> 
   <td> -2027 </td> 
   <td> Der Schlüssel für die Inhaltsverschlüsselung muss 32-Hexadezimalziffern lang sein. </td> 
  </tr> 
  <tr> 
   <td> -2030 </td> 
   <td> ExpressPlay Admin-Fehler: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td> Dienst Account deaktiviert </td> 
  </tr> 
  <tr> 
   <td> -2033 </td> 
   <td> Ungültiges Cookie </td> 
  </tr> 
  <tr> 
   <td> -2034 </td> 
   <td> Ungültige Ausgabesteuerung, Werte außerhalb des angegebenen Bereichs </td> 
  </tr> 
  <tr> 
   <td> -2035 </td> 
   <td> Kein entsprechender Wert angegeben </td> 
  </tr> 
  <tr> 
   <td> -2036 </td> 
   <td> Erweiterungstyp sollte 4 Zeichen umfassen </td> 
  </tr> 
  <tr> 
   <td> -2037 </td> 
   <td> Die Nutzlast der Erweiterung sollte Base64-kodiert sein </td> 
  </tr> 
  <tr> 
   <td> -2040 </td> 
   <td> <span class="codeph"> OutputControlFlag  </span> muss 4 Byte kodieren </td> 
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
   <td> <span class="codeph"> Kind  </span> muss 32 Hexadezimalzeichen lang sein </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> Kind  </span> muss 64 Zeichen lang nach ^ sein </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> Ungültige <span class="codeph"> Kind </span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td> Ungültiger verschlüsselter Schlüssel oder <span class="codeph"> kek </span> </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Ungültige allgemeine Flags </td> 
  </tr> 
  <tr> 
   <td> -6001 </td> 
   <td> Ungültige Parameter für <span class="codeph"> FPExtension </span> angegeben </td> 
  </tr> 
  <tr> 
   <td> -6002 </td> 
   <td> Ungültiger FP-Token-Typ </td> 
  </tr> 
  <tr> 
   <td> -6003 </td> 
   <td> Ungültiger Parameter <span class="codeph"> iv </span> angegeben </td> 
  </tr> 
  <tr> 
   <td> -6002 </td> 
   <td> Fehler beim Generieren von CKC für FP </td> 
  </tr> 
  <tr> 
   <td> -6005 </td> 
   <td> Ungültige Schlüsseldaten angegeben </td> 
  </tr> 
  <tr> 
   <td> -6006 </td> 
   <td> Dienst nicht für FairPlay-Unterstützung autorisiert </td> 
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
   <td> FairPlay-Option deaktiviert </td> 
  </tr> 
 </tbody> 
</table>