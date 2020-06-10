---
title: PTAI 19.11.1 - Versionshinweise
description: Die Versionshinweise zu PTAI 19.11.1 beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in Primetime Dynamic Ad Insertion im Jahr 2019.
translation-type: tm+mt
source-git-commit: 0a58cce0d80ade581e32b5dd9376d336e02fac8b
workflow-type: tm+mt
source-wordcount: '1968'
ht-degree: 0%

---


# Primetime Dynamic Ad Insertion 19.11.1 - Versionshinweise

Versionshinweise zur dynamischen Anzeigeneinfügung 19.11.1 beschreiben, was neu oder geändert ist, gelöste Probleme und bekannte Probleme bei der Primetime-Einführung dynamischer Anzeigen im Jahr 2019.

## Neue Funktionen in PTAI 19.11.1

**Wenn:** Montag, 4. November 2019 um 12:01 Uhr bis 01:00 Uhr OSTERN

Aktualisierungen der Wartung.

## Änderungen in früheren Versionen

### Version 19.10.2

**Wenn:** Donnerstag, 31. Oktober 2019 von 01:00 Uhr bis 03:00 Uhr morgens

Aktualisierungen der Wartung.

### Version 19.10.1

**Wenn:**  Dienstag, 22. Oktober um 01:00 Uhr bis 02:00 UHR OSTSEHR

Aktualisierungen der Wartung.

### Version 19.9.1

**Wenn:** Dienstag, 10. September 2019, 12:30 Uhr bis 2:00 Uhr östliche Zeit

Sicherheitsaktualisierungen

### Version 19.8.3

**Wenn:** Mittwoch, 28. August 2019, 12:30 Uhr - 01:30 Uhr früh im Osten

Es wurde ein Fehler behoben, durch den Chromecast-Player die Wiedergabe unerwartet abgebrochen haben, wenn Anzeigensegmente aus dem DVR-Fenster gerollt wurden.

### Version 19.8.2

**Wenn:** Mittwoch, 21. August 2019, 2:00 Uhr bis 3:00 Uhr östliche Zeit

* SSAI-Dashboard: Abschnitt &quot;Sitzungsstatistik&quot;. Sie können die Session-Ereignis über die Option CSV herunterladen exportieren.

* Aktualisierungen der Wartung

### Version 19.8.1

**Wenn:** Dienstag, 6. August 2019, 2:30 Uhr Ostzeit bis Dienstag, 6. August 2019, 4:30 Uhr Ostzeit

* SSAI-Dashboard: Der neue Abschnitt &quot;Sitzungsstatistik&quot;wurde zum SSAI-Dashboard hinzugefügt
   * Wenn Sie die Sitzungs-ID für eine SSAI-Sitzung haben, für die der Debug-Modus aktiviert war (ptdebug=true), können Sie die folgende Aktivität nachschlagen, die in dieser Sitzung aufgetreten ist:
      * Anzeigenanforderungen/Antworten
      * Eingefügte Anzeigen
      * Ausgelöste Beacons (nur serverseitige Verfolgung)
   * Sie können die Aktivität für eine bestimmte Sitzungs-ID bis zu 30 Tage nach der Sitzung des SAI nachschlagen
   * Sie können die Ereignis exportieren
* Datenbank: Sicherheitsaktualisierungen

### Version 19.7.1

**Wenn:** Mittwoch, 10. Juli

