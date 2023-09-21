---
description: Die Oberfläche des PlayReady-Lizenz-Tokens bietet Produktions- und Testdienste.
title: Anfrage/Antwort für PlayReady-Lizenz-Token
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 4%

---

# Anfrage/Antwort für PlayReady-Lizenz-Token {#playready-license-token-request-response}

Die Oberfläche des PlayReady-Lizenz-Tokens bietet Produktions- und Testdienste.

Diese HTTP-Anfrage gibt ein Token zurück, das für eine PlayReady-Lizenz eingelöst werden kann.

**Methode: GET, POST** (mit einem www-url-kodierten Textkörper, der Parameter für beide Methoden enthält)

**URLs:**

* **Produktion:** `https://pr-gen.{prod_domain}/hms/pr/token`

* **Test:** ` [https://pr-gen.test.expressplay.com/hms/pr/token](https://pr-gen.test.expressplay.com/hms/pr/token)`

* **Beispielanfrage:**

  ```
  <xref href="https: pr-gen.test.expressplay.com="" hms="" pr="" token?customerAuthenticator="201722,1ad8eed133edf43cbcc185f0236828ae&kid=b366360da82e9c6e0b0984002a362cf2&contentKey=b366360da82e9c6e0b0984002a362cf2&rightsType=BuyToOwn&analogVideoOPL=0&compressedDigitalAudioOPL=0&compressedDigitalVideoOPL=0&uncompressedDigitalAudioOPL=0&uncompressedDigitalVideoOPL=0&quot; format=&quot;html&quot; scope=&quot;external&quot;">
  https://pr-gen.test.expressplay.com/hms/pr/token?customerAuthenticator=
   <ExpressPlay customer authenticator identifier>
   &kid=<CEKSID>
   &contentKey=<CEK>
   &rightsType=BuyToOwn
   &analogVideoOPL=0
   &compressedDigitalAudioOPL=0
   &compressedDigitalVideoOPL=0
   &uncompressedDigitalAudioOPL=0
   &uncompressedDigitalVideoOPL=0
  </xref href="https:>
  ```

* **Beispielantwort:**

  ```
  {"licenseAcquisitionUrl":"https://expressplay-licensing.axprod.net/LicensingService.ashx",
              "token":"<base64-encoded ExpressPlay token>"}
  ```

## Abfrageparameter anfordern {#section_26F8856641A64A46A3290DBE61ACFAD2}

**Tabelle 9: Token-Abfrageparameter**

<table id="table_zxg_dyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Abfrageparameter</b> </th> 
   <th class="entry"><b>Beschreibung</b> </th> 
   <th class="entry"><b>Erforderlich?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> customerAuthenticator</span> </td> 
   <td> <p>Dies ist Ihr Customer-API-Schlüssel, jeweils einer für Ihre Produktions- und Testumgebungen. Sie finden dies auf der Registerkarte Admin Dashboard von ExpressPlay . </p> </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> errorFormat</span> </td> 
   <td>Entweder <span class="codeph"> html</span> oder <span class="codeph"> json</span>. Wenn <span class="codeph"> html</span> (Standard) Eine HTML-Darstellung aller Fehler wird im Entitätstext der Antwort bereitgestellt. <p>Wenn <span class="codeph"> json</span> angegeben ist, wird eine strukturierte Antwort im JSON-Format zurückgegeben. Siehe <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON-Fehler</a> für Details. </p> <p>Der MIME-Typ der Antwort lautet entweder <span class="codeph"> text/uri-list</span> zum Erfolg, <span class="codeph"> text/html</span> für das HTML-Fehlerformat oder <span class="codeph"> application/json</span> für das JSON-Fehlerformat. </p> </td> 
   <td> Nein </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 10: Lizenzabfrageparameter**

