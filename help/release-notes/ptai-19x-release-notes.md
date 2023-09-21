---
title: Versionshinweise zu PTAI 19.11.1
description: Die Versionshinweise zu PTAI 19.11.1 beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in Primetime Ad Insertion im Jahr 2019.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1971'
ht-degree: 0%

---

# Primetime Ad Insertion 19.11.1 - Versionshinweise

Die Primetime-Ad Insertion-Versionshinweise 19.11.1 beschreiben, was neu ist oder geändert wurde, Probleme gelöst wurden und bekannte Probleme in Primetime Ad Insertion im Jahr 2019.

## Neue Funktionen in PTAI 19.11.1

**Wenn:** Montag, 4. November 2019 um 12:01 Uhr bis 01:00 Uhr OSTERN

Wartungs-Updates.

## Änderungen in früheren Versionen

### Version 19.10.2

**Wenn:** Donnerstag, 31. Oktober 2019 von 01:00 Uhr bis 03:00 Uhr morgens

Wartungs-Updates.

### Version 19.10.1

**Wenn:**  Dienstag, 22. Oktober um 01:00 Uhr bis 02:00 UHR OSTERN

Wartungs-Updates.

### Version 19.9.1

**Wenn:** Dienstag, 10. September 2019, 12:30 Uhr bis 2:00 Uhr Ostzeit

Sicherheitsaktualisierungen

### Version 19.8.3

**Wenn:** Mittwoch, 28. August 2019, 12:30 - 01:30 Uhr EASTERN

Es wurde ein Fehler behoben, durch den Chromecast-Player unerwartet die Wiedergabe beendet haben, wenn Anzeigensegmente aus dem DVR-Fenster ausgerollt wurden.

### Version 19.8.2

**Wenn:** Mittwoch, 21. August 2019, 2:00 Uhr bis 3:00 Uhr Ostzeit

* SSAI-Dashboard: Abschnitt Sitzungsstatistik . Sie können die Sitzungsereignisse über die Option CSV herunterladen exportieren.

* Wartungsaktualisierungen

### Version 19.8.1

**Wenn:** Dienstag, 6. August 2019, 2:30 AM Eastern Time to Dienstag, 6. August 2019, 4:30 AM Eastern Time

* SSAI-Dashboard: Zum SSAI-Dashboard wurde der neue Abschnitt Sitzungsstatistik hinzugefügt.
   * Wenn Sie die Sitzungs-ID für eine SSAI-Sitzung haben, für die der Debug-Modus aktiviert war (ptdebug=true), können Sie die folgende Aktivität nachschlagen, die in dieser Sitzung aufgetreten ist:
      * Anzeigenanforderungen/Antworten
      * Eingefügte Anzeigen
      * Ausgelöste Beacons (nur serverseitige Verfolgung)

   * Sie können die Aktivität für eine bestimmte Sitzungs-ID bis zu 30 Tage nach dieser SSAI-Sitzung nachschlagen
   * Sie können die Ereignisse exportieren
* Datenbank: Sicherheitsupdates

### Version 19.7.1

**Wenn:** Mittwoch, 10. Juli

* SSAI: Für ptcueformat-Werte, die die EXT-X-CUE-OUT-Anzeigenunterbrechung in Live-Streams unterstützen, wurde ein allgemeines Makro hinzugefügt, um Daten aus Attributen im EXT-X-ASSET-Tag-Beispiel zu übergeben: Tag, das das Tag #EXT-X-CUE-OUT begleitet: #EXT-X-ASSET:CAID=75BCD15,GENRE=News,Program=News 10 Makros: # kann verwendet werden, um News (vom GENRE-Attribut) an eine URL-Nummer für Anzeigenaufrufe zu übergeben. Mit # können Sie NewsAt10 (aus dem Programmattribut) an eine URL-Ausnahme für Anzeigenaufrufe weiterleiten: Für Abwärtskompatibilität haben # und # dieselbe Funktionalität. Beide Makros können verwendet werden, um den Wert des CAID-Attributs zu übergeben, nachdem der Wert aus Hex in long konvertiert wurde. Der long-Wert ist 123456789 für den Hexadezimalwert 75BCD15 im oben stehenden Beispiel. Beide Makros werden verwendet, um 123456789 an eine Anzeigen-Aufruf-URL zu übergeben. Das Makro beginnt immer mit #. Beim Makro wird zwischen Groß- und Kleinschreibung unterschieden, das Attribut im EXT-X-ASSET-Tag jedoch nicht. Das heißt, sowohl PROGRAMM als auch Programm sind im EXT-X-ASSET-Tag zulässig
* SSAI: Konfigurationsänderungen für einen bestimmten Kunden für Folgendes:
   * Länge des beweglichen Fensters (Live-Playlist) von vier Minuten
   * Wenn beim Abrufen des Quellinhalts durch den Manifestserver eine Socket-Timeout-Ausnahme ausgelöst wird, gibt der Manifestserver den HTTP-Antwortcode (404) anstelle von 500 zurück.
