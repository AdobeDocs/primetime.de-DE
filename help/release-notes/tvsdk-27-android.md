---
title: TVSDK 2.7 für Android-Versionshinweise
description: TVSDK 2.7 für Android - Versionshinweise beschreiben, was neu ist oder geändert wurde, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 2.7
products: SG_PRIMETIME
topic-tags: release-notes
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '4095'
ht-degree: 0%

---


# TVSDK 2.7 für Android-Versionshinweise {#tvsdk-for-android-release-notes}

TVSDK 2.7 für Android - Versionshinweise beschreiben, was neu ist oder geändert wurde, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 2.7

## TVSDK Android 2.7 {#tvsdk-android}

Der Android-Referenzplayer ist im Verzeichnis samples/ Ihrer Distribution im Lieferumfang von Android TVSDK enthalten. In der zugehörigen Datei README&lt;.md wird beschrieben, wie Sie den Referenz-Player erstellen.

>[!NOTE]
>
>Um den Referenz-Player erfolgreich zu erstellen, wie in README.md beschrieben, das mit der Version verteilt wird, führen Sie folgende Schritte durch:
>
>1. VideoHeartbeat.jar von [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) herunterladen (VideoHeartbeat-Bibliothek für Android v2.0.0)
>1. Extrahieren Sie VideoHeartbeat.jar in den Ordner libs/.

>



## Neue Funktionen {#new-features}