<table id="table_f1l_fyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Abfrageparameter</b> </th> 
   <th class="entry"><b>Beschreibung</b> </th> 
   <th class="entry"><b>Erforderlich?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> generalFlags</span> </td> 
   <td>Ein 4-Byte-Hexadezimalstring, der die Lizenzflags darstellt. Für eine beständige Lizenz muss sie auf "0000001"gesetzt werden. <p>Hinweis: Mietlizenzen (<span class="codeph"> rightsType=Rental</span>) MUSS persistent sein. </p> </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kek</span> </td> 
   <td> Schlüssel-Verschlüsselungsschlüssel (KEK). Schlüssel werden mit einem KEK mithilfe eines Schlüsselumbruchalgorithmus (AES Key Wrap, RFC3394) verschlüsselt gespeichert. </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> Kind</span> </td> 
   <td>Eine 16-Byte-Hexadezimal-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels oder eines Strings <span class="codeph"> ^somestring'</span>. Die Länge des Strings gefolgt von '^' darf nicht größer als 64 Zeichen sein. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> ek</span> </td> 
   <td> Eine Hex-String-Darstellung des verschlüsselten Inhaltsschlüssels. </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> contentKey</span> </td> 
   <td> Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels </td> 
   <td>Ja, außer <span class="codeph"> kek</span> und <span class="codeph"> ek</span> oder <span class="codeph"> Kind</span> bereitgestellt werden </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rightsType</span> </td> 
   <td>Gibt die Art der Rechte an. Muss <span class="codeph"> BuyToOwn</span> oder <span class="codeph"> Miete</span>. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rent.periodEndTime</span> </td> 
   <td>Mietenddatum. Dieser Wert MUSS im Format "RFC 3339" _ Datum/Uhrzeit im Format "Z"Zone-Bezeichner ("Zulu-Zeit") oder einer Ganzzahl mit vorangestelltem "+"-Zeichen liegen. <p>Wenn der Wert eine <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339</a> Datums-/Uhrzeitformat und stellt dann ein absolutes Ablaufdatum/eine absolute Ablaufzeit für die Lizenz dar. Ein Beispiel für eine RFC 3339-Datums-/Uhrzeitangabe ist 2006-04-14T12:01:10Z. </p> <p> Wenn es sich bei dem Wert um eine Ganzzahl handelt, der ein "+"-Zeichen vorangestellt ist, wird diese als relative Anzahl von Sekunden ab der Ausgabe des Tokens verwendet. Der Inhalt kann nach dieser Zeit nicht mehr wiedergegeben werden. Nur gültig, wenn <span class="codeph"> rightsType</span> is <span class="codeph"> Miete</span>. </p> </td> 
   <td>Ja, wann <span class="codeph"> rightsType</span> is <span class="codeph"> Miete</span>. </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rent.playDuration</span> </td> 
   <td>Zeit (in Sekunden), die nach dem Start der Wiedergabe des Inhalts wiedergegeben werden kann. Nur gültig, wenn <span class="codeph"> rightsType</span> ist mietpflichtig. </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> analogVideoOPL</span> </td> 
   <td> Ganzzahlwert zur Angabe des Ausgangsschutzniveaus für analoge Videos. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressionDigitalAudioOPL</span> </td> 
   <td> Ganzzahlwert zur Angabe des Output Protection Level für komprimiertes digitales Audio. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressionDigitalVideoOPL</span> </td> 
   <td> Ganzzahlwert zur Angabe des Ausgabeschutzniveaus für komprimiertes digitales Video. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressionDigitalAudioOPL</span> </td> 
   <td> Ganzzahlwert zur Angabe des Output Protection Level für unkomprimiertes digitales Audio. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressionDigitalVideoOPL</span> </td> 
   <td> Ganzzahlwert zur Angabe des Ausgabeschutzniveaus für unkomprimiertes digitales Video. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> unknownOutputBehavior</span> </td> 
   <td>Erforderliches Verhalten bei unbekannter Ausgabe. Zulässige Werte: <span class="codeph"> Zulassen</span>, <span class="codeph"> Disallow</span> oder <span class="codeph"> SDOnly</span> </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> outputControlFlags</span> </td> 
   <td> Ein 4-Byte-Hex-Wert, der die Flags für andere Ausgabeoptionen angibt </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionType</span> </td> 
   <td>Ein beliebiges 4-Buchstaben-Wort, das eine 32-Bit-Kennung für eine Erweiterung darstellt. Der 8-Bit-ASCII-Code jedes Briefs ist der entsprechende 8-Bit-Byte-Teil der Kennung. Der Kennungswert 0x61626364 (hexadezimal) würde beispielsweise folgendermaßen geschrieben:<span class="codeph"> abcd</span>', da der ASCII-Code für "a"0x61 usw. ist. </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionPayload</span> </td> 
   <td> Eine base64-kodierte Zeichenfolge der Erweiterung. </td> 
   <td>Ja, wann <span class="codeph"> extensionType</span> festgelegt ist. </td> 
  </tr> 
 </tbody> 