* Sicherheitsaktualisierungen

### Version 19.6.1

**Wenn:** Mittwoch, 12. Juni 2019, 11:30 Uhr PST bis Donnerstag, 13. Juni 2019, 12:30 Uhr PST

* CRS: Normalisierungsregel für Kreative aus RevJet
   * Es wurde eine kreative URL-Normalisierungsregel für RevJet hinzugefügt, die von CRS und SSAI verwendet wird.
   * TVSDK: Wenn Sie Anzeigen von RevJet bereitstellen oder bereitstellen möchten, müssen die Normalisierungsregeln der CRS-Regeln-JSON hinzugefügt werden, um CRS mit ihren Kreativen verwenden zu können. Wenden Sie sich an Ihren technischen Kundenbetreuer, um Unterstützung zu erhalten.
* CRS: Normalisierungsregel für Kreative von Innovid
   * Hinzufügung der von SSAI verwendeten kreativen URL-Normalisierungsregel für Innovid
   * Die von CRS verwendete Normalisierungsregel wurde in einer früheren Version hinzugefügt
   * TVSDK: Die Normalisierungsregel, die in die CRS Rules JSON hinzugefügt werden soll, wurde nach einer vorherigen Version bereitgestellt. Um jedoch sicher zu sein, wenden Sie sich an Ihren technischen Kundenbetreuer, um alle vorhandenen Normalisierungsregeln zu überprüfen.
     >[!NOTE]
     >
     >Die meisten integrierten kreativen URLs werden ohne die Normalisierungsregel transkodiert und erfolgreich zugeordnet. Gelegentlich treten jedoch kreative URLs mit dynamischen Parametern auf. Die Normalisierungsregel ist erforderlich, um diese Instanzen zu verarbeiten.

### Version 19.5.2

**Wenn:** Mittwoch, 22. Mai, 22:30 Uhr Ostzeit bis Mittwoch, 22. Mai, 22:30 Uhr Ostzeit

* Unterstützung für CMAF (HLS/fMP4-Inhalt) hinzugefügt
   * SSAI: Umgang mit CMAF-Manifesten
   * SSAI: Initiieren von Transkodierungsanfragen und Abrufen von CRS-Assets abhängig vom Inhaltsformat (HLS/ts und HLS/fMP4)
   * CRS: Hinzugefügter Workflow zum Repacken von Anzeigen im CMAF-Format (HLS/fMP4)
* SSAI: Es wurde ein Problem behoben, durch das verhindert wurde, dass unverschraubte Anzeigen in ungemusterten Inhalt eingefügt werden, wenn sowohl der Inhalt als auch die Anzeige keine rein Audio-Streams haben (EXT-X-STREAM-INF).
* SSAI: Unterstützung für CDN-Authentifizierungstoken für Limelight (LLNW) für Inhaltssegmente hinzugefügt
   * Wann `pttoken=limelight` oder `pttoken=llnw` zur Bootstrap-URL hinzugefügt wird, fügen wir beim Abrufen der Quell-Master-Playlist einen geheimen Header hinzu. Anschließend hängen wir die Abfrageparameter aus der X-Adobe-Sig-Kopfzeile von LLNW an die Inhaltssegmente an
