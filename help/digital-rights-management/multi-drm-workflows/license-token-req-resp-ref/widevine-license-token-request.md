---
description: Die Widevine-Lizenz-Token-Schnittstelle bietet Produktions- und Testdienste.
seo-description: Die Widevine-Lizenz-Token-Schnittstelle bietet Produktions- und Testdienste.
seo-title: Anfrage/Antwort zum Java-LizenzToken
title: Anfrage/Antwort zum Java-LizenzToken
uuid: a3522422-7075-49a7-bc55-137ef84ee430
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 5%

---


# Anforderung eines Java-Lizenz-Tokens / Antwort {#widevine-license-token-request-response}

Die Widevine-Lizenz-Token-Schnittstelle bietet Produktions- und Testdienste.

Diese HTTP-Anforderung gibt ein Token zurück, das für eine Widevine-Lizenz eingelöst werden kann.

**Methode: GET, POST**  (mit einem www-url-kodierten Textkörper, der Parameter für beide Methoden enthält)

**URLs:**

* **Produktion:** `https://wv-gen.{prod_domain}/hms/wv/token`

* **Test:** ` [https://wv-gen.test.expressplay.com/hms/wv/token](https://wv-gen.test.expressplay.com/hms/wv/token)`

* **Beispielanforderung:**

   ```
   https://wv-gen.service.expressplay.com/hms/wv/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier>
   ```

* **Beispielantwort:**

   ```
   https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

<!--<a id="section_1E22012EE4B94BB2974D3B16DE8812D9"></a>-->

**Tabelle 13: Token-Abfragen-Parameter**

<table id="table_ww1_hcs_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Abfrage-Parameter</b> </th> 
   <th class="entry"> <b>Beschreibung</b> </th> 
   <th class="entry"> <b>Erforderlich?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> customerAuthenticator  </span> </td> 
   <td> <p>Dies ist Ihr Kunde-API-Schlüssel, einer für Ihre Produktions- und Testing-Umgebung. Sie finden dies auf der Registerkarte "ExpressPlay Admin-Dashboard". </p> </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td> <span class="codeph"> errorFormat  </span> </td> 
   <td> Entweder <span class="codeph"> html </span> oder <span class="codeph"> json </span>. <p>Wenn <span class="codeph"> html </span> (Standard), wird eine HTML-Darstellung aller Fehler im Entitätstext der Antwort bereitgestellt. Wenn <span class="codeph"> json </span> angegeben ist, wird eine strukturierte Antwort im JSON-Format zurückgegeben. Weitere Informationen finden Sie unter <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON-Fehler </a>. </p> <p>Der Mime-Typ der Antwort lautet entweder <span class="codeph"> text/uri-Liste </span> bei Erfolg, <span class="codeph"> text/html </span> bei <span class="codeph"> html </span> Fehlerformat oder <span class="codeph"> application/json </span> bei <span class="codeph"> json </span> Fehlerformat. </p> </td> 
   <td> Nein </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 14: Lizenzparameter für Abfragen**

| Abfrage-Parameter | Beschreibung | Erforderlich? |
|--- |--- |--- |
| `generalFlags` | Eine Hexadezimalzeichenfolge mit 4 Byte, die die Lizenzflags darstellt. &quot;0000&quot;ist der einzige zulässige Wert | Nein |
| `kek` | Schlüssel-Verschlüsselungsschlüssel (KEK). Schlüssel werden verschlüsselt mit einem KEK mit einem Schlüsselumbruch-Algorithmus (AES Key Wrap, RFC3394) gespeichert. | Nein |
| `kid` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels oder eine Zeichenfolge `^somestring'`. Die Länge der Zeichenfolge gefolgt von `^` darf 64 Zeichen nicht überschreiten. Ein Beispiel finden Sie unter Hinweis. | Ja |
| `ek` | Eine Hex-String-Darstellung des verschlüsselten Inhaltsschlüssels. | Nein |
| `contentKey` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels | Ja, es sei denn, `kek` und `ek` oder `kid` werden bereitgestellt |
| `contentId` | Inhalts-ID | Nein |
| `securityLevel` | Zulässige Werte sind 1-5. <ul><li>1 = `SW_SECURE_CRYPTO`</li><li> 2 = `SW_SECURE_DECODE` </li><li> 3 = `HW_SECURE_CRYPTO` </li><li> 4 = `HW_SECURE_DECODE` </li><li> 5 = `HW_SECURE_ALL`</li></ul> | Ja |
| `hdcpOutputControl` | Zulässige Werte sind 0, 1, 2. <ul><li>0 = `HDCP_NONE` </li><li> 1 = `HDCP_V1` </li><li> 2 = `HDCP_V2`</li></ul> | Ja |
| `licenseDuration` * | Dauer der Lizenz in Sekunden. Falls nicht angegeben, deutet dies darauf hin, dass die Dauer nicht begrenzt ist. Für detaillierte Informationen lesen Sie bitte den unten stehenden Hinweis. | Nein |
| `wvExtension` | Eine kurze Form, in die die Erweiterungen &quot;extensionType&quot;und &quot;extensionPayload&quot;als kommagetrennte Zeichenfolge eingeschlossen werden. Siehe unten stehendes Format. Beispiel: `…&wvExtension=wudo,AAAAAA==&…` | Nein, eine beliebige Zahl kann verwendet werden |

