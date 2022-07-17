---
title: TVSDK 2.7 für Android™ - Versionshinweise
description: TVSDK 2.7 für Android™ - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android™ 2.7
products: SG_PRIMETIME
topic-tags: release-notes
exl-id: d64f0ef2-60a9-43a1-b2f9-44764a570538
source-git-commit: 59ea8008c828f3bdf275fea5cc2a59c37b0c4845
workflow-type: tm+mt
source-wordcount: '4037'
ht-degree: 0%

---

# TVSDK 2.7 für Android™ - Versionshinweise {#tvsdk-for-android-release-notes}

TVSDK 2.7 für Android™ - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android™ 2.7

## TVSDK Android™ 2.7 {#tvsdk-android}

Der Android™-Referenz-Player ist im Verzeichnis &quot;samples/&quot;Ihrer Distribution im Lieferumfang von Android™ TVSDK enthalten. In der zugehörigen README&lt;.md-Datei wird erläutert, wie der Referenz-Player erstellt wird.

>[!NOTE]
>
>Um den Referenz-Player erfolgreich zu erstellen, wie in der mit der -Version verteilten README.md beschrieben, gehen Sie folgendermaßen vor:
>
>1. VideoHeartbeat.jar von herunterladen [https://github.com/Adobe-Marketing-Cloud/media-sdks/releases](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases) (VideoHeartbeat-Bibliothek für Android™ v2.0.0)
>1. Extrahieren Sie VideoHeartbeat.jar in den Ordner libs/ .

>


## Neue Funktionen {#new-features}

TVSDK 2.7 für Android™ umfasst alle Funktionen der Version 1.4 mit Ausnahme der nicht unterstützten Funktionen, die unter [Funktionsmatrix](#feature-matrix).

**Android™ TVSDK 2.7**

* **Unterstützung der parallelen Anzeigenauflösung**

TVSDK 2.7 unterstützt die gleichzeitige Auflösung aller Anzeigenanforderungen in einer Werbeunterbrechung anstelle einer sequenziellen Auflösung.

### Neue Funktionen in früheren Versionen {#new-features-previous-releases}

**Version 2.5.6**

* **TVSDK 2.5 unterstützt Android™ P**
* **Aktivieren von Hintergrund-Audio**

   Um die Audiowiedergabe zu aktivieren, wenn die App von vorne in den Hintergrund wechselt, sollte die App die API enableAudioPlaybackInBackground von MediaPlayer mit dem Argument &quot;true&quot;aufrufen, wenn der Player im Status &quot;PREPARED&quot;ist.

* **alwaysUseAudioOutputLatency(boolean val) in MediaPlayer-Klasse**

Verwenden Sie bei Festlegung die Latenz der Ausgabe in der Berechnung des Audio-Zeitstempels.
Boolesche Parameter val - True verwendet die Latenz der Audioausgabe bei der Berechnung des Audiozeitstempels.

* **Optimiert, um das beste Wiedergabeerlebnis zu erhalten, selbst wenn die Bandbreitengeschwindigkeit plötzlich abnimmt.**
TVSDK bricht jetzt bei Bedarf den Download des laufenden Segments ab und wechselt dynamisch zur entsprechenden Ausgabedarstellung. Dies geschieht durch einen nahtlosen Wechsel zwischen den Bitraten ohne Unterbrechungen.

**Version 2.5.5**

* **Einfügen einer partiellen Werbeunterbrechung**

   TV-ähnliche Erlebnisse beim Beitritt mitten in einer Anzeige, ohne dass das Tracking für die teilweise überwachte Anzeige ausgelöst wird.\
   Beispiel: Der Benutzer schließt sich in der Mitte (40 Sekunden) einer 90-Sekunden-Werbeunterbrechung an, die aus drei 30-Sekunden-Anzeigen besteht. Dies ist 10 Sekunden nach der zweiten Anzeige in der Pause.
   * Die zweite Anzeige wird für die verbleibende Dauer (20 Sek.) gefolgt von der dritten Anzeige wiedergegeben.
   * Anzeigentracker für die abgespielte partielle Anzeige (zweite Anzeige) werden nicht ausgelöst. Die Tracker für nur die dritte Anzeige werden ausgelöst.

* **Sicheres Laden von Anzeigen über HTTPS**

   Adobe Primetime bietet die Möglichkeit, den ersten Aufruf an den Primetime-Anzeigenserver und CRS über HTTPS anzufordern.

* **AdSystem und Creative ID zu CRS-Anforderungen hinzugefügt**

   * Jetzt einschließlich `AdSystem` und `CreativeId` als neue Parameter in den Anforderungen 1401 und 1403.

* **API setEncodeUrlForTracking in NetworkConfiguration-Klasse entfernt** als die unsicheren Zeichen in einer URL kodiert werden sollen.

**Version 2.5.4**

Android™ TVSDK v2.5.4 bietet die folgenden Updates und API-Änderungen:

* Änderungen am Standardwert für `WebViewDebbuging`

   Die `WebViewDebbuging` Wert auf _False_ Standardmäßig. Um sie zu aktivieren, rufen Sie `setWebContentsDebuggingEnabled` nach _True_ in der Anwendung.

* Aktualisierung der OpenSSL- und Curl-Version `libcurl` auf v7.57.0 und OpenSSL auf v1.0.2k.
* Zugriff auf App-Ebene für VAST-Antwortobjekt Einführung einer neuen API NetworkAdInfo::getVastXml() , die Zugriff auf das VAST-Antwortobjekt zur Anwendung bietet.

**Version 2.5.3**

Android™ TVSDK v2.5.3 bietet die folgenden Updates und API-Änderungen.

* Alle TVSDK-Kunden, die CRS verwenden, sollten ihre Apps mit TVSDK 2.5.3.85 oder der neuesten Version auf Android™ aktualisieren. Dies ist ein Abbruch-in-Ersatz für die vorhandene App-Implementierung. Überprüfen Sie nach dem TVSDK-Upgrade in einem Proxy-Tool (z. B.: Charles) und bestätigen Sie, dass der Hostname und die Version im Pfad wie in der Beispiel-URL-Struktur unten dargestellt sind.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* Benutzeragent von TVSDK anpassbar: haben wir einige neue APIs hinzugefügt, um die Benutzeragenten anzupassen.

   * `setCustomUserAgent`(Zeichenfolgenwert)
   * `getCustomUserAgent`()

* Cookies zwischen Android™-Anwendung und TVSDK freigeben: Android™ TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der Java™-Schicht (gespeichert im CookieStore der Android™-Anwendung) und der C++ TVSDK-Ebene. Jetzt ist es möglich, Cookies in der nativen C++-Ebene festzulegen und/oder zu ändern, da sie dem Java™ Cookie Store zur Verfügung gestellt werden.
* API-Änderungen:

   * Ein neues Ereignis CookiesUpdatedEvent wird hinzugefügt. Er wird vom Medienplayer gesendet, wenn sein Cookie aktualisiert wird.
   * Eine neue API wird hinzugefügt zu `NetworkConfiguration::set/ getCustomUserAgent()` , um benutzerdefinierten Benutzeragenten zu verwenden.
   * Eine neue API wird hinzugefügt zu `NetworkConfiguration::set/ getEncodedUrlForTracking` , um die Codierung von unsicheren Zeichen zu erzwingen.
   * Eine neue API wird hinzugefügt zu `NetworkConfiguration::getNetworkDownVerificationUrl()` , um eine URL für die Netzwerküberprüfung festzulegen, wenn ein Failover vorhanden ist.
   * TextFormat::handleSpaceAsAlphaNum wird um eine neue Eigenschaft ergänzt, die definiert, ob Leerzeichen beim Anzeigen von Untertiteln als alphanumerisch behandelt werden sollen.

* Änderungen in `SizeAvailableEvent`: Zuvor waren die Methoden getHeight() und getWidth() von `SizeAvailableEvent` in 2.5.2 verwendet, um die Frame-Höhe und die Frame-Breite zurückzugeben, die vom Medienformat zurückgegeben wurden. Jetzt werden die Ausgabehöhe und die vom Decoder zurückgegebene Ausgabebreite zurückgegeben.
* Änderungen im Pufferverhalten: Das Pufferverhalten ändert sich. Es bleibt dem App-Entwickler überlassen, was er tun möchte, wenn kein Puffer vorhanden ist. 2.5.3 verwendet die Wiedergabepuffergröße bei Pufferleersituationen.

**Version 2.5.2**

Android™ TVSDK v2.5.2 bietet wichtige Fehlerbehebungen und einige API-Änderungen.

**Version 2.5.1**

Die wichtigen neuen Funktionen, die in Android™ 2.5.1 veröffentlicht wurden.

* **Leistungsverbesserungen** Die neue TVSDK 2.5.1-Architektur bietet verschiedene Leistungsverbesserungen. Basierend auf Statistiken aus einer Benchmarking-Studie von Drittanbietern bietet die neue Architektur eine 5fache Reduzierung der Startzeit und 3,8mal weniger Dropped Frames im Vergleich zum Branchendurchschnitt:

   * **Sofortiges Aktivieren für VOD und Live -** Wenn Sie Sofort aktivieren, initialisiert und puffert das TVSDK Medien vor dem Start der Wiedergabe. Da Sie mehrere MediaPlayerItemLoader-Instanzen gleichzeitig im Hintergrund starten können, können Sie mehrere Streams puffern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, beginnt die Wiedergabe auf dem neuen Kanal sofort. TVSDK 2.5.1 unterstützt auch das Instant On für **live** auch Streams. Die Live-Streams werden beim Verschieben des Live-Fensters zwischengespeichert.

      * **Verbesserte ABR-Logik -** Die neue ABR-Logik basiert auf der Pufferlänge, der Änderungsrate der Pufferlänge und der gemessenen Bandbreite. Dadurch wird sichergestellt, dass die ABR bei Bandbreitenschwankungen die richtige Bitrate auswählt und die Anzahl der tatsächlichen Bitratenwechsel optimiert, indem die Geschwindigkeit überwacht wird, mit der sich die Pufferlänge ändert.
      * **Teilsegmentdownload/Untersegmentierung -** TVSDK reduziert die Größe jedes Fragments weiter, um die Wiedergabe so bald wie möglich zu starten. Das ts-Fragment muss alle zwei Sekunden einen Schlüsselframe aufweisen.
      * **Verzögerte Anzeigenauflösung -** TVSDK wartet nicht auf die Auflösung von Nicht-Pre-oll-Anzeigen, bevor die Wiedergabe gestartet wird, wodurch die Startzeit verkürzt wird. APIs wie Suche und Trick-Play sind immer noch nicht erlaubt, bis alle Anzeigen aufgelöst sind. Dies gilt für VOD-Streams, die mit CSAI verwendet werden. Vorgänge wie Suchen und Vorwärts sind erst nach Abschluss der Anzeigenauflösung zulässig. Bei Live-Streams kann diese Funktion nicht für die Anzeigenauflösung während eines Live-Ereignisses aktiviert werden.
      * **Persistente Netzwerkverbindungen -** Mit dieser Funktion kann TVSDK eine interne Liste persistenter Netzwerkverbindungen erstellen und speichern. Diese Verbindungen werden für mehrere Anforderungen wiederverwendet, anstatt für jede Netzwerkanforderung eine neue Verbindung zu öffnen und sie anschließend zu zerstören. Dies erhöht die Effizienz und verringert die Latenz im Netzwerkcode, was zu einer schnelleren Wiedergabeleistung führt.
Wenn TVSDK eine Verbindung öffnet, wird der Server um eine *Keep-Alive* Verbindung. Einige Server unterstützen diesen Verbindungstyp möglicherweise nicht. In diesem Fall führt TVSDK erneut eine Verbindung für jede Anfrage durch. Auch wenn persistente Verbindungen standardmäßig aktiviert sind, verfügt TVSDK jetzt über eine Konfigurationsoption, damit Apps persistente Verbindungen bei Bedarf deaktivieren können.
      * **Paralleler Download -** Durch das parallele Herunterladen von Video und Audio statt in Serien werden Starterverzögerungen reduziert. Diese Funktion ermöglicht die Wiedergabe von HLS Live- und VOD-Dateien, optimiert die verfügbare Bandbreitennutzung von einem Server, verringert die Wahrscheinlichkeit, in Puffersituationen zu gelangen, und minimiert die Verzögerung zwischen Download und Wiedergabe.
      * **Parallele Anzeigendownloads -** TVSDK ruft Anzeigen parallel zur Inhaltswiedergabe vor dem Drücken der Werbeunterbrechung ab, wodurch Anzeigen und Inhalte nahtlos wiedergegeben werden können.

* **Wiedergabe**

   * **MP4-Inhaltswiedergabe -** MP4-Kurzclips müssen nicht neu transkodiert werden, um sie im TVSDK wiederzugeben.
Hinweis: ABR-Switching, Trick Play, Anzeigeneinfügung, späte Audiobindung und Untersegmentierung werden für die MP4-Wiedergabe nicht unterstützt.
   * **Trick play with adaptive bit rate (ABR) -** Mit dieser Funktion kann TVSDK im Trick Play-Modus zwischen iFrame-Streams wechseln. Sie können Nicht-iFrame-Profile verwenden, um Tricks mit geringeren Geschwindigkeiten abzuspielen.
   * **Smoother Trick Play -** Diese Verbesserungen verbessern das Benutzererlebnis:

          * Auswahl der adaptiven Bit- und Bildrate während der Trickwiedergabe basierend auf der Bandbreite und dem Pufferprofil
          * Verwenden Sie den Hauptstrom anstelle des IDR-Streams, um eine schnelle Wiedergabe mit bis zu 30 fps zu ermöglichen.
      
* **Inhaltsschutz**

   * **Auflösungsbasierter Output Protection -** Diese Funktion verknüpft Wiedergabeschränkungen mit bestimmten Auflösungen und bietet feinere DRM-Steuerelemente.

* **Workflow-Unterstützung**

   * **Integration der direkten Rechnungsstellung -** Dadurch werden Rechnungsmetriken an das Adobe Analytics-Backend gesendet, das von Adobe Primetime für vom Kunden verwendete Streams zertifiziert ist.
TVSDK erfasst automatisch Metriken gemäß dem Kundenverkaufsvertrag, um regelmäßige Nutzungsberichte zu generieren, die für Abrechnungszwecke erforderlich sind. Bei jedem Stream-Startereignis verwendet TVSDK die Adobe Analytics-Dateneinfüge-API, um Abrechnungsmetriken wie Inhaltstyp, durch Anzeigeneinfügung aktivierte Flags und DRM-aktivierte Flags - basierend auf der Dauer des abrechnungsfähigen Streams - an die Report Suite von Adobe Analytics Primetime zu senden. Dies beeinträchtigt nicht die Report Suites oder Server-Aufrufe des Kunden, die er selbst in Adobe Analytics Report Suites oder Server-Aufrufen verwendet. Auf Anfrage wird dieser Rechnungsverwendungsbericht regelmäßig an Kunden gesendet. Dies ist die erste Phase der Abrechnungsfunktion, die nur die Nutzungsabrechnung unterstützt. Sie kann mithilfe der in der Dokumentation beschriebenen APIs basierend auf dem Kaufvertrag konfiguriert werden. Diese Funktion ist standardmäßig aktiviert. Informationen zum Deaktivieren dieser Funktion finden Sie im Beispiel des Referenz-Players .
   * **Verbesserte Failover-Unterstützung -** Es wurden zusätzliche Strategien implementiert, um die unterbrechungsfreie Wiedergabe trotz eines Fehlers von Host-Servern, Wiedergabelisten und Segmenten fortzusetzen.

* **Werbung**

   * **Moat-Integration -** Unterstützung für die Anzeigensichtbarkeitsmessung von Moat.
   * **Companion Banner -** Neben einer linearen Anzeige werden begleitende Banner angezeigt, die häufig nach Ende der Anzeige in der Ansicht angezeigt werden. Diese Banner können vom Typ HTML (ein HTML-Snippet) oder vom Typ iframe (eine URL zu einer iframe-Seite) sein.

* **Analytics**

   * **VHL 2.0 -** Dies ist die neueste optimierte VHL-Integration (Video Heartbeats Library) für die automatische Erfassung von Nutzungsdaten für Adobe Analytics. Die Komplexität der APIs wurde verringert, um die Implementierung zu erleichtern. VHL-Bibliothek herunterladen [v2.0.0 für Android™](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases) und extrahieren Sie die JAR-Datei im Ordner &quot;libs&quot;.

* **SizeAvaliableEventListener**
   * Die Methoden getHeight() und getWidth() von SizeAvailableEvent geben jetzt die Ausgabe in Höhe bzw. Breite zurück. Das Anzeigeseitenverhältnis kann wie folgt berechnet werden:

      ```
      SizeAvailableEvent e;
      
      DAR = e.getWidth()/ e.getHeight();
      
      Storage Aspect Ratio in terms of Sar width and Sar height can also be used to calculate Frame width and Frame height:
      
      SAR = e.getSarWidth()/e.getSarHeight();
      
      frameHeight = e.getHeight();
      
      frameWidth = e.getWidth()/SAR;    
      ```

* **Cookies**

   * Android™ TVSDK unterstützt jetzt den Zugriff auf Java™-Cookies, die im CookieStore der Android™-Anwendung gespeichert sind. Es wird eine Callback-API (onCookiesUpdated) bereitgestellt, um aufzuzeichnen, wann immer ein neues Cookie als Teil des Antwortheaders &quot;Set-Cookie&quot;eingeht. Diese Cookies sind als Liste von HttpCookie(s) verfügbar, die für einen anderen URI/eine andere Domäne verwendet werden, indem diese Cookie-Werte mithilfe von CookieStore für diesen bestimmten URI/diese Domäne festgelegt werden. Gleichermaßen werden die Cookie-Werte in TVSDK mit der CookieStore Add API aktualisiert.

## Funktionsmatrix {#feature-matrix}

TVSDK für Android™ unterstützt verschiedene Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.

In den unten stehenden Funktionstabellen zeigt ein &quot;Y&quot;an, dass die Funktion in der aktuellen Version unterstützt wird.

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | VOD + Live | Y |
| FER - Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | FER VOD | Y |
| Suchen, wann eine Anzeige wiedergegeben wird | VOD + Live | Nicht unterstützt |
| AC3 | VOD + Live | Nicht unterstützt |
| MP3 | VOD | Nicht unterstützt |
| MP4-Inhaltswiedergabe | VOD | Y |
| Adaptive Bit Rate Switching Logic | VOD + Live | Y |
| Nur-Audio-Wiedergabe | VOD + Live | Y |
| Multi-CDN-Unterstützung | VOD + Live | Nicht unterstützt |
| Wiedergabe von Anzeigen mit Nur-Audio-Medien | VOD + Live | Nicht unterstützt |
| Geschlossene Untertitel - 608/708 | VOD + Live | Y |
| Geschlossene Untertitel - WebVTT | VOD + Live | Y |
| Manifest-Failover | VOD + Live | Y |
| Erweitertes Failover | VOD + Live | Y |
| QoS- und Player-Benachrichtigungen | VOD + Live | Y |
| Unterstützung für Cookie-Kopfzeilen | VOD + Live | Y |
| Unterstützung für benutzerdefinierte HTTP-Header | VOD + Live | Y (Zulassungsauflistung erforderlich) |
| Puffersteuerungsparameter festlegen | VOD + Live | Y |
| Festlegen von adaptiven Bitratensteuerelementen | VOD + Live | Y |
| Benutzerdefinierte Manifest-Tags | VOD + Live | Y |
| Späte Audio-Bindung | VOD + Live | Y |
| 302 Umleitung | VOD + Live | Y |
| Wiedergabe mit Versatz | VOD + Live | Y |
| Nur Audio wiedergeben | VOD + Live | Y |
| Trick Play | VOD + Live | Y |
| Langsame Bewegung in Trick Play | VOD + Live | Nicht unterstützt |
| Glattes Trick Play (mit ABR) | VOD + Live | Y |
| ID3-Analyse | VOD + Live | Y |
| Werbeanzeigen ausblenden | VOD + Live | Nicht unterstützt |
| Sofort aktiviert | VOD + Live | Nicht unterstützt |
| Unterstützung von Diskontinuitätsmarken | VOD + Live | Y |
| 302 Umleitungs-Stickiness | VOD + Live | Y |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Allgemeine Wiedergabe, Anzeigen aktiviert | VOD + Live | Y |
| Fairer Inhalt mit aktivierten Anzeigen | VOD | Y |
| Standardmäßige Anzeigenverhalten | VOD + Live | Y |
| VAST 2.0/3.0 | VOD + Live | Y |
| VMAP 1.0 | VOD + Live | Y |
| MP4-Anzeigen | VOD + Live | Y (aus CRS) |
| Trick Play mit aktivierten Anzeigen | VOD + Live | Y |
| Nur Anzeige | VOD | Y |
| Targeting-Parameter | VOD + Live | Y |
| Benutzerdefinierte Parameter | VOD + Live | Y |
| Benutzerdefiniertes Anzeigenverhalten | VOD + Live | Y |
| Benutzerdefinierte Anzeigen-Tags | Live | Y |
| Benutzerdefinierte Anzeigenauflöser | VOD + Live | Y |
| Freewheel Custom Ad Resolver | VOD | Y |
| C3 | VOD + Live | Nicht unterstützt |
| Lazy Ad Resolve | VOD | Y |
| Unterstützung von Diskontinuitätsmarken - SSAI | VOD + Live | Y |
| Companion Ads, Banneranzeigen und klickbare Anzeigen | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y (JS) |
| Beenden einer frühzeitigen Anzeige | Live | Y |
| Regelbasierte kreative Priorisierung | VOD + Live | Y |
| CRS-Regeln | VOD + Live | Y |
| JSON Ad Resolver | VOD + Live | Nicht unterstützt |
| Mottenintegration | VOD + Live | Y |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| AES-Verschlüsselung | VOD + Live | Y |
| AES-Beispielverschlüsselung | VOD + Live | Y |
| Tokenisierte Streams | VOD + Live | Y |
| DRM | VOD + Live | Nur Primetime DRM (Future: Widevine) |
| Externe Wiedergabe (RBOP) | VOD + Live | Nur Primetime DRM |
| Lizenzrotation | VOD + Live | Nur Primetime DRM |
| Hauptrolle | VOD + Live | Nur Primetime DRM |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Adobe Analytics VHL-Integration | VOD + Live | Y |
| Rechnungsstellung | VOD + Live | Y |

## Gelöste Probleme {#resolved-issues}

Wenn die Lösung mit einem gemeldeten Problem verbunden ist, wird eine Zendesk-Referenz angezeigt, z. B. ZD#xxxxx

**Android™ TVSDK 2.7**

Dieser Abschnitt enthält eine Zusammenfassung des Problems, das in der TVSDK-Version 2.7 behoben wurde.

* ZD#37166 - Fehler-Tracking-Aufruf wird ausgelöst, auch wenn die Anzeige korrekt wiedergegeben wird.
* ZD#37134 - Falsche Anzeigen-IDs werden zurückgegeben, falls Wrapper(3P) Ad mit mehreren Anzeigen in der VMAP-Antwort vorhanden ist.

**Android™ TVSDK 2.5.6**

* ZD #34992 - Die Sprache ist in &quot;Geschlossene Beschriftung&quot;leer.
   * Es wurde ein Fall behoben, bei dem TVSDK #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS vom Hauptmanifest nicht analysiert hat, um die Details des Untertiteltracks abzurufen.
* ZD #35078 - Android P validation.
   * TVSDK 2.5.6 wurde mit den neuesten Beta-Builds von Android™ P validiert. Keine Probleme aufgrund des neuen Android™ OS gefunden.
* ZD #34149 - Der Player fordert weiterhin Manifeste an, auch wenn ein Fehler auftritt.
   * Fehlerkorrektur - TVSDK führt jetzt keine wiederholten Aufrufe mehr durch, selbst wenn alle Profile ausfallen (404-Fehler).
* ZD #31533 - Playing audio on Android™, nachdem die App in den Hintergrund gesendet wurde.
   * Hinzugefügt `enableAudioPlaybackInBackground` API von MediaPlayer, die mit &quot;True&quot;als Argument aufgerufen werden sollte (wenn der Player im Status &quot;VORBEREITT&quot;ist), um die Wiedergabe von Audio zu aktivieren, wenn die App im Hintergrund ausgeführt wird.

**Android™ TVSDK 2.5.5**

* ZD #21647 - Android TVSDK benachrichtigt 640 x 368, wenn die tatsächliche Videogröße 640 x 360 beträgt.
   * Aufgrund der Variablen m_nOutputHeight (innerhalb von AndroidMCVideoDecoder) wird die Frame-Höhe anstelle der tatsächlichen Ausgabehöhe aktualisiert. Es wurden relevante Änderungen an der Funktion getVideoFrame vorgenommen, um m_nOutputHeight korrekt zu berechnen.
* ZD #26614 - Urgent — third party ad serving/programmatic — Fehler bei der Bereitstellung von Impressionen.
   * Die frühere Korrektur wurde verbessert, indem die Groß-/Kleinschreibung in XML-Parsing verarbeitet wurde, bei der das Problem reproduzierbar war, wenn &quot;Leerzeichen&quot;vor dem &quot;Gleichheitszeichen&quot;liegt, wie &lt;vast version=&quot;2.0&quot;>
* ZD #29296 - Android: Fügen Sie AdSystem und Creative ID zu CRS-Anforderungen hinzu.
   * Jetzt einschließlich &#39;AdSystem&#39; und &#39;CreativeId&#39; als neue Parameter in den Anfragen 1401 und 1403.
* ZD #33062 - TVSDK stürzt beim Auftreten des Pipe-Zeichens in der VAST-Antwort unter dem CDATA-Knoten ab
   * API setEncodeUrlForTracking in NetworkConfiguration-Klasse wurde als unsichere Zeichen in einer URL, die kodiert werden soll, entfernt.
* ZD #33063 - CRS-Dateiauswahllogik war fehlerhaft - TVSDK sendete keine CRS-Anforderung für das Webm-Format, sondern schickte sie stattdessen für 3gpp-Dateien.
   * Die Logik wurde jetzt korrigiert. Bei der Verwendung von Mediendateien mit Webm- und 3gpp-Format muss eine CRS-Anfrage für Webm gesendet werden. Bei Verwendung der beiden Mediendateien im 3gpp-Format wird die CRS-Anforderung für die höchste Bitrate-3gpp-Datei gesendet.
* ZD #33125 - Die Android-App stürzt mit einem bestimmten DoubleClick-Tag im VMAP ab.
   * Das Szenario wurde behoben, um den Absturz zu vermeiden.
* ZD #32256 - License Rotation &amp; Key Rotation Issue - Adobe Access.
   * Die Segmentinitialisierung mit den DRM-Metadaten für SampleAES-Inhalt wurde korrigiert. Funktioniert problemlos mit AES128-Inhalten.
* ZD #33619 - Schnelle Weiterleitung eines wachsenden Playlist-Inhalts, der in der Nähe des Live-Punkts im Pufferstatus steckte.
   * Handle den Fall beim Überschreiten des Live-Punkts im Trick Play-Modus.
* ZD #34151 - TimedMetadata-Objekte nicht in der Reihenfolge.
   * Zwei TimedMetadata-Ereignisse wurden in zufälliger Reihenfolge angezeigt, wenn sie zur gleichen Zeit in der Timeline gehörten. Die ursprüngliche Reihenfolge wurde manifestiert.
* ZD #34189 - Problem beim Versuch, eine Werbeunterbrechung zu beginnen.
   * Das Problem betraf SSAI-Anzeigen, die mit Diskontinuität zugeordnet werden. Die Ursache war ein Verhalten, wenn wir versuchen, solche Anzeigen zu beginnen, wir nach einem Keyframe suchen und ihn nicht finden. Der Grund dafür war, dass der Audio-Zeitstempel der Anzeige vor dem Min-Video-Zeitstempel lag. Daher suchen wir am Ende nach einem Schlüsselframe mit falschen fragmentDump-Daten. Jetzt behoben.
* ZD #34528 - Videoauflösung, die auf dem Dongle der dritten Generation von FireTV nicht über 640 x 360 aktualisiert wird.
   * Die Fehlerbehebung wurde um die neuesten Firmware-Updates erweitert.
* ZD #34793 - TVSDK 2.5.x zum Absturz mit dem benutzerdefinierten Content Resolver verwendet, manchmal, wenn VideoEngine davon ausging, dass die auditudeSettings verfügbar sind und nicht.
   * Der Absturz erfolgte aufgrund eines Funktionsaufrufs an einem gemeinsam genutzten Null-Zeiger (auditudeSettings). Es wurde eine bedingte Prüfung in VideoEngineTimeline::placeToSourceTimeline() hinzugefügt, um sicherzustellen, dass auditudeSettings verfügbar ist, bevor irgendetwas für dieses Objekt aufgerufen wird.
* ZD #32584 - Es ist nicht möglich, auf vollständige Informationen im Abschnitt &lt;extensions> -Knoten einer VAST-Antwort.
   * Es wurde ein Problem mit der XML-Analyse behoben, sodass NetworkAdInfo jetzt die vollständigen Informationen im Abschnitt &lt;extensions> Knoten.
* ZD #35086 - Unvollständige Erweiterungsdaten vom Player erhalten, wenn bestimmte VMAP-Antworten vorhanden sind.
   * Das Problem war spezifisch für die Erweiterung XML, da das XML-Parsing nicht funktionierte, wenn die Erweiterung XML doppelte Anführungszeichen im Attributwert enthielt. Korrektur des Problems.

**Android™ TVSDK 2.5.4**

* ZenDesk#33659 - Wiedergabesitzung zur Aktivierung des Remote-Debugging von Webansichten.
   * WebViewDebbuging ist standardmäßig auf False festgelegt. Um das Debugging zu aktivieren, legen Sie mithilfe von setWebContentsDebuggingEnabled(true) den Wert true über die Anwendung fest.
* ZenDesk#33011 - Die Anzeigen-Timeline wird nicht aufgelöst, wenn eine fehlgeschlagene CRS-Anforderung vorliegt.
   * Wenn eine CRS-Anfrage an eine Anzeige fehlschlägt, wird die Timeline aufgelöst und die verbleibenden Anzeigen werden wiedergegeben.
* ZenDesk#34528 - Die Videoauflösung wird auf dem Dongle der dritten Generation von FireTV nicht über 640x360 aktualisiert.
   * Die Videoauflösung schaltet sich als Bitratenschalter hoch.
* ZenDesk#33192 - AudioTrack hat einen Nullnamen, wenn die Verfolgung über AudioUpdatedEventListener::onAudioUpdated abgerufen wird.
   * In einigen Szenarien zum FireTV-Stick wurde das onAudioUpdate-Ereignis ausgelöst, wenn kein tatsächliches Audio-Update vorhanden war. Dieses Problem wurde jetzt behoben.

**Android™ TVSDK 2.5.3**

* Zendesk#32216 - Benutzerdefiniertes Tag-Abonnement für TimedMetadata funktioniert nicht.
   * Wir geben ID3-Daten als Byte-Array (zur Unterstützung von APIC- oder generischen Daten) an den Client zurück, während in Version 1.4 eine Zeichenfolge zurückgegeben wird. Das Byte-Array verarbeitet das von null beendete Zeichen nicht selbst. Daher zeigte es dem Client Sonderzeichen an. Dieses Problem wurde jetzt behoben.
* Zendesk#32670 - Player kann nicht auf redundante Playlist gesetzt werden
   * Dies funktioniert jetzt einwandfrei und setNetworkDownVerificationUrl funktioniert erwartungsgemäß.
* Zendesk#32369 - Die verdeckte Beschriftung zeigt unterschiedliche Farbverläufe oder Artefakte.
   * Problem mit CC-Fehlern wurde im aktuellen Build behoben
* Zendesk#25590 - Verbesserung: TVSDK-Cookie-Store (C++ zu Java™)
   * Android™ TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der Java™-Schicht (gespeichert im CookieStore der Android™-Anwendung) und der C++ TVSDK-Ebene.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 scheint keine Fehlerbehebung für PTPLAY-20269 zu haben Dieses Problem wurde behoben und in die Verzweigung 2.5.2 integriert.
* Zendesk#31806 - Auditude sticks im PrePARING Player waren im Status &quot;Vorbereiten&quot;stecken geblieben, da Antwort-XML ein leeres Tag enthielt. Jetzt wurde das Problem behoben.
* Zendesk#31727 - TVSDK 2.5 Zeichen für geschlossene Beschriftungen werden entfernt oder falsch geschrieben.
   * Das Problem wurde behoben, und es werden keine Zeichen durch Ablegen/Fehlschreiben ersetzt.
* Zendesk#31485 - DrmManager in 2.5
   * Es gab ein Problem beim Erstellen von DRMManager über den neuen DRMManager (Kontext). Implementierung der DRMService-Klasse, die DRMManager bereitstellt.
* Zendesk#32794- 1080P Auflösungsstream wird nicht auf Android™ wiedergegeben.
   * SizeAvailableEvent wurde geändert. Zuvor `getHeight()` und `getWidth()` Methoden von SizeAvailableEvent in 2.5, die verwendet werden, um die Frame-Höhe und die Frame-Breite zurückzugeben, die vom Medienformat zurückgegeben wurden. Jetzt werden die Ausgabehöhe und die Ausgabebreite zurückgegeben, die jeweils vom Decoder zurückgegeben wurden.
* Zendesk #19359 Flash Player stürzt aufgrund der Position des Attributs #EXT-X-FAXS-CM im Manifest auf Setebene ab.
   * Das Tag #EXT-X-FAXS-CM muss immer auf der oberen Wiedergabeliste stehen, bevor einzelne Bitraten oder Segmente in der Wiedergabeliste angezeigt werden.

**Android™ TVSDK 2.5.2**

* Zendesk#17305 Artefakte in geschlossenen Untertiteln mit nicht opaken Hintergrund.
setTreatSpaceAsAlphaNum -Eigenschaft in TextFormat angezeigt wird. Standardmäßig ist die Eigenschaft False. Setzen Sie die Eigenschaft in einem Client auf True , um das Problem mit dem dunklen Bereich zu beheben.

* Die Anzeige in Zendesk#25097 CC verfügt über visuelle Artefakte mit CC-Einstellungen.
setTreatSpaceAsAlphaNum -Eigenschaft in TextFormat angezeigt wird. Standardmäßig ist die Eigenschaft False. Setzen Sie die Eigenschaft in einem Client auf True , um das Problem mit dem dunklen Bereich zu beheben.

* Zendesk #31620 Benutzeragenten-Zeichenfolge, die aus dem TVSDK-Player entfernt wird, wird abgeschnitten.
Die Benutzeragenten-Zeichenfolge wird nach 128 Zeichen nicht mehr abgeschnitten.
Adobe Primetime-Versionszeichenfolge wird dem Systembenutzeragenten hinzugefügt.

* Zendesk #30809 Fehlendes SEEK_END-Ereignis verhindert, dass die App in einen Wiedergabestatus wechselt.
* Zendesk #30415 Die Farbe &quot;Cyan&quot;der verdeckten Beschriftung ist jetzt im Vergleich zu früheren Primetime TVSDK-Versionen dunkler (türkis).

   Die Farbe wird von DarkCyan in Cyan geändert.

* Zendesk #30727 VOD-Anzeigen werden nicht heruntergeladen/aufgelöst.

   In VMAP XML, wenn ein leeres VAST-Tag ohne explizites schließendes Tag (&quot;&lt;/vast>&#39;) und ohne Zeilenumbruchzeichen danach wird die VMAP-XML nicht richtig analysiert und Anzeigen werden möglicherweise nicht wiedergegeben.

**Android™ TVSDK 2.5.1**

* Gerätespezifischer Absturz (Samsung Galaxy Tab 4); VOD DRM LBA mit Auditude und klicken Sie auf Anzeigen.
* VHL - Beim Start von Inhalten ab einem Versatz werden falsche Heartbeat-Aufrufe gesendet.
* Wenn VPAID-Anzeigen wiedergegeben werden, ruft der VHL-Heartbeat das Ereignis auf:type:Abspielanzeige fehlt.
* Nachdem der Player den Status ABGESCHLOSSEN erhalten hat, wechselt er für Post-Roll-Anzeigen wieder zum PLAYING-Status mit SKIP adBreakPolicy .
* Cookies werden nicht an ausgehende Anzeigen-Callbacks angehängt.
* Anzeigen-Cue-Punkte sind nicht sichtbar.
* HLS mit separatem EAC3 SAP Track wird nicht geladen.
* Der Player stürzt ab, wenn TVSDK nach der Wiederherstellung des Media-Players den Intent &quot;Bildschirm ein&quot;erhält.

## Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

**Android™ TVSDK 2.7**

* TVSDK 2.7 unterstützt die gleichzeitige Auflösung von bis zu fünf Anzeigen.
* Im Falle einer VMAP-Antwort gehen Anzeigenaufrufe in einer einzelnen Werbeunterbrechung parallel vor und die Werbeunterbrechungen werden sequenziell aufgelöst.
* Im Falle eines FER werden Anzeigenaufrufe bei jeder Gelegenheit gleichzeitig aufgelöst.

### Bekannte Probleme und Einschränkungen in den vorherigen Versionen{#known-issues-limitations-previous-releases}

**Android™ TVSDK 2.5.6**

* Mehrere VMAP-Werbeunterbrechungen gleichzeitig werden nicht unterstützt.

**Android™ TVSDK 2.5.3**

Diese Version weist die folgenden Probleme auf:

* Die Live-Videowiedergabe kann auf Geräten mit geringer Auslastung oder unter schlechten Netzwerkbedingungen Probleme bei der Audio-Video-Synchronisierung aufweisen.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. Auch FER mit Versatz funktioniert nicht.
* Die Wiedergabe wird möglicherweise blockiert, wenn der Inhalt von &quot;Spätbindung an Audio&quot;gesucht wird.
* Gelegentlich können WebVTT-Untertitel für LIVE-Inhalte nicht mehr synchron sein.
* Gelegentlich kann nach einer Werbeunterbrechung eine schnelle Wiedergabe einiger Frames auftreten.
* Manchmal wird der 303-Fehler für &quot;Triple Wrapper Ad Breaks&quot;ausgegeben, auch wenn Anzeigen wiedergegeben werden.

**Android™ TVSDK 2.5.2**

Diese Version weist die folgenden Probleme auf:

* Die Live-Videowiedergabe kann auf Geräten mit geringer Auslastung Probleme mit der Audio-Video-Synchronisierung haben.
* Die Wiedergabe kann beim Suchen nach dem Ende des VOD-Mediums anhalten.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. Außerdem funktioniert FER mit Versatz nicht.

**Android™ TVSDK 2.5.1**

Diese TVSDK-Version weist die folgenden Probleme auf:

* Die Live-Videowiedergabe kann auf Geräten mit geringer Auslastung Probleme mit der Audio-Video-Synchronisierung haben.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. Außerdem funktioniert FER mit Versatz nicht.
* Wenn in der VMAP-XML ein leeres VAST-Tag ohne ein explizites schließendes Tag (&lt;/vast>) und ohne einen Zeilenumbruch danach wird die VMAP-XML nicht richtig analysiert und Anzeigen werden möglicherweise nicht wiedergegeben.
* VPAID-Post-Roll wird nicht unterstützt.

## Hilfreiche Ressourcen {#helpful-resources}

* [Systemanforderungen](/help/programming/tvsdk-2.7-for-android/c-psdk-android-2.7-requirements.md)
* [TVSDK 2.7 für Android™-Programmierhandbuch](/help/programming/tvsdk-2.7-for-android/overview-prod-audience-guide/c-psdk-android-2.7-overview-prod-audience-guide.md)
* [TVSDK Android™ Javadoc für API-Referenz](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/index.html)
* [TVSDK Android™ C++ API-Dokument](https://help.adobe.com/en_US/primetime/api/psdk/cpp/namespaces.html) - Jede Java™-Klasse verfügt über eine entsprechende C++-Klasse. Die C++-Dokumentation enthält mehr erklärendes Material als die Java™-Dokumente. Weitere Informationen zur Java™-API finden Sie in der C++-Dokumentation.
* [Migrationshandbuch für TVSDK 1.4 bis 2.5 für Android™ (Java™)](/help/migration-guides/tvsdk-14-25-android.md)
* Informationen zur Handhabung von Ein-/Ausschaltszenarien für den Bildschirm finden Sie im Abschnitt `Application_Changes_for_Screen_On_Off.pdf` im Build enthaltene Datei.
* Die vollständige Hilfedokumentation finden Sie unter [Adobe Primetime - Lernen und Support](https://experienceleague.adobe.com/docs/primetime.html) Seite.