* SSAI: Es wurde ein weiterer pttoken-Wert hinzugefügt (`pttoken=centurylink`) für die CenturyLink CDN auth Token-Unterstützung, die am 30. Juli 2018 veröffentlicht wurde
   * `pttoken=centurylink` hat dasselbe Verhalten wie `pttoken=level3`und beide Werte sind gültig

### Version 19.5.1

**Wenn:** Donnerstag, 9. Mai 20:30 Uhr Ostzeit bis Donnerstag, 9. Mai um 9:30 Uhr Ostzeit

* SSAI: Sicherheitsupdates
* CRS-Dashboard: Kürzung der Zeichenfolge &quot;FqAdId-Beispiel&quot;auf 255 Zeichen aufgrund von Datenspeicherungsbeschränkungen (8 Bit)
   * Die Zeichenfolge &quot;FqAdId-Beispiel&quot;enthält das Anzeigensystem und die Anzeigen-ID aus jeder XML-Antwort in der Wrapper-Kette der Werbeanzeige für Einfügungen aller CRS-Anzeigen mit SSAI (Abschnitt &quot;Kreative Statistiken&quot;des CRS-Dashboards)
* SSAI- und CRS-Dashboards: Aktualisierungen der Softwareversion

### Version 19.4.1

**Wenn:** Mittwoch, 10. April 10, 2:30 Uhr Ostzeit bis Mittwoch, 10. April, 10:30 Uhr Ostzeit

* CRS: Die CRS-Repackaging-API unterstützt keine HTTP-POST-Befehle mehr. Die CRS-Repackaging-API leitet HTTP-POST-Befehle (301) automatisch zu HTTPS um
   * Ab dem 20. Mai wird die HTTP->HTTPS-Umleitung für HTTP-POST-Befehle deaktiviert
   * Wenn Sie die CRS Repackaging API verwenden, um Anzeigen vorab zu verpacken, wechseln Sie bis zum 20. Mai Ihre POST-Befehle zu HTTPS
* CRS: Architektur und Workflow zum Hochladen von CRS-Assets in die CDN-Herkunft von Kunden neu gestaltet
   * Auftragsprozesse pro CDN-Herkunft sind getrennt. Daher wirken sich Upload-Engpässe für eine CDN-Herkunft nicht auf Uploads in andere CDN-Quellen aus
   * Weitere Vorteile: Die Verarbeitungszeiten von CRS-Vorgängen und die Upload-Raten in CDN-Quellen von Kunden werden verbessert
* SSAI: ClickThrough- und ClickTracking-URLs für Videoanzeigen wurden zum JSON v2-Sidecar-Format hinzugefügt
   * Die neue JSON-Array-Eigenschaft &quot;videoClicks&quot;folgt der Eigenschaft &quot;trackingURLs&quot;
   * Die &quot;event&quot;-Wertnamen lauten &quot;clickThrough&quot;und &quot;clickTracking&quot;, und sie haben keinen startTime-Wert
* SSAI: Für CRS-Assets wurde eine Funktion hinzugefügt, mit der die Gültigkeit des Suchdatensatzes eines CRS-Assets beim Einfügen um 30 Tage verlängert werden kann.
   * Vorheriges Verhalten: CRS-Asset-Suchdatensätze werden in jedem Pod im Memcache gespeichert. CRS-Asset-Suchdatensätze werden 30 Tage nach dem Hinzufügen zum Memcache automatisch entfernt. Um den CRS-Asset-Suchdatensatz eines Kreativs in einem Pod zu replizieren, nachdem er aus dem Memcache entfernt wurde, muss in diesem Pod dreimal auf dieses Kreativelement gestoßen werden
   * Neues Verhalten: Wenn ein Pod auf einen CRS-Asset-Lookup-Datensatz zugreift, um das CRS-Asset einzufügen, wird die Gültigkeit des CRS-Asset-Lookup-Datensatzes in diesem Pod um 30 Tage verlängert. Daher werden häufig verwendete CRS-Assets erst 30 Tage nach ihrer letzten Verwendung aus dem Memcache eines Pods entfernt
   * Das neue Verhalten ist systemweit verfügbar und kann deaktiviert werden, wenn ein Leistungsabfall erkannt wird