* SAI: Für ptcuformat-Werte, die die Ausf.-X-CUE-OUT-Anzeigenunterbrechungssignalisierung in Live-Streams unterstützen, wurde ein generisches Makro hinzugefügt, um Daten aus Attributen im EXT-X-ASSET-Tag-Beispiel zu übermitteln: Tag, das dem Tag #EXT-X-CUE-OUT beigefügt ist: #EXT-X-ASSET:CAID=75BCD15,GENRE=News,Programm=NewsAt10 Makros: # kann verwendet werden, um News (vom GENRE-Attribut) an eine Anzeigen-Aufruf-URL zu übergeben. # kann verwendet werden, um NewsAt10 (vom Programm-Attribut) an eine Anzeige-Aufruf-URL-Ausnahme zu übergeben: Für die Abwärtskompatibilität haben # und # dieselbe Funktionalität. Beide Makros können verwendet werden, um den Wert des CAID-Attributs zu übergeben, nachdem der Wert von hex in long konvertiert wurde Der lange Wert ist 123456789 für den Hexadezimalwert 75BCD15 im oben gezeigten Beispiel. Beide Makros werden verwendet, um 123456789 an eine Anzeigenaufruf-URL zu übergeben. Das Makro wird immer mit # Beginn. Beim Makro wird die Groß-/Kleinschreibung beachtet, das Attribut im EXT-X-ASSET-Tag jedoch nicht. Das heißt, PROGRAMM und Programm sind im EXT-X-ASSET-Tag zulässig.
* SAI: Konfigurationsänderungen für einen bestimmten Kunden für Folgendes:
   * Länge des Sliding-Fensters (Live-Playlist) von vier Minuten
   * Wenn beim Abrufen des Quellinhalts durch den Manifestserver eine Ausnahme wegen des Socket-Timeouts ausgelöst wird, gibt der Manifestserver den HTTP-Antwortcode (404) anstelle von 500 zurück
* Sicherheitsaktualisierungen

### Version 19.6.1

**Wenn:** Mittwoch, 12. Juni 2019, 11:30 PST bis Donnerstag, 13. Juni 2019, 12:30 PST

* CRS: Normalisierungsregel für kreative Elemente aus RevJet
   * Es wurde eine Regel zur kreativen URL-Normalisierung für RevJet hinzugefügt, die von CRS und SSAI verwendet wird
   * TVSDK: Wenn Sie Anzeigen von RevJet bereitstellen oder bereitstellen möchten, müssen Normalisierungsregeln zu CRS Rules JSON hinzugefügt werden, um CRS mit ihren kreativen Elementen zu verwenden. Wenden Sie sich an Ihren technischen Kundenbetreuer, um Hilfe zu erhalten.
* CRS: Normalisierungsregel für Kreative aus Innovid
   * Es wurde eine Regel zur kreativen URL-Normalisierung für Innovid hinzugefügt, die von SSAI verwendet wird
   * Die von CRS verwendete Normalisierungsregel wurde in einer früheren Version hinzugefügt
   * TVSDK: Die Normalisierungsregel, die in das JSON für CRS-Regeln eingefügt werden soll, wurde nach einer früheren Version bereitgestellt. Um jedoch sicher zu sein, wenden Sie sich an Ihren technischen Kundenbetreuer, um alle vorhandenen Normalisierungsregeln zu überprüfen.
      >[!NOTE]
      >
      >Die meisten Innovid-Kreativ-URLs werden ohne die Normalisierungsregel erfolgreich transkodiert und geheftet. Gelegentlich werden jedoch auch innovide kreative URLs mit dynamischen Parametern gefunden. Die Normalisierungsregel ist erforderlich, um diese Instanzen zu bearbeiten.

### Version 19.5.2

**Wenn:** Mittwoch, 22. Mai 22:30 Uhr Ostzeit bis Mittwoch, 22. Mai 20:30 Uhr Ostzeit

* Unterstützung für CMAF (HLS/fMP4-Inhalt) hinzugefügt
   * SAI: Umgang mit CMAF-Manifesten
   * SAI: Initiieren von Transkodierungsanforderungen und Abrufen von CRS-Assets je nach Inhaltsformat (HLS/ts und HLS/fMP4)
   * CRS: Arbeitsablauf zum Neuverpacken von Anzeigen im CMAF-Format (HLS/fMP4) hinzugefügt
* SAI: Es wurde ein Problem behoben, das verhindert hat, dass ungemuxed Anzeigen in ungemusterten Inhalt eingefügt wurden, wenn sowohl der Inhalt als auch die Anzeige keine reinen Audiostreams haben (EXT-X-STREAM-INF)
* SAI: Unterstützung für CDN-Authentifizierungstoken für Limelight (LLNW) für Inhaltssegmente hinzugefügt
   * Wenn `pttoken=limelight` oder der Bootstrap-URL hinzugefügt `pttoken=llnw` wird, fügen wir beim Abrufen der Quell-Master-Playlist einen geheimen Header hinzu, dann hängen wir die Abfragen-Parameter aus dem X-Adobe-Sig-Header von LLNW an die Inhaltssegmente an