</table>

## Antworten {#section_0079C31B4AF14DBBB6277CF251FB90E3}

**Tabelle 11: HTTP-Antworten**

| **HTTP-Statuscode** | **Beschreibung** | **Content-Type** | **Entitätstext enthält** |
|---|---|---|---|
| `200 OK` | Kein Fehler. | `text/uri-list` | Lizenzakquise-URL und -Token |
| `400 Bad Request` | Ungültige Protokolle | `text/html` oder `application/json` | Fehlerbeschreibung |
| `401 Unauthorized` | Autor fehlgeschlagen | `text/html` oder `application/json` | Fehlerbeschreibung |
| `404 Not found` | Ungültige URL | `text/html` oder `application/json` | Fehlerbeschreibung |
| `50x Server Error` | Server-Fehler | `text/html` oder `application/json` | Fehlerbeschreibung |

**Tabelle 12: Fehlercodes für Ereignisse**

<table id="table_lqb_ycs_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Code</b> </th> 
   <th class="entry"><b>Beschreibung</b> </th> 
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
   <td> Ungültige Flags der Ausgabesteuerung angegeben: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> Authentifizierungstoken muss angegeben werden </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td>Authentifizierungstoken ungültig: &lt;details&gt; <p>Hinweis: Dies kann vorkommen, wenn der Authentifizierer falsch ist oder wenn er mithilfe des Produktionsauthentifikators unter *.test.expressplay.com auf die Test-API zugreift und umgekehrt. </p> <p importance="high">Hinweis: Das Test-SDK und das Advanced Test Tool (ATT) funktionieren nur mit <span class="filepath"> *.test.expressplay.com</span>, während Produktionsgeräte <span class="filepath"> *.service.expressplay.com</span>. </p> </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> Nicht genügend Token verfügbar </td> 
  </tr> 
  <tr> 
   <td> -2020 </td> 
   <td> Fehlende Rechte </td> 
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
   <td> Der Schlüssel zur Inhaltsverschlüsselung muss 32-Hexadezimalziffern lang sein. </td> 
  </tr> 
  <tr> 
   <td> -2030 </td> 
   <td> ExpressPlay Admin-Fehler: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td> Dienstkonto deaktiviert </td> 
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
   <td> Der Erweiterungstyp sollte 4 Zeichen enthalten </td> 
  </tr> 
  <tr> 
   <td> -2037 </td> 
   <td> Die Nutzlast der Erweiterung sollte Base64-kodiert sein </td> 
  </tr> 
  <tr> 
   <td> -2040 </td> 
   <td><span class="codeph"> OutputControlFlag</span> muss 4 Byte kodieren </td> 
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
   <td> -4018 </td> 
   <td>Fehlt <span class="codeph"> Kind</span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Inhaltsschlüssel konnte nicht vom Schlüsselspeicherdienst abgerufen werden </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td><span class="codeph"> Kind</span> muss 32 hexadezimale Zeichen lang sein </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td><span class="codeph"> Kind</span> muss 64 Zeichen lang nach dem ^ sein. </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td>Ungültig <span class="codeph"> Kind</span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td>Ungültige verschlüsselt <span class="codeph"> key</span> oder kek </td> 
  </tr> 
  <tr> 
   <td> -5001 </td> 
   <td> Ungültiger unbekannter Ausgabetyp-Fehler </td> 
  </tr> 
  <tr> 
   <td> -5002 </td> 
   <td> Die Option PlayReady ist für diesen Dienst deaktiviert. </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Ungültige allgemeine Flags </td> 
  </tr> 
  <tr> 
   <td> -5004 </td> 
   <td> Die Geräte-ID muss 32 hexadezimale Zeichen lang sein. </td> 
  </tr> 
  <tr> 
   <td> -5005 </td> 
   <td> Ungültige Geräte-ID </td> 
  </tr> 
  <tr> 
   <td> -5006 </td> 
   <td> Fehlender OPL-Wert </td> 
  </tr> 
  <tr> 
   <td> -5007 </td> 
   <td>Nur einer von <span class="codeph"> kek</span> oder <span class="codeph"> contentKey</span> kann angegeben werden </td> 
  </tr> 
 </tbody> 
</table>
