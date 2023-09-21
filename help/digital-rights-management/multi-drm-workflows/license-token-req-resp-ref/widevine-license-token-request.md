---
description: Die Widevine-Lizenz-Token-Schnittstelle bietet Produktions- und Testdienste.
title: Anfrage zum Widevine-Lizenz-Token / Antwort
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 5%

---

# Anfrage zum Widevine-Lizenz-Token / Antwort {#widevine-license-token-request-response}

Die Widevine-Lizenz-Token-Schnittstelle bietet Produktions- und Testdienste.

Diese HTTP-Anfrage gibt ein Token zurück, das für eine Widevine-Lizenz eingelöst werden kann.

**Methode: GET, POST** (mit einem www-url-kodierten Textkörper, der Parameter für beide Methoden enthält)

**URLs:**

* **Produktion:** `https://wv-gen.{prod_domain}/hms/wv/token`

* **Test:** ` [https://wv-gen.test.expressplay.com/hms/wv/token](https://wv-gen.test.expressplay.com/hms/wv/token)`

* **Beispielanfrage:**

  ```
  https://wv-gen.service.expressplay.com/hms/wv/token?customerAuthenticator= 
  <ExpressPlay customer authenticator identifier>
  ```

* **Beispielantwort:**

  ```
  https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
  ```

<!--<a id="section_1E22012EE4B94BB2974D3B16DE8812D9"></a>-->

**Tabelle 13: Token-Abfrageparameter**

<table id="table_ww1_hcs_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Abfrageparameter</b> </th> 
   <th class="entry"> <b>Beschreibung</b> </th> 
   <th class="entry"> <b>Erforderlich?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> customerAuthenticator </span> </td> 
   <td> <p>Dies ist Ihr Customer-API-Schlüssel, jeweils einer für Ihre Produktions- und Testumgebungen. Sie finden dies auf der Registerkarte Admin Dashboard von ExpressPlay . </p> </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td> <span class="codeph"> errorFormat </span> </td> 
   <td> Entweder <span class="codeph"> html </span> oder <span class="codeph"> json </span>. <p>Wenn <span class="codeph"> html </span> (Standard) Eine HTML-Darstellung aller Fehler wird im Entitätstext der Antwort bereitgestellt. Wenn <span class="codeph"> json </span> angegeben ist, wird eine strukturierte Antwort im JSON-Format zurückgegeben. Siehe <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON-Fehler </a> für Details. </p> <p>Der MIME-Typ der Antwort lautet entweder <span class="codeph"> text/uri-list </span> zum Erfolg, <span class="codeph"> text/html </span> für <span class="codeph"> html </span> Fehlerformat oder <span class="codeph"> application/json </span> für <span class="codeph"> json </span> Fehlerformat. </p> </td> 
   <td> Nein </td> 
  </tr> 
 </tbody> 
</table>

**Tabelle 14: Lizenzabfrageparameter**

| Abfrageparameter | Beschreibung | Erforderlich? |
|--- |--- |--- |
| `generalFlags` | Ein 4-Byte-Hexadezimalstring, der die Lizenzflags darstellt. &quot;0000&quot;ist der einzige zulässige Wert | Nein |
| `kek` | Schlüssel-Verschlüsselungsschlüssel (KEK). Schlüssel werden mit einem KEK mithilfe eines Schlüsselumbruchalgorithmus (AES Key Wrap, RFC3394) verschlüsselt gespeichert. | Nein |
| `kid` | Eine 16-Byte-Hexadezimal-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels oder eines Strings `^somestring'`. Die Länge des Strings , gefolgt von der `^` darf nicht länger als 64 Zeichen sein. Ein Beispiel finden Sie unten. | Ja |
| `ek` | Eine Hex-String-Darstellung des verschlüsselten Inhaltsschlüssels. | Nein |
| `contentKey` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels | Ja, außer `kek` und `ek` oder `kid` bereitgestellt werden |
| `contentId` | Inhalts-ID | Nein |
| `securityLevel` | Zulässige Werte sind 1-5. <ul><li>1 = `SW_SECURE_CRYPTO`</li><li> 2 = `SW_SECURE_DECODE` </li><li> 3 = `HW_SECURE_CRYPTO` </li><li> 4 = `HW_SECURE_DECODE` </li><li> 5 = `HW_SECURE_ALL`</li></ul> | Ja |
| `hdcpOutputControl` | Zulässige Werte sind 0, 1, 2. <ul><li>0 = `HDCP_NONE` </li><li> 1 = `HDCP_V1` </li><li> 2 = `HDCP_V2`</li></ul> | Ja |
| `licenseDuration` * | Dauer der Lizenz in Sekunden. Wenn keine Angabe gemacht wird, deutet dies darauf hin, dass die Dauer nicht begrenzt ist. Weitere Informationen finden Sie in der unten stehenden Notiz. | Nein |
| `wvExtension` | Eine kurze Form, die extensionType und extensionPayload als kommagetrennte Zeichenfolge umschließt. Siehe Format unten. Beispiel: `…&wvExtension=wudo,AAAAAA==&…` | Nein, eine beliebige Zahl kann verwendet werden |