* SSAI: Aktualisiertes WebVTT-Manifestmanipulationsverhalten nur für Live-Streams
   * Vorheriges Verhalten: Entfernen Sie nur im WebVTT-Manifest EXT-X-DISCONTINUITY -Tags, die vor jeder eingefügten Anzeige und nach dem letzten Segment der eingefügten Werbeunterbrechung eingefügt werden.
   * Neues Verhalten: Der SSAI-Bootstrap-URL wurde der neue Parameter vttdisk mit den akzeptierten Werten true und false hinzugefügt.
      * vttdisk=true: EXT-X-DISCONTINUITY -Tags werden vor jeder eingefügten Anzeige und nach dem letzten Segment der eingefügten Werbeunterbrechung in das WebVTT-Manifest eingefügt, was dem Verhalten für Audio-/Video- und Nur-Audio-Manifeste entspricht.
      * vttdisk=false (dasselbe wie das vorherige Verhalten): Entfernen Sie nur im WebVTT-Manifest EXT-X-DISCONTINUITY-Tags, die vor jeder eingefügten Anzeige und nach dem letzten Segment der eingefügten Werbeunterbrechung eingefügt werden würden
      * Wenn der vttdisk-Parameter weggelassen wird oder einen anderen Wert als &quot;true/false&quot;hat, wird vttdisk standardmäßig auf &quot;true&quot;gesetzt
* SSAI: Sicherheitsupdates und Softwareversionsaktualisierungen
   * Java: Aktualisierte Java-Version, die zusätzliche Chiffre-Suites für über TLS 1.2 (HTTPS) ausgelöste Anzeigenaufrufe unterstützt

### Version 19.2.1

**Wenn:** Mittwoch, 20. Februar 2019 1:30 Uhr Ostzeit bis Mittwoch, 20. Februar 2019, 3:30 Uhr Ostzeit

* SSAI: ClickThrough- und ClickTracking-URLs für Videoanzeigen wurden zum JSON v2-Sidecar-Format hinzugefügt
   * Unter der Eigenschaft &quot;trackingURLs&quot;lauten die Namen ihrer &quot;event&quot;-Werte &quot;Clickthrough&quot;und &quot;clickTracking&quot;.
   * Ihre startTime -Werte sind der Anfang der Anzeige
* SSAI: Für CRS-Assets wurde eine Funktion hinzugefügt, mit der die Gültigkeit des Suchdatensatzes eines CRS-Assets beim Einfügen um 30 Tage verlängert werden kann.
   * Vorheriges Verhalten: CRS-Asset-Suchdatensätze werden in jedem Pod im Memcache gespeichert. CRS-Asset-Suchdatensätze werden 30 Tage nach dem Hinzufügen zum Memcache automatisch entfernt. Um den CRS-Asset-Suchdatensatz eines Kreativs in einem Pod zu replizieren, nachdem er aus dem Memcache entfernt wurde, muss in diesem Pod dreimal auf dieses Kreativelement gestoßen werden
   * Neues Verhalten: Wenn ein Pod auf einen CRS-Asset-Lookup-Datensatz zugreift, um das CRS-Asset einzufügen, wird die Gültigkeit des CRS-Asset-Lookup-Datensatzes in diesem Pod um 30 Tage verlängert. Daher werden häufig verwendete CRS-Assets erst 30 Tage nach ihrer letzten Verwendung aus dem Memcache eines Pods entfernt
   * Das neue Verhalten ist systemweit verfügbar und kann deaktiviert werden, wenn ein Leistungsabfall erkannt wird

* SSAI: Updates der Softwareversion für NGINX und Kafka
   * NGINX und Kafka werden zum Auslösen von Anzeigen-Tracking-URLs serverseitig und zum Senden von Daten an die SSAI- und CRS-Dashboards verwendet
* CRS: Leistungsverbesserungen am CRS-Dashboard

### Veröffentlichung der Web-Benutzeroberfläche

**Wenn:** Mittwoch, 13. Februar, 4:00 - 4:30 Uhr Pazifik

**Was:** Komponente der Web-Benutzeroberfläche von Primetime und Decisioning