* SAI: Es wurde ein weiterer pttoken-Wert (`pttoken=centurylink`) für die Unterstützung von CenturyLink-CDN-Authentifizierungstoken hinzugefügt, der am 30. Juli 2018 veröffentlicht wurde
   * `pttoken=centurylink` hat das gleiche Verhalten wie `pttoken=level3`und beide Werte sind gültig

### Version 19.5.1

**Wenn:** Donnerstag, 9. Mai 20:30 UHR OSTZEIT bis Donnerstag, 9. Mai 4:30 UHR

* SAI: Sicherheitsaktualisierungen
* CRS-Dashboard: Kürzung der Zeichenfolge &quot;FqAdId-Beispiel&quot;auf 255 Zeichen aufgrund von Einschränkungen der Datenspeicherung von Daten (8 Bit)
   * Die Zeichenfolge &quot;FqAdId-Beispiel&quot;enthält das Anzeigensystem und die Anzeigen-ID jeder XML-Antwort in der Wrapper-Kette der Anzeige für Einfügungen aller CRS-Anzeigen mit SSAI (Abschnitt &quot;Kreative Statistiken&quot;des CRS-Dashboards)
* SSAI- und CRS-Dashboards: Softwareversionsaktualisierungen

### Version 19.4.1

**Wenn:** Mittwoch, 10. April 2010, 2:30 Uhr Ostzeit bis Mittwoch, 10.04.30 Uhr Ostzeit

* CRS: Die CRS-Umpackungs-API unterstützt keine HTTP-POST-Befehle mehr. Die CRS-Umverpackungs-API leitet HTTP-POST-Befehle (301) automatisch an HTTPS weiter
   * Ab dem 20. Mai wird die HTTP->HTTPS-Umleitung für HTTP POST-Befehle deaktiviert
   * Wenn Sie die CRS-Umpackungs-API verwenden, um Anzeigen im Voraus zu verpacken, wechseln Sie bis zum 20. Mai zu HTTPS für Ihre POST-Befehle
* CRS: Architektur und Arbeitsablauf zum Hochladen von CRS-Assets in die CDN-Herkünfte von Kunden neu gestaltet
   * Auftragsabläufe pro CDN-Herkunft sind voneinander getrennt. Daher wirken sich Upload-Engpässe für eine CDN-Herkunft nicht auf Uploads in andere CDN-Herkünfte aus
   * Weitere Vorteile: Die Verarbeitungszeiten für CRS-Aufträge und die Upload-Raten auf die CDN-Herkünfte der Kunden wurden verbessert.
* SAI: ClickThrough- und ClickTracking-URLs für Videoanzeigen wurden dem sidecar JSON v2-Format hinzugefügt
   * Eine neue JSON-Array-Eigenschaft, &quot;videoClicks&quot;, folgt der Eigenschaft &quot;trackingURLs&quot;
   * Die Wertnamen &quot;Ereignis&quot;lauten &quot;clickThrough&quot;und &quot;clickTracking&quot;, und sie haben keinen startTime-Wert
* SAI: Für CRS-Assets wurde eine Funktion hinzugefügt, mit der der Ablauf des Abfragedatensatzes eines CRS-Assets um 30 Tage verlängert werden kann, sobald es eingefügt wird
   * Vorheriges Verhalten: CRS-Asset-Nachschlagedatensätze werden in jedem Pod im memcache gespeichert. CRS-Asset-Lookup-Datensätze werden 30 Tage nach dem Hinzufügen zum memcache automatisch entfernt. Um den CRS-Asset-Nachschlagedatensatz eines kreativen Elements in einem Pod zu replizieren, nachdem er aus dem memcache entfernt wurde, muss dieses kreative Element in diesem Pod dreimal gefunden werden
   * Neues Verhalten: Wenn ein Pod auf einen CRS-Asset-Nachschlagedatensatz zugreift, um das CRS-Asset einzufügen, wird der Ablauf des CRS-Nachschlagedatensatzes in diesem Pod um 30 Tage verlängert. Daher werden häufig verwendete CRS-Elemente erst 30 Tage nach der letzten Verwendung aus dem Memcache eines Pods entfernt
   * Das neue Verhalten ist systemweit verfügbar und kann abgeschaltet werden, wenn ein Leistungsabfall erkannt wird