Info `licenseDuration`: <ol><li> Die Wiedergabe wird beendet `licenseDuration` Sekunden nach Beginn der Wiedergabe. </li><li> Damit die Wiedergabe für eine unbegrenzte Zeit angehalten/fortgesetzt werden kann, lassen Sie `licenseDuration` (standardmäßig unendlich). Geben Sie andernfalls an, wie lange Endbenutzer den Stream nutzen können sollen. </li></ol>

**Tabelle 15: Abfrageparameter für Token-Einschränkungen**

| Abfrageparameter | Beschreibung | Erforderlich? |
|--- |--- |--- |
| `expirationTime` | Ablaufzeit dieses Tokens. Dieser Wert MUSS eine Zeichenfolge in [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) Datums-/Uhrzeitformat im Bereichsbezeichner &quot;Z&quot;(&quot;Zulu-Zeit&quot;) oder eine Ganzzahl, der ein &quot;+&quot;-Zeichen vorangestellt ist. Ein Beispiel für eine RFC 3339-Datums-/Uhrzeitangabe ist 2006-04-14T12:01:10Z. <br> Wenn der Wert eine Zeichenfolge in [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) Datums-/Uhrzeitformat und stellt dann ein absolutes Ablaufdatum/eine absolute Ablaufzeit für das Token dar. Wenn der Wert eine Ganzzahl ist, der ein &quot;+&quot;-Zeichen vorangestellt ist, wird er als relative Anzahl von Sekunden ab Ausgabe interpretiert, dass das Token gültig ist. Beispiel: `+60` gibt eine Minute an. <br> Die maximale und standardmäßige Token-Lebensdauer (falls nicht angegeben) beträgt 30 Tage. | Nein |

**Tabelle 16: Korrelationsabfrageparameter**

| **Abfrageparameter** | **Beschreibung** | **Erforderlich?** |
|---|---|---|
| `cookie` | Beliebige Zeichenfolge mit einer Länge von bis zu 32 Zeichen, die im Token gespeichert und vom Token-Erlösungs-Server protokolliert wird. Kann verwendet werden, um Protokolleinträge auf dem Rückgabeserver und auf den Servern des Dienstleisters zu korrelieren. | Nein |

<!--<a id="section_6BFBD314C77C40C4B172ABBDD2D8D80E"></a>-->

**Tabelle 17: HTTP-Antwort**

| **HTTP-Statuscode** | **Beschreibung** | **Content-Type** | **Entitätstext enthält** |
|---|---|---|---|
| `200 OK` | Kein Fehler. | `text/uri-list` | Lizenzakquise-URL + Token |
| `400 Bad Request` | Ungültige Protokolle | `text/html` oder `application/json` | Fehlerbeschreibung |
| `401 Unauthorized` | Autor fehlgeschlagen | `text/html` oder `application/json` | Fehlerbeschreibung |
| `404 Not found` | Ungültige URL | `text/html` oder `application/json` | Fehlerbeschreibung |
| `50x Server Error` | Server-Fehler | `text/html` oder `application/json` | Fehlerbeschreibung |

**Tabelle 18: Fehlercodes für Ereignisse**

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
   <td> Ungültige Flags der Ausgabesteuerung angegeben: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> Authentifizierungstoken muss angegeben werden </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td> Authentifizierungstoken ungültig: &lt;details&gt; <p>Hinweis: Dies kann vorkommen, wenn der Authentifizierer falsch ist oder wenn er mithilfe des Produktionsauthentifikators unter *.test.expressplay.com auf die Test-API zugreift und umgekehrt. </p> <p importance="high">Hinweis: Das Test-SDK und das Advanced Test Tool (ATT) funktionieren nur mit <span class="filepath"> *.test.expressplay.com </span>, während Produktionsgeräte <span class="filepath"> *.service.expressplay.com </span> </p>. </td> 
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
   <td> Fehlt <span class="filepath"> Kind </span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Inhaltsschlüssel konnte nicht vom Schlüsselspeicherdienst abgerufen werden </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> Kind </span> muss 32 hexadezimale Zeichen lang sein </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> Kind </span> muss 64 Zeichen lang nach dem '^' sein </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> Ungültig <span class="codeph"> Kind </span> </td> 
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
   <td> Fehlender Wert auf der Sicherheitsstufe </td> 
  </tr> 
  <tr> 
   <td> -7004 </td> 
   <td> Ungültiger Sicherheitsstufenwert </td> 
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
   <td> Ungültig <span class="codeph"> WVExtension </span> Parameter angegeben </td> 
  </tr> 
  <tr> 
   <td> -7011 </td> 
   <td> Weitwinkeloption deaktiviert </td> 
  </tr> 
 </tbody> 
</table>
