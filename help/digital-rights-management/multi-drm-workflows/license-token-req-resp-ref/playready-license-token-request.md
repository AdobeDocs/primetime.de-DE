---
description: Die Oberfläche des PlayReady-LizenzTokens bietet Produktions- und Testdienste.
seo-description: Die Oberfläche des PlayReady-LizenzTokens bietet Produktions- und Testdienste.
seo-title: PlayReady-Lizenz-Token-Anforderung/Antwort
title: PlayReady-Lizenz-Token-Anforderung/Antwort
uuid: 20ebd582-ebb9-4716-8c1e-df3e58d6ec14
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# PlayReady-Lizenz-Token-Anforderung/Antwort {#playready-license-token-request-response}

Die Oberfläche des PlayReady-LizenzTokens bietet Produktions- und Testdienste.

Diese HTTP-Anforderung gibt ein Token zurück, das für eine PlayReady-Lizenz eingelöst werden kann.

**Methode: GET, POST** (mit einem www-url-kodierten Textkörper, der Parameter für beide Methoden enthält)

**URLs:**

* **Produktion:** `https://pr-gen.{prod_domain}/hms/pr/token`

* **Test:** ` [https://pr-gen.test.expressplay.com/hms/pr/token](https://pr-gen.test.expressplay.com/hms/pr/token)`

* **Beispielanforderung:**

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

## Anforderungsparameter für Abfragen {#section_26F8856641A64A46A3290DBE61ACFAD2}

**Tabelle 9: Token-Abfragen-Parameter**

<table id="table_zxg_dyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Abfrage-Parameter</b> </th> 
   <th class="entry"><b>Beschreibung</b> </th> 
   <th class="entry"><b>Erforderlich?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> customerAuthenticator</span> </td> 
   <td> <p>Dies ist Ihr Kunde-API-Schlüssel, einer für Ihre Produktions- und Testing-Umgebung. Sie finden dies auf der Registerkarte "ExpressPlay Admin-Dashboard". </p> </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> errorFormat</span> </td> 
   <td>Entweder <span class="codeph"> html</span> oder <span class="codeph"> json</span>. Wenn <span class="codeph"> HTML</span> (Standard), wird eine HTML-Darstellung aller Fehler im Entitätstext der Antwort bereitgestellt. <p>Wenn <span class="codeph"> json</span> angegeben ist, wird eine strukturierte Antwort im JSON-Format zurückgegeben. Weitere Informationen finden Sie unter <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON-Fehler</a> . </p> <p>Der Mime-Typ der Antwort lautet entweder <span class="codeph"> text/uri-Liste</span> bei Erfolg, <span class="codeph"> text/html</span> bei HTML-Fehlerformat oder <span class="codeph"> application/json</span> bei JSON-Fehlerformat. </p> </td> 
   <td> Nein </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 10: Lizenzparameter für Abfragen**

<table id="table_f1l_fyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Abfrage-Parameter</b> </th> 
   <th class="entry"><b>Beschreibung</b> </th> 
   <th class="entry"><b>Erforderlich?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> generalFlags</span> </td> 
   <td>Eine Hexadezimalzeichenfolge mit 4 Byte, die die Lizenzflags darstellt. Für eine beständige Lizenz muss sie auf "00000001"gesetzt werden. <p>Hinweis: Mietlizenzen (<span class="codeph"> rightsType=Rental</span>) MÜSSEN dauerhaft sein. </p> </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kek</span> </td> 
   <td> Schlüssel-Verschlüsselungsschlüssel (KEK). Schlüssel werden verschlüsselt mit einem KEK mit einem Schlüsselumbruch-Algorithmus (AES Key Wrap, RFC3394) gespeichert. </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> Kind</span> </td> 
   <td>Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels oder eine Zeichenfolge <span class="codeph"> ^somestring'</span>. Die Länge der Zeichenfolge gefolgt von '^' darf 64 Zeichen nicht überschreiten. </td> 
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
   <td>Ja, es sei denn, <span class="codeph"> Kek</span> und <span class="codeph"> ek</span> oder <span class="codeph"> Kind</span> sind angegeben </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rightsType</span> </td> 
   <td>Gibt die Art der Rechte an. Muss <span class="codeph"> BuyToOwn</span> oder <span class="codeph"> Miete</span>sein. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> miet.periodEndTime</span> </td> 
   <td>Mietende. Dieser Wert MUSS im Format "RFC 3339" _ Datum/Uhrzeit im Format "Z"-Zone-Bezeichner ("Zulu-Zeit") oder eine Ganzzahl mit vorangestelltem "+"-Zeichen sein. <p>Wenn der Wert ein <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339</a> Datums-/Uhrzeitformat ist, stellt er ein absolutes Ablaufdatum/eine absolute Ablaufzeit für die Lizenz dar. Ein Beispiel für ein RFC 3339 Datum/Uhrzeit ist 2006-04-14T12:01:10Z. </p> <p> Wenn der Wert eine Ganzzahl ist, der das Pluszeichen "+"vorangestellt ist, wird er als relative Anzahl von Sekunden ab dem Zeitpunkt der Ausgabe des Tokens verwendet. Der Inhalt kann nach dieser Zeit nicht mehr wiedergegeben werden. Nur gültig, wenn <span class="codeph"> Berechtigungstyp</span> <span class="codeph"> Miete</span>ist. </p> </td> 
   <td>Ja, wenn <span class="codeph"> der</span> Berechtigungstyp <span class="codeph"> Miete</span>ist. </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rent.playDuration</span> </td> 
   <td>Zeit (in Sekunden), die die Wiedergabe des Inhalts nach dem Start der Wiedergabe ermöglicht. Nur gültig, wenn <span class="codeph"> Berechtigungstyp</span> mieten ist. </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> analogVideoOPL</span> </td> 
   <td> Integer-Wert, um den Output Protection Level für analoge Videos anzugeben. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressionDigitalAudioOPL</span> </td> 
   <td> Integer-Wert, um die Ausgabeschutzstufe für komprimierte digitale Audiodaten anzugeben. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressionDigitalVideoOPL</span> </td> 
   <td> Integer-Wert, um den Output Protection Level für komprimiertes digitales Video anzugeben. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressionDigitalAudioOPL</span> </td> 
   <td> Integer-Wert, um die Ausgabeschutzstufe für unkomprimierte digitale Audiodaten anzugeben. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressionDigitalVideoOPL</span> </td> 
   <td> Integer-Wert, um den Output Protection Level für unkomprimiertes digitales Video anzugeben. Gültiger Bereich 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> unknownOutputBehavior</span> </td> 
   <td>Erforderliches Verhalten, wenn die Ausgabe unbekannt ist. Zulässige Werte: <span class="codeph"> Nur</span>zulassen, <span class="codeph"> Nicht zulassen</span> oder <span class="codeph"> SDOnly</span> </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> outputControlFlags</span> </td> 
   <td> Ein 4-Byte-Hex-Wert, der die Flags für andere Ausgabesteuerungsoptionen angibt </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionType</span> </td> 
   <td>Ein beliebiges 4-Buchstaben-Wort, das einen 32-Bit-Bezeichner für eine Erweiterung darstellt. Der 8-Bit-ASCII-Code jedes Briefs ist der entsprechende 8-Bit-Byte-Teil des Identifikators. Der Bezeichnerwert 0x61626364 (hexadezimal) würde beispielsweise mit "<span class="codeph"> abcd</span>"geschrieben, da der ASCII-Code für "a"0x61 usw. lautet. </td> 
   <td> Nein </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionPayload</span> </td> 
   <td> Eine Base64-kodierte Zeichenfolge der Erweiterung. </td> 
   <td>Ja, wenn <span class="codeph"> der Erweiterungstyp</span> angegeben ist. </td> 
  </tr> 
 </tbody> 