TVSDK 2.7 für Android enthält alle Funktionen von Version 1.4 mit Ausnahme der nicht unterstützten Funktionen, die unter [Funktionsmatrix](#feature-matrix) aufgeführt sind.

**Android TVSDK 2.7**

* **Unterstützung der parallelen Anzeigenauflösung**

TVSDK 2.7 unterstützt die gleichzeitige Auflösung aller Anzeigenanforderungen in einer Werbeunterbrechung anstelle einer sequenziellen Auflösung.

### Neue Funktionen in früheren Versionen {#new-features-previous-releases}

**Version 2.5.6**

* **TVSDK 2.5 unterstützt Android P**
* **Hintergrundaudio aktivieren**

   Um die Audiowiedergabe zu aktivieren, wenn die App von vorne in den Hintergrund wechselt, sollte die App die enableAudioPlaybackInBackground-API des MediaPlayer mit dem Argument &quot;true&quot;aufrufen, wenn sich der Player im Status &quot;VORBEREITT&quot;befindet.

* **alwaysUseAudioOutputLatency(boolean val) in der MediaPlayer-Klasse**

Verwenden Sie bei Festlegung die Ausgabedatenz in der Berechnung des Audio-Zeitstempels.
Boolesche Parameter val - True verwendet die Latenz der Audioausgabe bei der Berechnung des Audiozeitstempels.

* **Optimiert, um die beste Wiedergabe zu erzielen, selbst wenn die Bandbreite plötzlich abfällt.**
TVSDK bricht jetzt bei Bedarf den Download des aktuellen Segments ab und wechselt dynamisch zur entsprechenden Darstellung. Dies geschieht durch einen nahtlosen Wechsel zwischen den Bitraten ohne Unterbrechungen.

**Version 2.5.5**

* **Einfügen einer partiellen Werbeunterbrechung**

   TV-ähnliche Erfahrung, in der Mitte einer Anzeige zu erscheinen, ohne die Verfolgung der teilweise überwachten Anzeige auszulösen.\
   Beispiel**: **Benutzer schließt sich einer 90-Sekunden-Werbeunterbrechung mit drei 30-Sekunden-Anzeigen in der Mitte (40 Sekunden) an. Dies ist 10 Sekunden nach der zweiten Anzeige in der Pause.
   * Die zweite Anzeige wird während der verbleibenden Dauer (20 Sekunden) und die dritte Anzeige abgespielt.
   * Anzeigentracker für die teilweise wiedergegebene Anzeige (zweite Anzeige) werden nicht ausgelöst. Die Tracker für nur die dritte Anzeige werden ausgelöst.

* **Sicheres Laden der Anzeige über HTTPS**

   Adobe Primetime bietet eine Option zum Anfordern des ersten Aufrufs an den Primetime-Anzeigenserver und CRS über HTTPS.

* **Zu CRS-Anforderungen hinzugefügte AdSystem- und Creative-ID**

   * Jetzt einschließlich &#39;AdSystem&#39; und &#39;CreativeId&#39; als neue Parameter in den Anforderungen 1401 und 1403.

* **Die API setEncodeUrlForTracking in der NetworkConfiguration-Klasse** entfernt die unsicheren Zeichen in einer URL, die kodiert werden sollen.

**Version 2.5.4**

Android TVSDK v2.5.4 Angebote mit den folgenden Aktualisierungen und API-Änderungen:

* Änderungen am Standardwert für WebViewDebbuging
Der Wert von WebViewDebbuging ist standardmäßig auf False eingestellt. Rufen Sie dazu setWebContentsDebuggingEnabled(true) in der Anwendung auf.
* Aktualisierung der OpenSSL- und Curl-Version
Aktualisierung von libcurl auf v7.57.0 und OpenSSL auf v1.0.2k.
* Zugriff auf App-Ebene für VAST-Antwortobjekt
Es wurde eine neue API NetworkAdInfo::getVastXml() eingeführt, die Zugriff auf das VAST-Antwortobjekt der Anwendung ermöglicht.

**Version 2.5.3**

Android TVSDK v2.5.3 Angebot die folgenden Updates und API-Änderungen.

* Alle TVSDK-Kunden, die CRS verwenden, sollten ihre Apps mit TVSDK 2.5.3.85 oder höher auf Android aktualisieren. Dies ist eine Ablage, die die vorhandene App-Implementierung ersetzt. Überprüfen Sie nach dem TVSDK-Upgrade die kreativen URL-Anforderungen von CRS in einem Proxy-Tool (z. B.: Charles) und bestätigen Sie, dass der Hostname und die Version im Pfad sich wie in der Beispiel-URL-Struktur unten widerspiegeln.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* Benutzeragent von TVSDK anpassbar: haben wir einige neue APIs hinzugefügt, um die Benutzeragenten anzupassen.

   * setCustomUserAgent(String-Wert)
   * getCustomUserAgent()

* Freigeben von Cookies zwischen Android-Anwendung und TVSDK: Android TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der JAVA-Ebene (gespeichert im CookieStore der Android-Anwendung) und der C++ TVSDK-Ebene. Jetzt ist es möglich, Cookies in der nativen C++-Ebene einzustellen und/oder zu ändern, da sie dem Java Cookie Store ausgesetzt werden.
* API-Änderungen:

   * Ein neues Ereignis CookiesUpdatedEvent wird hinzugefügt. Er wird vom Medienplayer ausgelöst, wenn sein Cookie aktualisiert wird.
   * Eine neue API wird zu NetworkConfiguration::set/ getCustomUserAgent() hinzugefügt, um einen benutzerdefinierten Benutzeragent zu verwenden.
   * Eine neue API wird zu NetworkConfiguration::set/ getEncodedUrlForTracking hinzugefügt, um die Kodierung von unsicheren Zeichen zu erzwingen.
   * Eine neue API wird zu NetworkConfiguration::getNetworkDownVerificationUrl() hinzugefügt, um im Falle eines Failover eine URL für die Netzwerküberprüfung festzulegen.
   * Eine neue Eigenschaft wird TextFormat::handleSpaceAsAlphaNum hinzugefügt, die definiert, ob Leerzeichen bei der Anzeige von Beschriftungen als alphanumerisch behandelt werden sollen.

* Änderungen in SizeAvailableEvent: Zuvor gaben die Methoden getHeight() und getWidth() von SizeAvailableEvent in 2.5.2 die Frame-Höhe und die Frame-Breite zurück, die vom Medienformat zurückgegeben wurden. Jetzt gibt es Ausgabehöhe und -breite zurück, die vom Decoder zurückgegeben werden.
* Änderungen im Pufferverhalten: Das Pufferverhalten wird geändert. Es bleibt dem App-Entwickler überlassen, was er tun möchte, wenn der Puffer leer ist. 2.5.3 verwendet die Wiedergabepuffergröße bei einer leeren Puffersituation.

**Version 2.5.2**

Android TVSDK v2.5.2 Angebot wichtige Fehlerbehebungen und einige API-Änderungen.

**Version 2.5.1**

Die wichtigen neuen Funktionen, die in Android 2.5.1 veröffentlicht wurden.

* **Leistungsverbesserungen** Die neue TVSDK 2.5.1 Architektur bietet eine Reihe von Leistungsverbesserungen. Basierend auf Statistiken aus einer Drittanbieter-Benchmarking-Studie bietet die neue Architektur eine 5fache Reduzierung der Startzeit und 3,8fache Reduzierung der Dropdown-Rahmen im Vergleich zum Branchendurchschnitt:

   * **Sofort für VOD und live -** Wenn Sie Sofort aktivieren, initialisiert und puffert das TVSDK Medien vor dem Beginn der Wiedergabe. Da Sie mehrere MediaPlayerItemLoader-Instanzen gleichzeitig im Hintergrund starten können, können Sie mehrere Streams puffern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird die Wiedergabe sofort auf den Beginn des neuen Kanals wiedergegeben. TVSDK 2.5.1 unterstützt auch den Instant On für **live**-Streams. Die Live-Streams werden erneut gepuffert, wenn das Live-Fenster verschoben wird.

      * **Verbesserte ABR-Logik -** Die neue ABR-Logik basiert auf der Pufferlänge, der Änderungsrate der Pufferlänge und der gemessenen Bandbreite. Dadurch wird sichergestellt, dass die ABR die richtige Bitrate wählt, wenn die Bandbreite schwankt, und auch die Anzahl der auftretenden Bitratenwechsel optimiert wird, indem die Rate überwacht wird, mit der sich die Pufferlänge ändert.
      * **Teilweiser Segmentdownload/Untersegmentierung -** TVSDK verringert die Größe der einzelnen Fragmente weiter, um so schnell wie möglich Beginn abspielen zu können. Das zugehörige Fragment muss alle zwei Sekunden über einen Schlüsselrahmen verfügen.
      * **Verzögerte Anzeigenauflösung -** TVSDK wartet nicht auf die Auflösung von Nicht-Preroll-Anzeigen, bevor die Wiedergabe gestartet wird, wodurch die Startzeit verringert wird. APIs wie Suchen und Trick-play sind immer noch nicht zulässig, bis alle Anzeigen aufgelöst sind. Dies gilt für VOD-Streams, die mit CSAI verwendet werden. Vorgänge wie Suchen und Vorwärts sind erst nach Abschluss der Anzeigenauflösung zulässig. Bei Live-Streams kann diese Funktion nicht für die Anzeigenauflösung während eines Live-Ereignisses aktiviert werden.
      * **Persistente Netzwerkverbindungen -** Diese Funktion ermöglicht es TVSDK, eine interne Liste persistenter Netzwerkverbindungen zu erstellen und zu speichern. Diese Verbindungen werden für mehrere Anforderungen wiederverwendet, anstatt für jede Netzwerkanforderung eine neue Verbindung zu öffnen und anschließend zu zerstören. Dadurch wird die Effizienz erhöht und die Latenz im Netzwerkcode verringert, was zu einer schnelleren Wiedergabe führt.
Wenn TVSDK eine Verbindung öffnet, fordert es den Server auf, eine *Keep-Alive* Verbindung herzustellen. Einige Server unterstützen diese Art der Verbindung möglicherweise nicht. In diesem Fall greift TVSDK zurück, um für jede Anforderung erneut eine Verbindung herzustellen. Auch wenn persistente Verbindungen standardmäßig aktiviert sind, verfügt TVSDK jetzt über eine Konfigurationsoption, damit Apps persistente Verbindungen bei Bedarf deaktivieren können.
      * **Paralleles Herunterladen - Das parallele** Herunterladen von Video und Audio anstelle von Serien reduziert Startverzögerungen. Diese Funktion ermöglicht die Wiedergabe von HLS Live- und VOD-Dateien, optimiert die verfügbare Bandbreitennutzung von einem Server, verringert die Wahrscheinlichkeit, in Puffersituationen zu gelangen, und minimiert die Verzögerung zwischen Download und Wiedergabe.
      * **Parallele Anzeigendownloads -** TVSDK lädt parallel zur Inhaltswiedergabe Anzeigen ein, bevor die Werbeunterbrechungen erreicht werden, wodurch eine nahtlose Wiedergabe von Anzeigen und Inhalten ermöglicht wird.

* **Wiedergabe**

   * **MP4 Content Play-back -** MP4-Kurzclips müssen nicht neu transkodiert werden, um innerhalb von TVSDK wiedergegeben zu werden.
Hinweis: ABR-Switching, Trick Play, Anzeigeneinfügung, späte Audiobindung und Untersegmentierung werden für die MP4-Wiedergabe nicht unterstützt.
   * **Trick play with adaptive bit rate (ABR) -** Diese Funktion ermöglicht es TVSDK, zwischen iFrame-Streams zu wechseln, während sie im Trick Play-Modus arbeiten. Sie können Profil ohne iFrame verwenden, um Tricks mit geringeren Geschwindigkeiten auszuführen.
   * **Glättere Trick-Wiedergabe -** Diese Verbesserungen verbessern die Benutzerfreundlichkeit:

          * Adaptive Bitrate- und Framerate-Auswahl während der Trick-Wiedergabe, basierend auf Bandbreite und Puffer-Profil
          * Verwendung des Hauptstreams anstelle des IDR-Streams, um eine schnelle Wiedergabe mit bis zu 30 fps zu erzielen.
      
* **Inhaltsschutz**

   * **Auflösungsbasierter Ausgabeschutz -** Diese Funktion verknüpft Wiedergabebeschränkungen mit bestimmten Auflösungen und bietet feinere DRM-Steuerelemente.

* **Workflow-Unterstützung**

   * **Integration der direkten Rechnungsstellung:** Hiermit werden Rechnungsmetriken an das Adobe Analytics-Backend gesendet, das von Adobe Primetime für vom Kunden verwendete Streams zertifiziert wurde.
TVSDK sammelt automatisch Metriken, wobei der Kaufvertrag des Kunden eingehalten wird, um regelmäßige Nutzungsberichte zu erstellen, die für die Abrechnung erforderlich sind. Auf jedem Stream-Beginn-Ereignis verwendet TVSDK die Adobe Analytics-Dateneinfüge-API, um Abrechnungsmetriken wie Inhaltstyp, durch Anzeigeneinfügung aktivierte Flags und DRM-aktivierte Flags - je nach Dauer des abrechnungsfähigen Streams - an die eigene Report Suite von Adobe Analytics Primetime zu senden. Dies beeinträchtigt oder wird nicht in die eigenen Adobe Analytics Report Suites oder Server-Aufrufe des Kunden aufgenommen. Auf Anfrage wird dieser Bericht zur Rechnungsnutzung regelmäßig an Kunden gesendet. Dies ist die erste Phase der Abrechnungsfunktion, die nur die Nutzungsabrechnung unterstützt. Sie kann mithilfe der in der Dokumentation beschriebenen APIs auf Grundlage des Kaufvertrags konfiguriert werden. Diese Funktion ist standardmäßig aktiviert. Um diese Funktion zu deaktivieren, lesen Sie das Referenz-Player-Beispiel.
   * **Verbesserte Failover-Unterstützung -** Zusätzliche Strategien wurden implementiert, um die unterbrechungsfreie Wiedergabe fortzusetzen, obwohl Host-Server, Wiedergabelistendateien und Segmente ausfallen.

* **Werbung**

   * **Moat-Integration -** Unterstützung für die Messung der Anzeigensichtbarkeit von Moat.
   * **Begleitbanner -** Begleitbanner werden neben einer linearen Anzeige angezeigt und werden oft auch nach dem Ende der Anzeige auf der Ansicht angezeigt. Diese Banner können vom Typ &quot;html&quot;(ein HTML-Snippet) oder &quot;iframe&quot;(eine URL zu einer iframe-Seite) sein.

* **Analytics**

   * **VHL 2.0 -** Dies ist die neueste optimierte VHL-Integration (Video Heartbeats Library) für die automatische Erfassung von Nutzungsdaten für Adobe Analytics. Die Komplexität der APIs wurde verringert, um die Implementierung zu erleichtern. Laden Sie die VHL-Bibliothek [v2.0.0 für Android](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) herunter und extrahieren Sie die JAR-Datei im Ordner libs.

* **SizeAvaliableEventListener**
   * getHeight()- und getWidth()-Methoden von SizeAvailableEvent geben nun die Ausgabe in Höhe bzw. Breite zurück. Das Anzeigeseitenverhältnis kann wie folgt berechnet werden:

      ```
      SizeAvailableEvent e;
      
      DAR = e.getWidth()/ e.getHeight();
      
      Storage Aspect Ratio in terms of Sar width and Sar height can also be used to calculate Frame width and Frame height:
      
      SAR = e.getSarWidth()/e.getSarHeight();
      
      frameHeight = e.getHeight();
      
      frameWidth = e.getWidth()/SAR;    
      ```

* **Cookies**

   * Android TVSDK unterstützt jetzt den Zugriff auf JAVA-Cookies, die im CookieStore der Android-Anwendung gespeichert sind. Eine Callback-API (onCookiesUpdated) wird bereitgestellt, um zu protokollieren, wann immer ein neues Cookie als Teil des Antwortheaders &quot;Set-Cookie&quot;eingeht. Diese Cookies stehen als Liste von HttpCookie(s) zur Verfügung, die für eine andere URI/Domäne verwendet werden, indem diese Cookie-Werte mithilfe von CookieStore für diese bestimmte URI/Domäne festgelegt werden. Gleichermaßen werden die Cookie-Werte in TVSDK mithilfe der CookieStore Add-API aktualisiert.

## Funktionsmatrix {#feature-matrix}

TVSDK für Android unterstützt eine Reihe von Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.

In den unten stehenden Funktionstabellen gibt ein &quot;Y&quot;an, dass die Funktion in der aktuellen Version unterstützt wird.

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | VOD + Live | Y |
| FER - Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | FER VOD | Y |
| Suchen, wann eine Anzeige abgespielt wird | VOD + Live | Nicht unterstützt |
| AC3 | VOD + Live | Nicht unterstützt |
| MP3 | VOD | Nicht unterstützt |
| MP4-Inhaltswiedergabe | VOD | Y |
| Adaptive Bit Rate Switching Logic | VOD + Live | Y |
| Wiedergabe nur Audio | VOD + Live | Y |
| Multi-CDN-Unterstützung | VOD + Live | Nicht unterstützt |
| Wiedergabe von Anzeigen mit reinen Audiomedien | VOD + Live | Nicht unterstützt |
| Untertitel - 608/708 | VOD + Live | Y |
| Untertitel - WebVTT | VOD + Live | Y |
| Manifest-Failover | VOD + Live | Y |
| Erweiterte Failover | VOD + Live | Y |
| Servicequalitäts- und Player-Benachrichtigungen | VOD + Live | Y |
| Unterstützung für Cookie-Kopfzeilen | VOD + Live | Y |
| Unterstützung für benutzerdefinierte HTTP-Kopfzeilen | VOD + Live | Y (Aufnahme zulassen erforderlich) |
| Puffersteuerungsparameter festlegen | VOD + Live | Y |
| Festlegen der Steuerelemente für adaptive Bitraten | VOD + Live | Y |
| Benutzerdefinierte Manifest-Tags | VOD + Live | Y |
| Verspätete Audiobindung | VOD + Live | Y |
| 302 Umleitung | VOD + Live | Y |
| Wiedergabe mit Versatz | VOD + Live | Y |
| Wiedergabe nur Audio | VOD + Live | Y |
| Trick Play | VOD + Live | Y |
| Langsame Bewegung bei Trick Play | VOD + Live | Nicht unterstützt |
| Glattes Trick Play (mit ABR) | VOD + Live | Y |
| ID3-Analyse | VOD + Live | Y |
| Werbeunterbrechung | VOD + Live | Nicht unterstützt |
| Sofort ein | VOD + Live | Nicht unterstützt |
| Unterstützung von Diskontinuitätsmarken | VOD + Live | Y |
| 302 Umleitungs-Stickiness | VOD + Live | Y |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Allgemeine Wiedergabe, Anzeige aktiviert | VOD + Live | Y |
| FER-Inhalt mit aktivierten Anzeigen | VOD | Y |
| Standardverhalten von Werbeanzeigen | VOD + Live | Y |
| VAST 2.0/3.0 | VOD + Live | Y |
| VMAP 1.0 | VOD + Live | Y |
| MP4-Anzeigen | VOD + Live | Y (aus CRS) |
| Trick Play mit aktivierten Anzeigen | VOD + Live | Y |
| Nur Anzeige | VOD | Y |
| Targeting-Parameter | VOD + Live | Y |
| Benutzerdefinierte Parameter | VOD + Live | Y |
| Benutzerdefiniertes Anzeigenverhalten | VOD + Live | Y |
| Benutzerdefinierte Anzeigen-Tags | Live | Y |
| Benutzerdefinierte Anzeigenauflösungen | VOD + Live | Y |
| Freirad benutzerdefinierter Anzeigenauflösung | VOD | Y |
| C3 | VOD + Live | Nicht unterstützt |
| Verzögerte Anzeigenauflösung | VOD | Y |
| Unterstützung von Diskontinuitätsmarken - SSAI | VOD + Live | Y |
| Ergänzende Anzeigen, Banneranzeigen und anklickbare Anzeigen | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y (JS) |
| Vorzeitiger Anzeigenausstieg | Live | Y |
| Regelbasierte kreative Priorisierung | VOD + Live | Y |
| CRS-Regeln | VOD + Live | Y |
| JSON Ad Resolver | VOD + Live | Nicht unterstützt |
| Mottenintegration | VOD + Live | Y |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| AES-Verschlüsselung | VOD + Live | Y |
| Beispiel-AES-Verschlüsselung | VOD + Live | Y |
| Tokenisierte Streams | VOD + Live | Y |
| DRM | VOD + Live | Nur Primetime-DRM (Zukunft: Widevine) |
| Externe Wiedergabe (RBOP) | VOD + Live | Nur Primetime-DRM |
| Lizenzdrehung | VOD + Live | Nur Primetime-DRM |
| Schlüsseldrehung | VOD + Live | Nur Primetime-DRM |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Adobe Analytics VHL-Integration | VOD + Live | Y |
| Rechnungsstellung | VOD + Live | Y |

## Behobene Probleme {#resolved-issues}

Wenn die Auflösung mit einem gemeldeten Problem verbunden ist, wird ein Zendesk-Verweis angezeigt, z. B. ZD#xxxxx

**Android TVSDK 2.7**

Dieser Abschnitt enthält eine Zusammenfassung des Problems, das in der Version TVSDK 2.7 behoben wurde.

* ZD#37166 - Ein Fehler-Tracking-Aufruf wird ausgelöst, auch wenn die Anzeige korrekt wiedergegeben wird.
* ZD#37134 - Falsche Anzeigen-IDs werden zurückgegeben, falls Wrapper(3P) Eine Anzeige mit mehreren Anzeigen in der VMAP-Antwort vorhanden ist.

**Android TVSDK 2.5.6**

* ZD #34992 - Die Sprache ist in &quot;Untertitel&quot;leer.
   * Es wurde ein Fall behoben, bei dem TVSDK #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS vom Hauptmanifest nicht analysiert hat, um die Details der Untertitel-Verfolgung abzurufen.
* ZD #35078 - Android P-Überprüfung.
   * TVSDK 2.5.6 wurde mit den neuesten Android P Beta-Builds validiert. Aufgrund des neuen Android-Betriebssystems wurden keine Probleme gefunden.
* ZD #34149 - Player fordert weiterhin Manifeste an, auch wenn ein Fehler aufgetreten ist.
   * Korrektur des Problems, bei dem TVSDK wiederholende Aufrufe tätigte, selbst wenn alle Profil ausfielen (404-Fehler).
* ZD #31533 - Audiowiedergabe auf Android, nachdem die App in den Hintergrund gesendet wurde.
   * Es wurde die API `enableAudioPlaybackInBackground` von MediaPlayer hinzugefügt, die mit &quot;True&quot;als Argument aufgerufen werden sollte (wenn der Player im Status &quot;PREPARED&quot;ist), um die Wiedergabe von Audio zu aktivieren, wenn die App im Hintergrund ausgeführt wird.

**Android TVSDK 2.5.5**

* ZD #21647 - Android TVSDK benachrichtigt 640 x 368, wenn die tatsächliche Videogröße 640 x 360 beträgt.
   * Aufgrund der Variablen m_nOutputHeight (innerhalb von AndroidMCVideoDecoder) wird eine Aktualisierung mit der Rahmenhöhe anstelle der tatsächlichen Ausgabehöhe vorgenommen. Es wurden relevante Änderungen an der Funktion getVideoFrame vorgenommen, um m_nOutputHeight korrekt zu berechnen.
* ZD #26614 - Urgent - Drittanbieter-Ad-Serving / Programmatic - Misserfolgen von Impressionen.
   * Die frühere Korrektur wurde verbessert, indem die Groß-/Kleinschreibung bei der XML-Analyse behandelt wurde, bei der das Problem reproduzierbar war, wenn &quot;space&quot;vor dem Gleichheitszeichen wie &lt;VAST-Version =&quot;2.0&quot;> liegt
* ZD #29296 - Android: hinzufügen von AdSystem- und Creative-ID für CRS-Anforderungen.
   * Jetzt einschließlich &#39;AdSystem&#39; und &#39;CreativeId&#39; als neue Parameter in den Anforderungen 1401 und 1403.
* ZD #33062 - TVSDK stürzt beim Auftreten von Pipe-Zeichen in VAST-Antwort unter CDATA-Knoten ab
   * API setEncodeUrlForTracking in der NetworkConfiguration-Klasse wurde als unsichere Zeichen in einer zu kodierenden URL entfernt.
* ZD #33063 - CRS Dateiauswahllogik beschädigt - TVSDK sendete keine CRS-Anforderung für Webm-Format, sondern schickte sie stattdessen für 3gpp-Dateien.
   * Die Logik wurde jetzt behoben. Bei der Verwendung von Mediendateien mit Webm und 3gpp-Format wird eine CRS-Anforderung für Webm gesendet. Bei Verwendung beider Mediendateien im 3gpp-Format muss die CRS-Anforderung für die höchste Bitrate-3-gpp-Datei gesendet werden.
* ZD #33125 - Die Android-App stürzt mit einem bestimmten DoubleClick-Tag innerhalb des VMAP ab.
   * Korrektur des Szenarios zur Vermeidung des Absturzes.
* ZD #32256 - Problem mit Lizenzdrehung und Schlüsseldrehung - Adobe Access.
   * Die Segmentinitialisierung mit den DRM-Metadaten für SampleAES-Inhalte wurde korrigiert. Funktioniert einwandfrei mit AES128-Inhalten.
* ZD #33619 - Schnelles Weiterleiten eines wachsenden Playlist-Inhalts, der im Pufferzustand nahe dem Live Point feststeckt.
   * Handle des Gehäuses beim Überqueren des Live-Points im Trick Play-Modus.
* ZD #34151 - TimedMetadata-Objekte nicht in der Reihenfolge.
   * Zwei TimedMetadata-Ereignis wurden in zufälliger Reihenfolge angezeigt, wenn sie zur selben Zeit in der Zeitleiste gehörten. Ihre ursprüngliche Reihenfolge wurde manifest beibehalten.
* ZD #34189 - Problem beim Suchen nach Beginn der Werbeunterbrechung.
   * Das Problem betraf SSAI-Anzeigen, die mit Diskontinuität verbunden werden. Und die Ursache war ein Verhalten, wenn wir versuchen, solche Anzeigen zu beginnen, suchen wir nach einem Keyframe und wir finden es nicht. Der Grund dafür war, dass der Mindest-Audio-Zeitstempel der Anzeige vor dem Mindest-Video-Zeitstempel lag. Daher suchen wir am Ende nach einem Schlüsselbild mit falschen fragmentDump-Daten. Jetzt behoben.
* ZD #34528 - Videoauflösung, die auf einem 3rd-gen-Dongle von FireTV nicht über 640 x 360 aktualisiert wird.
   * Die Fehlerbehebung wurde verbessert und enthält nun die neuesten Firmware-Updates.
* ZD #34793 - TVSDK 2.5.x führte in einigen Fällen zu Abstürzen mit benutzerdefiniertem Content-Auflöser, wenn VideoEngine davon ausging, dass die auditudeSettings verfügbar sind und nicht.
   * Der Absturz ereignete sich aufgrund eines Funktionsaufrufs an einem Null-freigegebenen Zeiger (auditudeSettings). Es wurde eine bedingte Prüfung in VideoEngineTimeline::placeToSourceTimeline() hinzugefügt, um sicherzustellen, dass auditudeSettings verfügbar sind, bevor irgendetwas für dieses Objekt aufgerufen wird.
* ZD #32584 - Kein Zugriff auf vollständige Informationen im Knoten &lt;Erweiterungen> einer VAST-Antwort möglich.
   * Korrektur des Problems mit der XML-Analyse, und nun stellt NetworkAdInfo die vollständigen Informationen bereit, die im Knoten &lt;Erweiterungen> vorhanden sind.
* ZD #35086 - Bei bestimmten VMAP-Antworten werden keine vollständigen Erweiterungsdaten vom Player abgerufen.
   * Das Problem war spezifisch für die Erweiterung XML, da die XML-Analyse nicht funktionierte, wenn die Erweiterung XML Dubletten-Anführungszeichen im Attributwert enthielt. Korrektur des Problems.

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Wiedergabesitzung zur Aktivierung des Remotedebuggens von Webansicht.
   * WebViewDebbuging ist standardmäßig auf False eingestellt. Um das Debugging zu aktivieren, legen Sie mithilfe von setWebContentsDebuggingEnabled(true) als true über die Anwendung fest.
* ZenDesk#33011 - Die Anzeigenzeitschiene wird nicht aufgelöst, wenn eine CRS-Anforderung fehlschlägt.
   * Wenn eine CRS-Anforderung an eine Anzeige fehlschlägt, wird die Zeitschiene gelöst und die verbleibenden Anzeigen werden wiedergegeben.
* ZenDesk#34528 - Die Videoauflösung wird auf einem Dongle der dritten Generation von FireTV nicht über 640 x 360 aktualisiert.
   * Die Videoauflösung schaltet sich als Bitratenwechsel nach oben.
* ZenDesk#33192 - AudioTrack hat einen Null-Namen, wenn die Spur über AudioUpdatedEventListener::onAudioUpdated abgerufen wird.
   * In einigen Szenarien beim FireTV-Stick wurde onAudioUpdate-Ereignis ausgelöst, wenn es kein aktuelles Audio-Update gab. Das wurde jetzt behoben.

**Android TVSDK 2.5.3**

* Zendesk#32216 - Benutzerdefiniertes TimedMetadata-Tag-Abonnement funktioniert nicht.
   * Wir geben ID3-Daten als Byte-Array (zur Unterstützung von APIC- oder generischen Daten) an den Client zurück, während in 1.4 die Rückgabestaste angegeben ist. Das Byte-Array behandelt kein mit null beendetes Zeichen selbst, daher zeigte es dem Client Sonderzeichen an. Dieses Problem wurde jetzt behoben.
* Zendesk#32670 - Player, der nicht zu Redundant Playlist überspringt
   * Dies funktioniert jetzt einwandfrei und setNetworkDownVerificationUrl funktioniert erwartungsgemäß.
* Zendesk#32369 - Die Bildunterschrift weist einen anderen Farbabfall oder ein anderes Artefakt auf.
   * Problem mit CC-Fehlern wurde im letzten Build behoben
* Zendesk#25590 - Verbesserung: TVSDK-Cookie-Store (C++ bis JAVA)
   * Android TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der JAVA-Ebene (gespeichert im CookieStore der Android-Anwendung) und der C++ TVSDK-Ebene.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 hat offenbar keine Fehlerbehebung für PTPLAY-20269
Dieses Problem wurde behoben und in den Zweig 2.5.2 integriert.
* Zendesk#31806 - Auditude sticks bei der Vorbereitung
Player war im Vorbereitungszustand hängen geblieben, da response xml ein leeres Tag enthielt. Das Problem wurde nun behoben.
* Zendesk#31727 - TVSDK 2.5 Untertitel werden abgelegt oder falsch geschrieben.
   * Das Problem wurde behoben, und es werden keine Zeichen abgelegt/falsch geschrieben.
* Zendesk#31485 - DrmManager in 2.5
   * Es ist ein Problem beim Erstellen von DRMManager über den neuen DRMManager(Kontext) aufgetreten. Die DRMService-Klasse wurde implementiert, die DRMManager bereitstellen würde.
* Zendesk#32794- 1080P-Auflösungsstream wird unter Android nicht abgespielt.
   * Die Methoden SizeAvailableEvent und Previous, getHeight() und getWidth() von SizeAvailableEvent in 2.5 wurden geändert, um Frame-Höhe und Frame-Breite zurückzugeben, die vom Medienformat zurückgegeben wurden. Es gibt nun Ausgabehöhe und -breite zurück, die vom Decoder zurückgegeben werden.
* Zendesk #19359 Flash Player stürzt aufgrund der Position des Attributs #EXT-X-FAXS-CM im Set-Level-Manifest ab.
   * Das Tag #EXT-X-FAXS-CM muss immer in der oberen Wiedergabeliste angezeigt werden, bevor einzelne Bitraten oder Segmente in der Wiedergabeliste angezeigt werden.

**Android TVSDK 2.5.2**

* Zendesk#17305 Artefakte in geschlossenen Bildunterschriften mit undurchsichtigem Hintergrund.
setTreatSpaceAsAlphaNum-Eigenschaft in TextFormat verfügbar ist. Standardmäßig ist die Eigenschaft false. Legen Sie die Eigenschaft in einem Client auf &quot;True&quot;fest, um das Problem mit dem dunklen Bereich zu beheben.

* Zendesk#25097 CC-Anzeige hat visuelle Artefakte mit CC-Einstellungen.
setTreatSpaceAsAlphaNum-Eigenschaft in TextFormat verfügbar ist. Standardmäßig ist die Eigenschaft false. Legen Sie die Eigenschaft in einem Client auf &quot;True&quot;fest, um das Problem mit dem dunklen Bereich zu beheben.

* Zendesk #31620 Die Benutzeragenten-Zeichenfolge, die aus dem TVSDK-Player entfernt wird, wird abgeschnitten.
Die Benutzeragenten-Zeichenfolge wird nach 128 Zeichen nicht mehr abgeschnitten.
Der Adobe Primetime-Versionszeichenfolge wird dem Systembenutzer-Agent hinzugefügt.

* Zendesk #30809 Fehlendes SEEK_END-Ereignis verhindert, dass die App zu einem Wiedergabestatus wechselt.
* Zendesk #30415 Die &quot;Cyan&quot;-Farbe der Untertitel ist jetzt ein dunkler Farbton von blau (türkis) im Vergleich zu den vorherigen Primetime TVSDK-Versionen.

   Die Farbe wird von DarkCyan in Cyan geändert.

* Zendesk #30727 VOD-Anzeigen werden nicht heruntergeladen/aufgelöst.

   Wenn in VMAP XML ein leeres VAST-Tag ohne explizites schließendes Tag (&quot;&lt;/VAST>&quot;) und danach ohne Zeilenumbruchzeichen vorhanden ist, wird die VMAP-XML nicht korrekt analysiert und Anzeigen werden möglicherweise nicht abgespielt.

**Android TVSDK 2.5.1**

* Gerätespezifischer Absturz (Samsung Galaxy Tab 4); VOD DRM LBA mit Auditude und klicken Sie auf Anzeigen.
* VHL - Falsche Heartbeat-Aufrufe werden gesendet, wenn Inhalte von einem Offset aus gestartet werden.
* Bei der Wiedergabe von VPAID-Anzeigen fehlen die VHL-Heartbeat-Aufrufe für Ereignis:type:play-Anzeige.
* Nachdem der Player den Status ABGESCHLOSSEN erreicht hat, kehrt er bei Post-Roll-Anzeigen wieder zum PLAYING-Status mit SKIP adBreakPolicy zurück.
* Cookies werden nicht an ausgehende Anzeigenrückrufe angehängt.
* Anzeigen-Cue-Points sind nicht sichtbar.
* HLS mit separatem EAC3 SAP Track werden nicht geladen.
* Der Player stürzt ab, wenn TVSDK nach der Wiederherstellung des Media Player die Absicht &quot;Bildschirm ein&quot;erhält.

## Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

**Android TVSDK 2.7**

* TVSDK 2.7 unterstützt gleichzeitige Auflösungen von bis zu 5 Anzeigen.
* Bei einer VMAP-Antwort werden Anzeigenaufrufe in einer Werbeunterbrechung gleichzeitig gesendet und die Werbeunterbrechungen werden sequenziell gelöst.
* Im Falle von FER werden Anzeigenaufrufe bei jeder Gelegenheit gleichzeitig aufgelöst.

### Bekannte Probleme und Einschränkungen in früheren Versionen{#known-issues-limitations-previous-releases}

**Android TVSDK 2.5.6**

* Mehrere VMAP-Werbeunterbrechungen gleichzeitig werden nicht unterstützt.

**Android TVSDK 2.5.3**

Diese Version hat folgende Probleme:

* Bei der Live-Videowiedergabe treten möglicherweise Probleme mit der Audio-/Video-Synchronisierung auf Geräten mit niedrigem Ende oder bei schlechten Netzwerkbedingungen auf.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. Auch FER mit Versatz funktioniert nicht.
* Die Wiedergabe wird möglicherweise gestoppt, wenn der Inhalt von &quot;Spätbindung - Audio&quot;gesucht wird.
* Gelegentlich werden WebVTT-Beschriftungen für LIVE-Inhalte möglicherweise nicht mehr synchron.
* Nach einer Werbeunterbrechung kann immer wieder eine schnelle Wiedergabe einiger Frames auftreten.
* Manchmal wird der Fehler &quot;303&quot;für &quot;Tripple Wrapper Ad Breaks&quot;ausgegeben, auch wenn Anzeigen wiedergegeben werden.

**Android TVSDK 2.5.2**

Diese Version hat folgende Probleme:

* Bei der Live-Videowiedergabe treten möglicherweise Probleme mit der Audio-/Video-Synchronisierung auf Geräten mit niedrigem Status auf.
* Die Wiedergabe kann manchmal anhalten, wenn der Benutzer bis zum Ende des VOD-Mediums sucht.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. FER mit Versatz funktioniert ebenfalls nicht.

**Android TVSDK 2.5.1**

Diese Version von TVSDK hat folgende Probleme:

* Bei der Live-Videowiedergabe treten möglicherweise Probleme mit der Audio-/Video-Synchronisierung auf Geräten mit niedrigem Videostatus auf.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. FER mit Versatz funktioniert ebenfalls nicht.
* Wenn in der VMAP-XML ein leeres VAST-Tag ohne explizites schließendes Tag (&lt;/VAST>) vorhanden ist und danach kein Zeilenumbruch erfolgt, wird die VMAP-XML nicht korrekt analysiert und Anzeigen werden möglicherweise nicht abgespielt.
* VPAID-Post-Roll wird nicht unterstützt.

## Hilfreiche Ressourcen {#helpful-resources}

* [Systemanforderungen](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-2-7-for-android/overview/c-psdk-android-2_7-requirements.html)
* [TVSDK 2.7 für Android-Programmierhandbuch](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-2-7-for-android/overview/c-psdk-android-2_7-overview-prod-audience-guide.html)
* [TVSDK Android Javadoc für API-Referenz](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/index.html)
* [TVSDK Android C++ API-Dokument](https://help.adobe.com/en_US/primetime/api/psdk/cpp/namespaces.html)  - Jede Java-Klasse hat eine entsprechende C++-Klasse. Die C++-Dokumentation enthält mehr erklärende Informationen als die JavaScript-Dateien. In der C++-Dokumentation finden Sie daher ein tiefergehendes Verständnis der Java-API.
* [TVSDK 1.4 bis 2.5 für Android (Java)-Migrationshandbuch](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* Informationen zum Bearbeiten von Bildschirm-Ein-/Ausschalten-Szenarien finden Sie in der Datei `Application_Changes_for_Screen_On_Off.pdf`, die im Build enthalten ist.
* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).