* SAI: Aktualisiertes Manifestbearbeitungsverhalten von WebVTT nur für Live-Streams
   * Vorheriges Verhalten: Entfernen Sie nur im WebVTT-Manifest EXT-X-DISCONTINUITY-Tags, die vor jeder eingefügten Anzeige und nach dem letzten Segment der eingefügten Werbeunterbrechung eingefügt werden.
   * Neues Verhalten: Der SSAI-Bootstrap-URL wurde ein neuer Parameter vttdisk mit den akzeptierten Werten true und false hinzugefügt
      * vttdisk=true: EXT-X-DISCONTINUITY-Tags werden vor jeder eingefügten Anzeige und nach dem letzten Segment der eingefügten Werbeunterbrechung in das WebVTT-Manifest eingefügt, wobei das Verhalten für Audio-/Video- und Nur-Audio-Manifeste übereinstimmt
      * vttdisk=false (siehe vorheriges Verhalten): Entfernen Sie nur im WebVTT-Manifest EXT-X-DISCONTINUITY-Tags, die vor jeder eingefügten Anzeige und nach dem letzten Segment der eingefügten Werbeunterbrechung eingefügt werden.
      * Wenn der vttdisk-Parameter ausgelassen wird oder einen anderen Wert als true/false hat, lautet der Standardwert vttdisk true (wahr)
* SAI: Sicherheitsaktualisierungen und Updates der Softwareversion
   * Java: Aktualisierung der Java-Version zur Unterstützung zusätzlicher ChiffrierSuites für Anzeigenaufrufe, die über TLS 1.2 (HTTPS) ausgelöst werden

### Version 19.2.1

**Wenn:** Mittwoch, 20. Februar 2019, 1:30 Uhr Ostzeit bis Mittwoch, 20. Februar 2019, 3:30 Uhr Ostzeit

* SAI: ClickThrough- und ClickTracking-URLs für Videoanzeigen wurden dem sidecar JSON v2-Format hinzugefügt
   * Unter der Eigenschaft &quot;trackingURLs&quot;lauten ihre &quot;Ereignis&quot;-Wertnamen &quot;Clickthrough&quot;und &quot;clickTracking&quot;
   * Ihre startTime-Werte sind der Anfang der Anzeige
* SAI: Für CRS-Assets wurde eine Funktion hinzugefügt, mit der der Ablauf des Abfragedatensatzes eines CRS-Assets um 30 Tage verlängert werden kann, sobald es eingefügt wird
   * Vorheriges Verhalten: CRS-Asset-Nachschlagedatensätze werden in jedem Pod im memcache gespeichert. CRS-Asset-Lookup-Datensätze werden 30 Tage nach dem Hinzufügen zum memcache automatisch entfernt. Um den CRS-Asset-Nachschlagedatensatz eines kreativen Elements in einem Pod zu replizieren, nachdem er aus dem memcache entfernt wurde, muss dieses kreative Element in diesem Pod dreimal gefunden werden
   * Neues Verhalten: Wenn ein Pod auf einen CRS-Asset-Nachschlagedatensatz zugreift, um das CRS-Asset einzufügen, wird der Ablauf des CRS-Nachschlagedatensatzes in diesem Pod um 30 Tage verlängert. Daher werden häufig verwendete CRS-Elemente erst 30 Tage nach der letzten Verwendung aus dem Memcache eines Pods entfernt
   * Das neue Verhalten ist systemweit verfügbar und kann abgeschaltet werden, wenn ein Leistungsabfall erkannt wird

* SAI: Updates der Softwareversion für NGINX und Kafka
   * NGINX und Kafka werden zum Auslösen von Anzeigen-Tracking-URLs serverseitig und zum Weiterleiten von Daten an die SSAI- und CRS-Dashboard verwendet
* CRS: Leistungsverbesserungen beim CRS-Dashboard

### Web UI-Version

**Wenn:** Mittwoch, 13. Februar, 4:00 Uhr - 4:30 Uhr Pazifik

**Was:** Komponente der Benutzeroberfläche für Primetime- und Entscheidungsfindung