</table>

## Antworten {#section_0079C31B4AF14DBBB6277CF251FB90E3}

**Tabelle 11: HTTP-Antworten**

| **HTTP-Statuscode** | **Beschreibung** | **Content-Type** | **Entitätstext enthält** |
|---|---|---|---|
| `200 OK` | Kein Fehler. | `text/uri-list` | Lizenzakquise-URL und -Token |
| `400 Bad Request` | Ungültige Artikel | `text/html` os `application/json` | Fehlerbeschreibung |
| `401 Unauthorized` | Autom fehlgeschlagen | `text/html` os `application/json` | Fehlerbeschreibung |
| `404 Not found` | Ungültige URL | `text/html` os `application/json` | Fehlerbeschreibung |
| `50x Server Error` | Serverfehler | `text/html` os `application/json` | Fehlerbeschreibung |

**Tabelle 12: Ereignis-Fehlercodes**

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
   <td> Ungültige Ausgabesteuerungs-Flags angegeben: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> Authentifizierungstoken muss angegeben werden </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td>Authentifizierungstoken ungültig: &lt;details&gt; <p>Hinweis:  Dies kann vorkommen, wenn der Authentifizierer falsch ist oder wenn der Zugriff auf die Test-API unter *.test.expressplay.com mit dem Produktionsauthentifizierer erfolgt und umgekehrt. </p> <p importance="high">Hinweis: Das Test SDK und das Advanced Test Tool (ATT) funktionieren nur mit <span class="filepath"> *.test.expressplay.com</span>, während Produktionsgeräte <span class="filepath"> *.service.expressplay.com</span>verwenden müssen. </p> </td> 
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
   <td>Fehlendes <span class="codeph"> Kind</span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Inhaltsschlüssel konnte nicht vom wichtigen Datenspeicherung-Dienst abgerufen werden </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td><span class="codeph"> Kind</span> muss 32 Hexadezimalzeichen lang sein </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td><span class="codeph"> Kind</span> muss 64 Zeichen lang nach dem ^ sein </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td>Ungültiges <span class="codeph"> Kind</span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td>Ungültiger verschlüsselter <span class="codeph"> Schlüssel</span> oder ungültiger Schlüssel </td> 
  </tr> 
  <tr> 
   <td> -5001 </td> 
   <td> Unbekannter Ausgabetypfehler </td> 
  </tr> 
  <tr> 
   <td> -5002 </td> 
   <td> Die Option "PlayReady"ist für diesen Dienst deaktiviert </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Ungültige allgemeine Flags </td> 
  </tr> 
  <tr> 
   <td> -5004 </td> 
   <td> Die Geräte-ID muss 32 Hexadezimalzeichen lang sein. </td> 
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
   <td>Es kann nur einer der <span class="codeph"> Tastenkombinationen</span> oder der <span class="codeph"> Inhaltsschlüssel</span> angegeben werden </td> 
  </tr> 
 </tbody> 
</table>