* Korrektur des Problems mit der Kalenderbenutzeroberfläche, bei dem der Benutzer beim Tracken einer Kampagne oder beim Abrufen eines Berichts kein Datum über den 31. Dezember 2018 hinaus aus der Kalenderkomponente auswählen konnte.

### Version 19.1.2

**Wenn:** Mittwoch, 30. Januar 2019 1:30 Uhr Ostzeit bis Mittwoch, 30. Januar 30:30 Uhr Ostzeit

* SSAI: Die Suchschlüsselstruktur, die SSAI verwendet, um CRS-Assets zu speichern und abzurufen, wurde aktualisiert, um Szenarien zu verarbeiten, in denen Anzeigenanbieter über eine dynamische Anzeigen-ID oder Creative ID für dieselbe Anzeige verfügen.
   * Neue Lookup-Schlüsselstruktur: Zone-, Creative-URL- und Formatparameter (Zieldauer, Ausgabeformat, Ziel-CDN)
   * Alte Lookup-Schlüsselstruktur: Zone-, Anzeigen-System-, Anzeigen-ID-, Creative-ID-, Creative-URL- und Formatparameter (Zieldauer, Ausgabeformat, Ziel-CDN)
   * Die Lookup-Schlüssel für vorhandene CRS-Assets werden aktualisiert, damit sie vor der Produktionsversion der neuen Struktur entsprechen. Beachten Sie jedoch, dass neue Assets, die zwischen der Aktualisierung der Lookup-Schlüssel und der Produktionsversion transkodiert wurden, möglicherweise fehlen. Wenn dies der Fall ist, initiieren sie eine neue CRS-Anfrage, wenn sie nach der Veröffentlichung das nächste Mal auftreten.

* CRS: Es wurde die Möglichkeit zur Blockierungsliste/Zulassungsliste von CRS-Anforderungen aus bestimmten Anzeigensystemen, Anzeigen-IDs, kreativen IDs, kreativen URLs und/oder kreativen Formaten hinzugefügt.

  >Hinweis
  >
  >Adobe fügt Blockierungsliste-Regeln hinzu, wenn Anzeigenanbieter mit dynamischen Werten (z. B. dynamischer Parameter in URL) für dieselbe Anzeige gefunden werden. Solche Blockierungsliste-Regeln werden deaktiviert, nachdem die dynamische Komponente aufgelöst wurde, entweder durch den Provider oder durch eine Normalisierungsregel.

   * Wenn Sie eine Blockierungsliste- oder Zulassungsliste-Regel für Ihre Zone hinzufügen möchten, wenden Sie sich an Ihren technischen Kundenbetreuer, um Hilfe zu erhalten.

### Version 19.1.1

**Wenn:** Mittwoch, 9. Januar 2019 1:30 Uhr Ostzeit bis Mittwoch, 9. Januar um 9:30 Uhr Ostzeit

* Es wurde ein Problem behoben, bei dem eine falsche Interpretation von HTTP-Keep-Alive-Headern zu einem Fehler führen kann, wenn eingehende Kreativ-Assets validiert werden, die auf total-stream.net gehostet werden.
* Es wurde ein Problem behoben, bei dem einfache Anführungszeichen (&#39;) und doppelte Anführungszeichen (&quot;) in Anzeigen-ID-, Kreativ-ID- und anderen Feldern für eine Neuverpackungsanfrage dazu führten, dass die Neuverpackungsanforderung fehlschlug.
* Wird zu Java long (Datentyp) umgestellt, um ein Problem zu beheben, bei dem das Erreichen der Java-int-Grenze von 2.147.483.647 bei der Transkodierung von Auftrags-ID-Werten dazu führt, dass alle Neuverpackungsanfragen fehlschlagen.
* Datenbankoptimierungen.

## Gelöste Probleme

Wenn die Lösung mit einem gemeldeten Problem verknüpft ist, wird eine Zendesk-Referenz angezeigt. Beispiel: ZD#xxxxx.

**PTAI 19.7.1**

ZD#37503 - JSON-Antworten für die CRS-Regeln werden zwischengespeichert, um doppelte Anforderungen zu vermeiden.

## Bekannte Probleme und Einschränkungen

**PTAI 19.7.1**

Keine neue Einschränkung hinzugefügt.