* Korrektur des Problems mit der Kalender-Benutzeroberfläche, bei dem der Benutzer kein Datum über den 31. Dezember 2018 hinaus aus der Kalenderkomponente auswählen konnte, während eine Kampagne weitergeleitet oder ein Bericht abgerufen wurde.

### Version 19.1.2

**Wenn:** Mittwoch, 30. Januar 2019 1:30 Uhr Ostzeit bis Mittwoch, 30. Januar 30 Uhr Ostzeit

* SAI: Die Lookup-Key-Struktur, die SSAI zum Speichern und Abrufen von CRS-Assets verwendet, wurde aktualisiert, um Szenarios zu behandeln, in denen Anzeigenanbieter eine dynamische Anzeigen-ID oder eine Creative-ID für dieselbe Anzeige haben
   * Neue Lookup-Key-Struktur: Zone-, Creative URL- und Formatparameter (Zielgruppe, Ausgabeformat, Ziel-CDN)
   * Alte Lookup-Key-Struktur: Zonen-, Anzeigen- und Anzeigensystem-, Anzeigen-ID-, Kreativ-ID-, Kreativ-URL- und Formatparameter (Zielgruppe-Dauer, Ausgabeformat, Ziel-CDN)
   * Die Lookup-Keys für vorhandene CRS-Assets werden vor der Produktionsversion aktualisiert, um der neuen Struktur zu entsprechen. Beachten Sie jedoch, dass neue Assets, die zwischen der Lookup-Keys-Aktualisierung und der Produktionsversion transkodiert wurden, möglicherweise fehlen. In diesem Fall würden sie eine neue CRS-Anforderung starten, wenn sie nach der Veröffentlichung des Releases das nächste Mal auf sie stoßen

* CRS: Es wurde die Möglichkeit hinzugefügt, CRS-Anforderungen von bestimmten Anzeigensystemen, Anzeigen-IDs, kreativen IDs, kreativen URLs und/oder kreativen Formaten auf schwarze Liste/Whitelist zu setzen

   >Hinweis
   >
   >Adobe fügt Blacklist-Regeln hinzu, wenn Anzeigenanbieter mit dynamischen Werten (z. B. dynamischer Parameter in URL) für dieselbe Anzeige gefunden werden. Solche Blacklist-Regeln werden deaktiviert, nachdem die dynamische Komponente entweder vom Anbieter oder durch eine Normalisierungsregel aufgelöst wurde.

   * Wenn Sie eine Blacklist- oder Whitelist-Regel für Ihre Zone hinzufügen möchten, wenden Sie sich bitte an Ihren technischen Kundenbetreuer.

### Version 19.1.1

**Wenn:** Mittwoch, 9. Januar 2019 1:30 Uhr Ostzeit bis Mittwoch, 9. Januar 3:30 Uhr Ostzeit

* Es wurde ein Problem behoben, bei dem eine fehlerhafte Interpretation von HTTP-Headern, die am Leben erhalten bleiben, zu einem Fehler führen kann, wenn eingehende kreative Elemente validiert werden, die auf total-stream.net gehostet werden.
* Es wurde ein Problem behoben, bei dem einzelne Anführungszeichen (&#39;) und Anführungszeichen (&quot;) in der Anzeigen-ID, der Creative-ID und anderen Feldern für eine Umverpackungsanfrage dazu führten, dass die Anforderung zum Umpacken fehlschlug.
* Wird auf Java long (Datentyp) umgestellt, um ein Problem zu beheben, bei dem das Erreichen der Java-int-Grenze von 2.147.483.647 bei der Transkodierung von Auftrags-ID-Werten dazu führen würde, dass alle Reverpackungsanforderungen fehlschlagen.
* Datenbankoptimierungen.

## Behobene Probleme

Wenn die Lösung mit einem gemeldeten Problem verbunden ist, wird ein Zendesk-Verweis angezeigt. Beispiel: ZD#xxxxx.

**PTAI 19.7.1**

ZD#37503 - JSON-Antworten für die CRS-Regeln werden zwischengespeichert, um die Duplikat-Anforderungen zu vermeiden.

## Bekannte Probleme und Einschränkungen

**PTAI 19.7.1**

Keine neue Einschränkung hinzugefügt.