Über `licenseDuration`: <ol><li> Die Wiedergabe wird nach Beginn der Wiedergabe `licenseDuration` Sekunden beendet. </li><li> Damit die Wiedergabe für eine unbegrenzte Zeit gestoppt/fortgesetzt werden kann, lassen Sie `licenseDuration` weg (standardmäßig ist unendlich). Geben Sie andernfalls an, wie lange Endbenutzer den Stream nutzen können sollen. </li></ol>

**Tabelle 15: Token-Zugriffsparameter für Abfragen**

| Abfrage-Parameter | Beschreibung | Erforderlich? |
|--- |--- |--- |
| `expirationTime` | Ablaufzeit dieses Tokens. Dieser Wert MUSS eine Zeichenfolge im Datums-/Uhrzeitformat [RFC 339](https://www.ietf.org/rfc/rfc3339.txt) im Z-Zonenbezeichner (&quot;Zulu-Zeit&quot;) oder eine Ganzzahl mit vorangestelltem +-Zeichen sein. Ein Beispiel für ein RFC 3339 Datum/Uhrzeit ist 2006-04-14T12:01:10Z. <br> Wenn der Wert eine Zeichenfolge im  [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) Datums-/Uhrzeitformat ist, stellt er ein absolutes Ablaufdatum/eine absolute Ablaufzeit für das Token dar. Wenn der Wert eine Ganzzahl ist, der ein +-Zeichen vorangestellt ist, wird er als relative Anzahl von Sekunden ab Ausgabe interpretiert, dass das Token gültig ist. Beispiel: `+60` gibt eine Minute an. <br> Die Gültigkeitsdauer des Tokens beträgt maximal 30 Tage (sofern nicht angegeben). | Nein |

**Tabelle 16: Korrelationsparameter für Abfragen**

| **Abfrage-Parameter** | **Beschreibung** | **Erforderlich?** |
|---|---|---|
| `cookie` | Beliebige Zeichenfolge mit einer Länge von bis zu 32 Zeichen, die im Token gespeichert und vom Token-Einlösungsserver protokolliert wurde. Kann verwendet werden, um Protokolleinträge auf dem Einlöseserver und auf den Servern des Dienstleisters zu korrelieren. | Nein |

<!--<a id="section_6BFBD314C77C40C4B172ABBDD2D8D80E"></a>-->

**Tabelle 17: HTTP-Antwort**

| **HTTP-Statuscode** | **Beschreibung** | **Content-Type** | **Entitätstext enthält** |
|---|---|---|---|
| `200 OK` | Kein Fehler. | `text/uri-list` | Lizenzakquise-URL + Token |
| `400 Bad Request` | Ungültige Artikel | `text/html` oder  `application/json` | Fehlerbeschreibung |
| `401 Unauthorized` | Autom fehlgeschlagen | `text/html` oder  `application/json` | Fehlerbeschreibung |
| `404 Not found` | Ungültige URL | `text/html` oder  `application/json` | Fehlerbeschreibung |
| `50x Server Error` | Serverfehler | `text/html` oder  `application/json` | Fehlerbeschreibung |

**Tabelle 18: Ereignis-Fehlercodes**

<table id="table_agj_gqx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> Code </th> 
   <th class="entry"> Beschreibung </th> 
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
   <td> Authentifizierungstoken ungültig: &lt;details&gt; <p>Hinweis:  Dies kann vorkommen, wenn der Authentifizierer falsch ist oder wenn der Zugriff auf die Test-API unter *.test.expressplay.com mit dem Produktionsauthentifizierer erfolgt und umgekehrt. </p> <p importance="high">Hinweis:  Das Test SDK und das Advanced Test Tool (ATT) funktionieren nur mit <span class="filepath"> *.test.expressplay.com </span>, während Produktionsgeräte <span class="filepath"> *.service.expressplay.com </span> verwenden müssen </p>. </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> Nicht genügend Token verfügbar </td> 
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
   <td> Fehlendes <span class="filepath"> Kind </span> </td> 
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
   <td> <span class="codeph"> Kind  </span> muss 64 Zeichen lang nach dem '^' sein </td> 
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
   <td> -6005 </td> 
   <td> Ungültige Schlüsseldaten angegeben </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> Ungültige Mietdauer angegeben </td> 
  </tr> 
  <tr> 
   <td> -7002 </td> 
   <td> Die Bindung der Geräte-ID wird für Widevine nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td> -7003 </td> 
   <td> Fehlender Wert auf Sicherheitsstufe </td> 
  </tr> 
  <tr> 
   <td> -7004 </td> 
   <td> Ungültiger Wert für Sicherheitsstufe </td> 
  </tr> 
  <tr> 
   <td> -7006 </td> 
   <td> Fehlender HDCP-Ausgabekontrollwert </td> 
  </tr> 
  <tr> 
   <td> -7007 </td> 
   <td> Ungültige Lizenzdauer angegeben </td> 
  </tr> 
  <tr> 
   <td> -7008 </td> 
   <td> Widevine-Lizenz konnte nicht generiert werden </td> 
  </tr> 
  <tr> 
   <td> -7009 </td> 
   <td> Ungültige Parameter <span class="codeph"> WVExtension </span> angegeben </td> 
  </tr> 
  <tr> 
   <td> -7011 </td> 
   <td> Option "Wide"deaktiviert </td> 
  </tr> 
 </tbody> 
</table>