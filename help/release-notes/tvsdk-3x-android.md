---
title: TVSDK 3.12 für Android-Versionshinweise
seo-title: TVSDK 3.12 für Android-Versionshinweise
description: TVSDK 3.12 für Android - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 3.12
seo-description: TVSDK 3.12 für Android - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 3.12
uuid: 685d46f5-5a02-4741-af5c-91e91babd6f7
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 3a27379f-3cef-4ea3-bcae-21382dc1e9fd
translation-type: tm+mt
source-git-commit: d1881d1fe97d416ee0f69f62828aef46c5ad21bb
workflow-type: tm+mt
source-wordcount: '5415'
ht-degree: 0%

---


# TVSDK 3.12 für Android-Versionshinweise {#tvsdk-for-android-release-notes}

TVSDK 3.12 für Android - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 3.12.

Der Android-Referenzplayer ist im Verzeichnis samples/ Ihrer Distribution im Lieferumfang von Android TVSDK enthalten. In der zugehörigen Datei README.md wird beschrieben, wie Sie den Referenz-Player erstellen.

>[!NOTE]
>
>Um den Referenz-Player erfolgreich zu erstellen, wie in README.md beschrieben, das mit der Version verteilt wird, führen Sie folgende Schritte durch:
>
>1. VideoHeartbeat.jar von [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) herunterladen (VideoHeartbeat-Bibliothek für Android v2.0.0)
>1. Extrahieren Sie VideoHeartbeat.jar in den Ordner libs/.
>



TVSDK für Android bietet viele Leistungsverbesserungen im Vergleich zu früheren Versionen. Es bietet ein hochwertiges Anzeigeerlebnis und umfasst alle Funktionen von Version 1.4, mit Ausnahme von Multi-CDN-Unterstützung.

Die umfassenden Funktionen, die unterstützt und nicht unterstützt werden, finden Sie im Abschnitt [Funktionsmatrix](#feature-matrix) der Versionshinweise.

## Android TVSDK 3.12

Die Gradle Version der Primetime Reference-Anwendung wird jetzt auf Version 5.6.4 aktualisiert.

Um die Referenz-App mit Android Studio einzurichten und auszuführen, befolgen Sie die Anweisungen in der ReadMe-Datei, die mit TVSDK zip verfügbar ist unter `TVSDK_Android_x.x.x.x/samples/PrimetimeReference/src/README.md`.

Die wichtigsten in der aktuellen Version behobenen Kundenprobleme werden im Abschnitt [gelöste Probleme](#resolved-issues) beschrieben.

### Neue Funktionen und Verbesserungen in früheren Versionen

**Android TVSDK 3.11**

* **Protection System specific Header (PSSH) Box Abrufen zulässig** - TVSDK ermöglicht das Abrufen des Schutzsystem-spezifischen Header Box, das mit der aktuell geladenen Medienressource verknüpft ist. Neue API `getPSSH()` hinzugefügt `com.adobe.mediacore.drm.DRMManager`.

Weitere Informationen finden Sie unter [Widevine DRM](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md).

**Android TVSDK 3.10**

Die Veröffentlichung konzentrierte sich auf die Behebung der wichtigsten Kundenprobleme, wie im Abschnitt [gelöste Probleme](#resolved-issues) beschrieben.

**Android TVSDK 3.9**

* **Secure Versand over HTTPS** - Android TVSDK 3.9 bietet die Funktion zum sicheren Versand über HTTPS, um Inhalte mit beispielloser Skalierbarkeit und Performance sicher bereitzustellen.

   Um sicheren Versand über HTTPS zu aktivieren, wurde in der `NetworkConfiguration` Klasse eine neue API eingeführt.

   `public void setForceHTTPS (boolean value)`

   `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **Pre-Roll-Unterstützung mit Teil-Werbeunterbrechung** - Mit dieser Verbesserung unterstützt TVSDK 3.8 Pre-Roll-Anzeigen mit Teil-Ad-Break-Funktion (PABI).

Die Pre-Roll-Anzeige wird, sofern verfügbar, abgespielt und dann vom Live-Point aus wiedergegeben, der dem Erlebnis des Live-Fernsehens nachbildet.

**Android TVSDK 3.7**

* Bei Widevine-Testinhalten wird eine neue API `setMediaDrmCallback` in der DRMManager-Klasse bereitgestellt, um die Standardimplementierung der MediaDRMCallback-Schnittstelle zu überschreiben.

   `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* Der AppCrash-Fehler wurde behoben, der dafür gesorgt hatte, dass `MediaPlayerEvent.ITEM_UPDATED` die C++-Ebene (64 Bit Android) nicht verarbeitet wurde.

**Android TVSDK 3.6**

* **Verbessern Sie Ihre Apps für die 64-Bit-Anforderung** - Die native Bibliothek `(libAVEAndroid.so)` wird jetzt aktualisiert und in zwei Versionen zur Verfügung gestellt. Der Speicherort der vorhandenen nativen Armeabi-Bibliothek (32 Bit) wurde geändert `/framework/Player to /framework/Player/armeabi` und eine zusätzliche arm64-v8a-Bibliothek (64 Bit) wurde in `/framework/Player/arm64-v8a.`

**Version 3.5**

* **Just In Time Ad Resolution** - TVSDK 3.5 entfernt die Unterstützung der abgespielten Anzeigen aus der Zeitschiene.

* **Unterstützung für die Offline-Wiedergabe** aktiviert - Bei der Offline-Wiedergabe können Benutzer Videoinhalte jetzt auf ihre Geräte herunterladen und anzeigen, wenn keine Verbindung besteht. Ausführliche Informationen finden Sie unter &quot;[Offline-Wiedergabe mit Android](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf)&quot;.

**Version 3.4**

* TVSDK unterstützt jetzt die Wiedergabe von CMAF-Streams für CBC-verschlüsselte und einfache Streams.

**Version 3.3**

* **API-Änderungen**

   * Eine neue API wird hinzugefügt, um Netzwerkfehler und Zeitüberschreitungen `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` zu verarbeiten.
      * wobei n die Anzahl der weitere Zustellversuche ist.

**Version 3.2**

* **Unterstützung für parallele Anzeigenauflösung und Manifestdownload**

   * TVSDK 3.2 unterstützt die gleichzeitige Auflösung anstelle der sequenziellen Auflösung für alle Anzeigenanforderungen und Werbeunterbrechungen mit Ausnahme von VMAP.

   * Alle Anzeigenmanifeste in einer Werbeunterbrechung werden gleichzeitig heruntergeladen.

* **Unterstützung für Anzeigenauflösung und Manifestdownload-Timeout aktiviert.**

   * Benutzer können jetzt den Timeout-Wert für die gesamte Anzeigenauflösung und Manifestdownloads festlegen.  Bei VMAP gilt der Timeout-Wert für einzelne Werbeunterbrechungen, da alle Werbeunterbrechungen sequenziell gelöst werden.

* **Neue APIs in der AdvertisingMetadata-Klasse:**

   * `void setAdResolutionTimeout(int adResolutionTimeout)`

   * `int getAdResolutionTimeout()`

   * `void setAdManifestTimeout(int adManifestTimeout)`

   * `int getAdManifestTimeout()`

* **Unter APIs aus der AdvertisingMetadata-Klasse entfernt:**

   * `void setAdRequestTimeout(int adRequestTimeout)`

   * `int getAdRequestTimeout()`

* **Wiedergabe von Streams mit AC3/EAC3-Audio-Codec aktiviert**

   * `void alwaysUseAC3OnSupportedDevices(boolean val)` in `MediaPlayer` Klasse

* **TVSDK unterstützt die Wiedergabe von CMAF- und Nur-Streams für verschlüsselte Widevine CTR.**

* **Die Wiedergabe von 4K HEVC-Streams wird jetzt unterstützt.**

* **Parallele Anzeigenaufrufanforderungen** - TVSDK ruft jetzt parallel 20 Anzeigenaufrufanforderungen ab.

**Version 3.0**

* **TVSDK 3.0 unterstützt HEVC-Streams (High Efficiency Video Coding).**

* **Just in Time - Durch das Beheben von Anzeigen, die näher an Anzeigenmarken** liegen, wird jetzt jede Werbeunterbrechung unabhängig voneinander gelöst. Zuvor war die Anzeigenauflösung ein zweistufiger Ansatz: Pre-Roll-Aufnahmen wurden vor dem Beginn der Wiedergabe aufgelöst und alle Mid-/Post-Roll-Slots nach dem Start der Wiedergabe kombiniert. Mit dieser erweiterten Funktion wird jeder Werbeunterbrechung nun zu einem bestimmten Zeitpunkt vor dem Anzeigen-Cue-Point aufgelöst.

> [!NOTE]
>
> Die verzögerte Anzeigenauflösung wurde jetzt standardmäßig deaktiviert und muss explizit aktiviert werden.

Eine neue API wird hinzugefügt, `AdvertisingMetadata::setDelayAdLoadingTolerance` um die Toleranz für verzögertes Laden der Anzeige im Zusammenhang mit diesen Advertising Metadata abzurufen.\
Die Suche ist jetzt unmittelbar nach der Vorbereitung zulässig, wenn Sie nach Werbeunterbrechungen suchen, wird eine sofortige Auflösung vor Abschluss der Suche erzielt.\
Signalisierungsmodi `SERVER_MAP` und - `MANIFEST_CUES` funktionen werden unterstützt.

Weitere Informationen finden Sie unter [TVSDK 3.0 für Android-Programmierhandbuch](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/c-lazy-ad-resolving.md) zu API- und Ereignis-Änderungen.

* **Auf`targetSdkVersion`neueste Version aktualisiert**

Aktualisierung `targetSdkVersion` von 19 auf 27 für reibungslose Funktionsweise.

* **Placement.Type getPlacementType() ist jetzt eine Methode auf der Schnittstelle TimelineMarker**

   Diese Methode gibt einen Platzierungstyp von Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL oder Placement.Type.POST_ROLL zurück. Wenn eine Werbeunterbrechung ungelöst ist, gibt die getDuration()-Methode auf der TimelineMarker-Schnittstelle 0 zurück.

**Version 2.5.6.**

* **TVSDK 2.5 unterstützt Android P.**

* **Hintergrundaudio aktivieren**

   Um die Audiowiedergabe zu aktivieren, wenn die App von vorne in den Hintergrund wechselt, sollte die App die MediaPlayer- `enableAudioPlaybackInBackground` API mit true als Argument aufrufen, wenn sich der Player im VORBEREITTEN Status befindet.

* **alwaysUseAudioOutputLatency(boolean val) in der MediaPlayer-Klasse**

Verwenden Sie bei Festlegung die Ausgabedatenz in der Berechnung des Audio-Zeitstempels.
Boolesche Parameter val - True verwendet die Latenz der Audioausgabe bei der Berechnung des Audiozeitstempels.

* **Optimiert, um die beste Wiedergabe zu erzielen, selbst wenn die Bandbreite plötzlich abfällt**

TVSDK bricht jetzt bei Bedarf den Download des aktuellen Segments ab und wechselt dynamisch zur entsprechenden Darstellung. Dies geschieht durch einen nahtlosen Wechsel zwischen den Bitraten ohne Unterbrechungen.

**Version 2.5.5**

* **Einfügen einer partiellen Werbeunterbrechung**

   TV-ähnliche Erfahrung, in der Mitte einer Anzeige zu erscheinen, ohne die Verfolgung der teilweise überwachten Anzeige auszulösen.\
   Beispiel: Der Benutzer schließt sich in der Mitte (40 Sekunden) einer 90-Sekunden-Werbeunterbrechung an, die aus drei 30-Sekunden-Anzeigen besteht. Dies ist 10 Sekunden nach der zweiten Anzeige in der Pause.

   * Die zweite Anzeige wird während der verbleibenden Dauer (20 Sekunden) und die dritte Anzeige abgespielt.

   * Anzeigentracker für die teilweise wiedergegebene Anzeige (zweite Anzeige) werden nicht ausgelöst. Die Tracker für nur die dritte Anzeige werden ausgelöst.

* **Sicheres Laden der Anzeige über HTTPS**

   Adobe Primetime bietet eine Option zum Anfordern des ersten Aufrufs an den Primetime-Anzeigenserver und CRS über HTTPS.

* **Zu CRS-Anforderungen hinzugefügte AdSystem- und Creative-ID**

   Jetzt auch `AdSystem` und `CreativeId` als neue Parameter in den 1401- und 1403-Anforderungen.

* **API setEncodeUrlForTracking in der NetworkConfiguration-Klasse entfernt** , da die unsicheren Zeichen in einer URL kodiert werden sollten.

**Version 2.5.4**

Android TVSDK v2.5.4 Angebote mit den folgenden Aktualisierungen und API-Änderungen:

* Änderungen am Standardwert für `WebViewDebbuging`

   `WebViewDebbuging` ist standardmäßig auf `Fals`e eingestellt. Rufen Sie dazu `setWebContentsDebuggingEnabled(true)` in der Anwendung auf.

* **Aktualisierung der OpenSSL- und Curl-Version**

   Aktualisierung von libcurl auf v7.57.0 und OpenSSL auf v1.0.2k.

* Zugriff auf App-Ebene für VAST-Antwortobjekt

   Es wurde eine neue API eingeführt, `NetworkAdInfo::getVastXml()` die den Zugriff auf das VAST-Antwortobjekt auf die Anwendung ermöglicht.

**Version 2.5.3**

Android TVSDK v2.5.3 Angebot die folgenden Updates und API-Änderungen.

* Alle TVSDK-Kunden, die CRS verwenden, sollten ihre Apps mit TVSDK 2.5.3.85 oder höher auf Android aktualisieren. Dies ist eine Ablage, die die vorhandene App-Implementierung ersetzt. Überprüfen Sie nach dem TVSDK-Upgrade die kreativen URL-Anforderungen von CRS in einem Proxy-Tool (z. B.: Charles) und bestätigen Sie, dass der Hostname und die Version im Pfad sich wie in der Beispiel-URL-Struktur unten widerspiegeln.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* Benutzeragent von TVSDK anpassbar: haben wir einige neue APIs hinzugefügt, um die Benutzeragenten anzupassen.

   * `setCustomUserAgent(String value)`
   * `getCustomUserAgent()`

* Freigeben von Cookies zwischen Android-Anwendung und TVSDK: Android TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der JAVA-Ebene (gespeichert im CookieStore der Android-Anwendung) und der C++ TVSDK-Ebene. Jetzt ist es möglich, Cookies in der nativen C++-Ebene einzustellen und/oder zu ändern, da sie dem Java Cookie Store ausgesetzt werden.

* API-Änderungen:

   * Ein neues Ereignis `CookiesUpdatedEvent` wird hinzugefügt. Er wird vom Medienplayer ausgelöst, wenn sein Cookie aktualisiert wird.

   * Es wird eine neue API hinzugefügt, `NetworkConfiguration::set/ getCustomUserAgent()` um benutzerdefinierte Benutzeragenten zu verwenden.

   * Eine neue API wird hinzugefügt, um die Kodierung von unsicheren Zeichen `NetworkConfiguration::set/ getEncodedUrlForTracking` zu erzwingen.

   * Eine neue API wird hinzugefügt, `NetworkConfiguration::getNetworkDownVerificationUrl()` um im Falle eines Failover eine URL für die Netzwerküberprüfung festzulegen.

   * Eine neue Eigenschaft wird hinzugefügt, `TextFormat::treatSpaceAsAlphaNum` die definiert, ob Leerzeichen bei der Anzeige von Beschriftungen als alphanumerisch behandelt werden sollen.

* Änderungen in `SizeAvailableEvent`. Bisher wurden die Höhe `getHeight()` und die Breite des Rahmens mit `getWidth()` den Methoden `SizeAvailableEvent` in 2.5.2 zurückgegeben, die vom Medienformat zurückgegeben wurden. Jetzt gibt es Ausgabehöhe und -breite zurück, die vom Decoder zurückgegeben werden.

* Änderungen im Pufferverhalten: Das Pufferverhalten wird geändert. Es bleibt dem App-Entwickler überlassen, was er tun möchte, wenn der Puffer leer ist. 2.5.3 verwendet die Wiedergabepuffergröße bei einer leeren Puffersituation.

**Version 2.5.2**

Android TVSDK v2.5.2 Angebot wichtige Fehlerbehebungen und einige API-Änderungen.

**Version 2.5.1**

Die wichtigen neuen Funktionen, die in Android 2.5.1 veröffentlicht wurden.

* **Leistungsverbesserungen -** Die neue TVSDK 2.5.1 Architektur bringt eine Reihe von Leistungsverbesserungen. Basierend auf Statistiken aus einer Drittanbieter-Benchmarking-Studie bietet die neue Architektur eine 5fache Reduzierung der Startzeit und 3,8fache Reduzierung der Dropdown-Rahmen im Vergleich zum Branchendurchschnitt:

* **Sofort für VOD und live - Wenn Sie Sofortzugriff aktivieren, initialisiert und puffert das TVSDK Medien vor dem Beginn der Wiedergabe.** Da Sie mehrere MediaPlayerItemLoader-Instanzen gleichzeitig im Hintergrund starten können, können Sie mehrere Streams puffern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird die Wiedergabe sofort auf den Beginn des neuen Kanals wiedergegeben. TVSDK 2.5.1 unterstützt auch Instant On für **Live** Streams. Die Live-Streams werden erneut gepuffert, wenn das Live-Fenster verschoben wird.

* **Verbesserte ABR-Logik -** Die neue ABR-Logik basiert auf der Pufferlänge, der Änderungsrate der Pufferlänge und der gemessenen Bandbreite. Dadurch wird sichergestellt, dass die ABR die richtige Bitrate wählt, wenn die Bandbreite schwankt, und auch die Anzahl der auftretenden Bitratenwechsel optimiert wird, indem die Rate überwacht wird, mit der sich die Pufferlänge ändert.

* **Teilweiser Segmentdownload/Untersegmentierung - TVSDK verringert die Größe der einzelnen Fragmente weiter, um so schnell wie möglich Beginn abspielen zu können.** Das zugehörige Fragment muss alle zwei Sekunden über einen Schlüsselrahmen verfügen.

* **Verzögerte Anzeigenauflösung -** TVSDK wartet nicht auf die Auflösung von Nicht-Preroll-Anzeigen, bevor die Wiedergabe gestartet wird, wodurch die Startzeit verringert wird. APIs wie Suchen und Trick-play sind immer noch nicht zulässig, bis alle Anzeigen aufgelöst sind. Dies gilt für VOD-Streams, die mit CSAI verwendet werden. Vorgänge wie Suchen und Vorwärts sind erst nach Abschluss der Anzeigenauflösung zulässig. Bei Live-Streams kann diese Funktion nicht für die Anzeigenauflösung während eines Live-Ereignisses aktiviert werden.

* **Persistente Netzwerkverbindungen -** Diese Funktion ermöglicht es TVSDK, eine interne Liste persistenter Netzwerkverbindungen zu erstellen und zu speichern. Diese Verbindungen werden für mehrere Anforderungen wiederverwendet, anstatt für jede Netzwerkanforderung eine neue Verbindung zu öffnen und anschließend zu zerstören. Dadurch wird die Effizienz erhöht und die Latenz im Netzwerkcode verringert, was zu einer schnelleren Wiedergabe führt.
Wenn TVSDK eine Verbindung öffnet, fordert es den Server auf, eine Verbindung *aufrechtzuerhalten* . Einige Server unterstützen diese Art der Verbindung möglicherweise nicht. In diesem Fall greift TVSDK zurück, um für jede Anforderung erneut eine Verbindung herzustellen. Auch wenn persistente Verbindungen standardmäßig aktiviert sind, verfügt TVSDK jetzt über eine Konfigurationsoption, damit Apps persistente Verbindungen bei Bedarf deaktivieren können.

* **Paralleler Download -** Das parallele Herunterladen von Video und Audio statt in Serie reduziert die Startverzögerungen. Diese Funktion ermöglicht die Wiedergabe von HLS Live- und VOD-Dateien, optimiert die verfügbare Bandbreitennutzung von einem Server, verringert die Wahrscheinlichkeit, in Puffersituationen zu gelangen, und minimiert die Verzögerung zwischen Download und Wiedergabe.

* **Parallele Anzeigendownloads - TVSDKs rufen Anzeigen parallel zur Inhaltswiedergabe ab, bevor sie auf die Werbeunterbrechungen zutreffen. Dadurch wird eine nahtlose Wiedergabe von Anzeigen und Inhalten ermöglicht.**

* **Wiedergabe**

* **MP4 Content Play-back -** MP4-Kurzclips müssen nicht neu transkodiert werden, um innerhalb von TVSDK wiedergegeben zu werden.

   > [!NOTE]
   >
   > ABR-Switching, Trick Play, Anzeigeneinfügung, späte Audiobindung und Untersegmentierung werden für die MP4-Wiedergabe nicht unterstützt.

* **Trick play with adaptive bit rate (ABR) -** Diese Funktion ermöglicht TVSDK, während der Trick Play-Modus zwischen iFrame-Streams zu wechseln. Sie können Profil ohne iFrame verwenden, um Tricks mit geringeren Geschwindigkeiten auszuführen.

* **Glättere Trick-Wiedergabe -** Diese Verbesserungen verbessern die Benutzerfreundlichkeit:

   * Adaptive Auswahl der Bitrate und Bildrate während der Trick-Wiedergabe, basierend auf Profil von Bandbreite und Puffer

   * Verwendung des Hauptstreams anstelle des IDR-Streams, um eine schnelle Wiedergabe mit bis zu 30 fps zu erzielen.

* **Inhaltsschutz**

   * **Auflösungsbasierter Ausgabeschutz -** Diese Funktion verknüpft Wiedergabebeschränkungen mit bestimmten Auflösungen und bietet feinere DRM-Steuerelemente.

* **Workflow-Unterstützung**

   * **Integration der direkten Rechnungsstellung -** Hiermit werden Rechnungsmetriken an das Adobe Analytics-Back-End gesendet, das von Adobe Primetime für vom Kunden verwendete Streams zertifiziert wurde.
   TVSDK sammelt automatisch Metriken, wobei der Kaufvertrag des Kunden eingehalten wird, um regelmäßige Nutzungsberichte zu erstellen, die für die Abrechnung erforderlich sind. Auf jedem Stream-Beginn-Ereignis verwendet TVSDK die Adobe Analytics-Dateneinfüge-API, um Rechnungsmetriken wie Inhaltstyp, durch Anzeigeneinfügung aktivierte Flags und DRM-aktivierte Flags - je nach Dauer des abrechnungsfähigen Streams - an die Adobe Analytics Primetime-Report Suite zu senden. Dies beeinträchtigt oder wird nicht in die eigenen Adobe Analytics Report Suites oder Server-Aufrufe des Kunden aufgenommen. Auf Anfrage wird dieser Bericht zur Rechnungsnutzung regelmäßig an Kunden gesendet. Dies ist die erste Phase der Abrechnungsfunktion, die nur die Nutzungsabrechnung unterstützt. Sie kann mithilfe der in der Dokumentation beschriebenen APIs auf Grundlage des Kaufvertrags konfiguriert werden. Diese Funktion ist standardmäßig aktiviert. Um diese Funktion zu deaktivieren, lesen Sie das Referenz-Player-Beispiel.

   * **Verbesserte Failover-Unterstützung -** Zusätzliche Strategien wurden implementiert, um die unterbrechungsfreie Wiedergabe fortzusetzen, obwohl Host-Server, Wiedergabelistendateien und Segmente ausfallen.


* **Werbung**

   * **Moat-Integration -** Unterstützung für Anzeigenanzeigbarkeitsmessung von Moat.

   * **Begleitbanner -** Neben einer linearen Anzeige werden begleitende Banner angezeigt, die nach dem Ende der Anzeige oft auf der Ansicht angezeigt werden. Diese Banner können vom Typ &quot;html&quot;(ein HTML-Snippet) oder &quot;iframe&quot;(eine URL zu einer iframe-Seite) sein.

* **Analytics**

   * **VHL 2.0 -** Dies ist die neueste optimierte VHL-Integration (Video Heartbeats Library) für die automatische Erfassung von Nutzungsdaten für Adobe Analytics. Die Komplexität der APIs wurde verringert, um die Implementierung zu erleichtern. Laden Sie die VHL-Bibliothek [v2.0.0 für Android](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) herunter und extrahieren Sie die JAR-Datei im Ordner libs.

* **SizeAvaliableEventListener**

   * `getHeight()` und `getWidth()` Methoden von `SizeAvailableEvent` gibt nun Ausgabe in Höhe und Breite zurück. Das Anzeigeseitenverhältnis kann wie folgt berechnet werden:

      ```java
      SizeAvailableEvent e;
      DAR = e.getWidth()/ e.getHeight();
      ```

      Das Seitenverhältnis der Datenspeicherung in Bezug auf die Breite und Höhe der Breite kann auch zur Berechnung der Rahmenbreite und -höhe verwendet werden:

      ```java
      SAR = e.getSarWidth()/e.getSarHeight();
      frameHeight = e.getHeight();
      frameWidth = e.getWidth()/SAR;
      ```

* **Cookies**

   * Android TVSDK unterstützt jetzt den Zugriff auf JAVA-Cookies, die im CookieStore der Android-Anwendung gespeichert sind. Eine Callback-API (onCookiesUpdated) wird bereitgestellt, um aufzuzeichnen, wann immer ein neues Cookie als Teil des **Set-Cookie** Response-Headers erscheint. Diese Cookies stehen als Liste von HttpCookie(s) zur Verfügung, die für eine andere URI/Domäne verwendet werden, indem diese Cookie-Werte mithilfe von CookieStore für diese bestimmte URI/Domäne festgelegt werden. Gleichermaßen werden die Cookie-Werte in TVSDK mithilfe der CookieStore Add-API aktualisiert.

## Funktionsmatrix {#feature-matrix}

TVSDK für Android unterstützt eine Reihe von Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.

In den unten stehenden Funktionstabellen gibt ein &quot;Y&quot;an, dass die Funktion in der aktuellen Version unterstützt wird.

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | VOD + Live | Y |
| FER - Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | FER VOD | Y |
| Suchen, wann eine Anzeige abgespielt wird | VOD + Live | Nicht unterstützt |
| HEVC-Wiedergabe | VOD + Live | Nur fMP4-Container |
| AC3 und EAC3 | VOD + Live | Nicht unterstützt |
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
| Unterstützung für benutzerdefinierte HTTP-Kopfzeilen | VOD + Live | Y (Whitelist erforderlich) |
| Puffersteuerungsparameter festlegen | VOD + Live | Y |
| Festlegen der Steuerelemente für adaptive Bitraten | VOD + Live | Y |
| Benutzerdefinierte Manifest-Tags | VOD + Live | Y |
| Verspätete Audiobindung | VOD + Live | Y |
| 302 Umleitung | VOD + Live | Y |
| Wiedergabe mit Versatz | VOD + Live | Y |
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
| Einfügen eines Teilformulars mit Werbeunterbrechung | Live | Y |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| AES-Verschlüsselung | VOD + Live | Y |
| Beispiel-AES-Verschlüsselung | VOD + Live | Y |
| Tokenisierte Streams | VOD + Live | Y |
| Widevine DRM | VOD + Live | Nur fMP4-Container |
| Primetime DRM | VOD + Live | Y |
| Externe Wiedergabe (RBOP) | VOD + Live | Nur Primetime-DRM |
| Lizenzdrehung | VOD + Live | Nur Primetime-DRM |
| Schlüsseldrehung | VOD + Live | Nur Primetime-DRM |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Adobe Analytics VHL-Integration | VOD + Live | Y |
| Rechnungsstellung | VOD + Live | Y |

## Behobene Probleme {#resolved-issues}

Wenn die Auflösung mit einem gemeldeten Problem verbunden ist, wird ein Zendesk-Verweis angezeigt, z. B. ZD#xxxxx.

**Android TVSDK 3.12**

Dieser Abschnitt enthält eine Zusammenfassung des Problems, das in der TVSDK 3.12-Android-Version behoben wurde.

* ZD#40584 - Die Primetime-Referenz-App wird nicht mit der neuesten Gradle-Version erstellt.

### Behobene Probleme in früheren Versionen

**Android TVSDK 3.11**

* ZD#41252 - Koreanische Zeichen in WebVTT, die nach Android 7.1 beschädigt wurden.

**Android TVSDK 3.10**

* ZD#40340 - Anwendungsabstürze mit dem Fehler &quot;App reagiert nicht&quot;beim Versuch der Wiedergabe nach der Blacklist aller TS-(TypeScript-)Dateien.

**Android TVSDK 3.8**

* Keine neuen Ausgaben hinzugefügt.

**Android TVSDK 3.7**

* Keine neuen Ausgaben hinzugefügt.

**Android TVSDK 3.6**

* Keine neuen Ausgaben hinzugefügt.

**Version 3.5**

* ZD#37503 - JSON-Antworten für die CRS-Regeln werden zwischengespeichert, um die Duplikat-Anforderungen zu vermeiden.

**Version 3.4**

* ZD#37996 - Es wurde ein Problem mit der abgeschnittenen Wiedergabe von linearen und VOD-CMAF-HEVC-Streams behoben.
* ZD#37706 - Es wurde ein Problem mit beschädigten Beschriftungen behoben.
* ZD#37622 - Es wurde ein Problem mit tödlichen URISyntaxErrors für bestimmte Anzeigen behoben.
* ZD#36938 - Es wurde ein Problem behoben, bei dem die Bitrate nach unten zur mittleren Bitrate und dann nach oben zur höchsten Bitrate wechselte, nachdem die Trick-Wiedergabe beendet wurde.

**Version 3.3**

* ZD#37394 - CMAF-Assets mit hoher Geschwindigkeit werden nach der Geschwindigkeitsänderung zu Artefakten.
   * Es wurde ein Problem behoben, das bei einer Änderung des Profils während der Trickwiedergabe auftrat.
* ZD#37396 - Ereignisse zur Anzeigenverfolgung fehlen für einige Mitterrollen und Post-Roll-Rollen.
   * Es wurde ein spezifischer Fall bei Ereignissen zur Anzeigenverfolgung behoben.
* ZD#37491 - HTTP-Statuscode mit Fehlermeta ist nicht vorhanden.
   * Es wurde daran gearbeitet, Netzwerkfehler im Stapel zu verbreiten.
* ZD#37808 - Whitelist Neue benutzerdefinierte Kopfzeile.
   * SSAI_TAG-Unterstützung als Teil dieser Korrektur hinzugefügt.
* ZD#37622 - URISyntax-Fehler von bestimmten Anzeigen-Pods.
   * Es wurde ein Problem mit dem Absturz der Stream-Wiedergabe behoben, der auftrat, wenn eine benutzerdefinierte Android-App mit einer nicht kodierten % bereitgestellt wurde
* ZD#37631 - Master-Manifestwiederholungsmechanismus für Android TVSDK.
   * Neue API in der Netzwerkkonfiguration für die Bearbeitung dieser Verbesserung hinzugefügt. Wenn diese API nicht verwendet wird, wird das Manifest nicht erneut versucht. Wenn es verwendet wird, wird manifest erneut versucht, um Netzwerkfehler und Timeouts zu verarbeiten.

**Version 3.2**

* ZD#37493- Tracking-Beacons für die Live-Wiedergabe werden nicht zeitweise für die erste Anzeige in der Sequenz ausgelöst.
* ZD#36985- Tracking-Beacons werden nicht für leere Werbeunterbrechungen in der VMAP-Antwort gesendet.
* ZD#37134 - TVSDK gibt gelegentlich die falsche ID für die VMAP-Antwort aus.

**Version 3.0**

* ZD#33740 - TVSDK gibt unmittelbar nach dem Erstellen eines MediaPlayer-Objekts und dem Aufrufen von replaceCurrentResource() eine nicht benötigte Warnung aus

   * Die frühere Korrektur wurde verbessert, indem die Wiederherstellung nur dann aufgerufen wurde, wenn der Player im Status &quot;Beendet&quot;ist

* ZD#36442 - Jede neue Wiedergabe trennt die Remotedebugingsitzung, wodurch das Debugging unmöglich wird.

   * Debug ist auf der Web-Ansicht standardmäßig nicht möglich, da das Debugging nicht standardmäßig aktiviert ist. App sollte das Debugging aktivieren, wenn dies erforderlich ist, indem setWebContentsDebuggingEnabled(true) für ein Objekt aufgerufen wird, das von MediaPlayer.getCustomAdView() zurückgegeben wird.

* ZD#33688 - Unterstützung für Just-in-Time und Auflösung

   * Werbeunterbrechungen werden in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst.

* ZD#36441 - Die Dauer des Live-Fensters nimmt über 5 Minuten hinaus zu und verursacht mehrere Probleme.

   * Es wurde ein Problem behoben, bei dem VirtualStartTime zweimal hinzugefügt wurde, während der virtuelle Live-Point berechnet wurde, was zu diesem Problem führte.

**Android TVSDK 2.5.6**

* ZD #34992 - Die Sprache ist in &quot;Untertitel&quot;leer.

   * Es wurde ein Fall behoben, bei dem TVSDK #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS vom Hauptmanifest nicht analysiert hat, um die Details der Untertitel-Verfolgung abzurufen.

* ZD #35078 - Android P-Überprüfung.

   * TVSDK 2.5.6 wurde mit den neuesten Android P Beta-Builds validiert. Aufgrund des neuen Android-Betriebssystems wurden keine Probleme gefunden.

* ZD #34149 - Player fordert weiterhin Manifeste an, auch wenn ein Fehler aufgetreten ist.

   * Korrektur des Problems, bei dem TVSDK wiederholende Aufrufe tätigte, selbst wenn alle Profil ausfielen (404-Fehler).

* ZD #31533 - Audiowiedergabe auf Android, nachdem die App in den Hintergrund gesendet wurde.

   * Es wurde `enableAudioPlaybackInBackground` API von MediaPlayer hinzugefügt, die mit &quot;True&quot;als Argument aufgerufen werden sollte (wenn der Player den Status &quot;VORBEREITET&quot;aufweist), um die Wiedergabe von Audio zu aktivieren, wenn die App im Hintergrund ausgeführt wird.

**Android TVSDK 2.5.5**

* ZD #21647 - Android TVSDK benachrichtigt 640 x 368, wenn die tatsächliche Videogröße 640 x 360 beträgt.

   * Aufgrund der Variablen m_nOutputHeight (innerhalb von AndroidMCVideoDecoder) wird eine Aktualisierung mit der Rahmenhöhe anstelle der tatsächlichen Ausgabehöhe vorgenommen. Es wurden relevante Änderungen an der Funktion getVideoFrame vorgenommen, um m_nOutputHeight korrekt zu berechnen.

* ZD #26614 - Urgent - Drittanbieter-Ad-Serving / Programmatic - Misserfolgen von Impressionen.

   * Die frühere Korrektur wurde verbessert, indem die Groß-/Kleinschreibung bei der XML-Analyse behandelt wurde, bei der das Problem reproduzierbar war, wenn &quot;space&quot;vor dem Gleichheitszeichen wie &lt;VAST-Version =&quot;2.0&quot;> liegt

* ZD #29296 - Android: Hinzufügen von AdSystem- und Creative-ID für CRS-Anforderungen.

   * Jetzt einschließlich &#39;AdSystem&#39; und &#39;CreativeId&#39; als neue Parameter in den Anforderungen 1401 und 1403.

* ZD #33062 - TVSDK stürzt beim Auftreten von Pipe-Zeichen in VAST-Antwort unter CDATA-Knoten ab

   * API setEncodeUrlForTracking in der NetworkConfiguration-Klasse wurde als unsichere Zeichen in einer URL entfernt, die kodiert werden soll

* ZD #33063 - CRS Dateiauswahllogik beschädigt - TVSDK sendete keine CRS-Anforderung für Webm-Format, sondern schickte sie stattdessen für 3gpp-Dateien.

   * Die Logik wurde jetzt behoben. Bei der Verwendung von Mediendateien mit Webm und 3gpp-Format wird eine CRS-Anforderung für Webm gesendet. Bei Verwendung beider Mediendateien im 3gpp-Format muss die CRS-Anforderung für die höchste Bitrate-3-gpp-Datei gesendet werden.

* ZD #33125 - Die Android-App stürzt mit einem bestimmten DoubleClick-Tag innerhalb des VMAP ab.

   * Korrektur des Szenarios zur Vermeidung des Absturzes.

* ZD #32256 - Problem mit Lizenzrotation und Schlüsseldrehung - Adobe Access

   * Die Segmentinitialisierung mit den DRM-Metadaten für SampleAES-Inhalte wurde korrigiert. Funktioniert einwandfrei mit AES128-Inhalten.

* ZD #33619 - Schnelles Weiterleiten eines wachsenden Playlist-Inhalts, der im Pufferzustand nahe dem Live Point feststeckt.

   * Handle des Gehäuses beim Überqueren des Live-Points im Trick Play-Modus

* ZD #34151 - TimedMetadata-Objekte nicht in der Reihenfolge.

   * Zwei TimedMetadata-Ereignis wurden in zufälliger Reihenfolge angezeigt, wenn sie zur selben Zeit in der Zeitleiste gehörten. Ihre ursprüngliche Reihenfolge wurde manifest beibehalten.

* ZD #34189 - Problem beim Suchen nach Beginn der Werbeunterbrechung.

   * Das Problem betraf SSAI-Anzeigen, die mit Diskontinuität verbunden werden. Und die Ursache war ein Verhalten, wenn wir versuchen, solche Anzeigen zu beginnen, suchen wir nach einem Keyframe und wir finden es nicht. Der Grund dafür war, dass der Mindest-Audio-Zeitstempel der Anzeige vor dem Mindest-Video-Zeitstempel lag. Daher suchen wir am Ende nach einem Schlüsselbild mit falschen fragmentDump-Daten. Jetzt behoben.

* ZD #34528 - Videoauflösung, die auf einem 3rd-gen-Dongle von FireTV nicht über 640 x 360 aktualisiert wird.

   * Die Fehlerbehebung wurde dahingehend verbessert, dass sie die neuesten Firmware-Updates enthält

* ZD #34793 - TVSDK 2.5.x führte in einigen Fällen zu Abstürzen mit dem benutzerdefinierten Content-Auflöser, wenn VideoEngine davon ausging, dass die auditudeSettings verfügbar sind und nicht.

   * Der Absturz ereignete sich aufgrund eines Funktionsaufrufs an einem Null-freigegebenen Zeiger (auditudeSettings). Es wurde eine bedingte Prüfung in VideoEngineTimeline::placeToSourceTimeline() hinzugefügt, um sicherzustellen, dass auditudeSettings verfügbar sind, bevor irgendetwas für dieses Objekt aufgerufen wird.

* ZD #32584 - Kein Zugriff auf vollständige Informationen im Knoten &lt;Erweiterungen> einer VAST-Antwort möglich.

   * Korrektur des Problems mit der XML-Analyse, und nun stellt NetworkAdInfo die vollständigen Informationen bereit, die im Knoten &lt;Erweiterungen> vorhanden sind

* ZD #35086 - Bei bestimmten VMAP-Antworten werden keine vollständigen Erweiterungsdaten vom Player abgerufen.

   * Das Problem war spezifisch für die Erweiterung XML, da die XML-Analyse nicht funktionierte, wenn die Erweiterung XML Dubletten-Anführungszeichen im Attributwert enthielt. Korrektur des Problems.

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Wiedergabesitzung zur Aktivierung des Remotedebuggens von Webansicht.

WebViewDebbuging ist standardmäßig auf False eingestellt. Um das Debugging zu aktivieren, legen Sie mithilfe von setWebContentsDebuggingEnabled(true) als true über die Anwendung fest.

* ZenDesk#33011 - Die Anzeigenzeitschiene wird nicht aufgelöst, wenn eine CRS-Anforderung fehlschlägt.

   Wenn eine CRS-Anforderung an eine Anzeige fehlschlägt, wird die Zeitschiene gelöst und die verbleibenden Anzeigen werden wiedergegeben.

* ZenDesk#34528 - Die Videoauflösung wird auf einem Dongle der dritten Generation von FireTV nicht über 640 x 360 aktualisiert.

   Die Videoauflösung schaltet sich als Bitratenwechsel nach oben.

* ZenDesk#33192 - AudioTrack hat einen Null-Namen, wenn die Spur über AudioUpdatedEventListener::onAudioUpdated abgerufen wird.

   In einigen Szenarien beim FireTV-Stick wurde onAudioUpdate-Ereignis ausgelöst, wenn es kein aktuelles Audio-Update gab. Das wurde jetzt behoben.

**Android TVSDK 2.5.3**

* Zendesk#32216 - Benutzerdefiniertes TimedMetadata-Tag-Abonnement funktioniert nicht.

   Wir geben ID3-Daten als Byte-Array (zur Unterstützung von APIC- oder generischen Daten) an den Client zurück, während in 1.4 die Rückgabestaste angegeben ist. Das Byte-Array behandelt kein mit null beendetes Zeichen selbst, daher zeigte es dem Client Sonderzeichen an. Dieses Problem wurde jetzt behoben.
* Zendesk#32670 - Player, der nicht zu Redundant Playlist überspringt

   Dies funktioniert jetzt einwandfrei und setNetworkDownVerificationUrl funktioniert erwartungsgemäß.
* Zendesk#32369 - Die Bildunterschrift weist einen anderen Farbabfall oder ein anderes Artefakt auf.

   Problem mit CC-Fehlern wurde im letzten Build behoben
* Zendesk#25590 - Verbesserung: TVSDK-Cookie-Store ( C++ zu JAVA)

   Android TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der JAVA-Ebene (gespeichert im CookieStore der Android-Anwendung) und der C++ TVSDK-Ebene.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 hat offenbar keine Fehlerbehebung für PTPLAY-20269

   Dieses Problem wurde behoben und in den Zweig 2.5.2 integriert.
* Zendesk#31806 - Auditude sticks bei der Vorbereitung

   Player war im Vorbereitungszustand hängen geblieben, da response xml ein leeres Tag enthielt. Das Problem wurde nun behoben.
* Zendesk#31727 - TVSDK 2.5 Untertitel werden abgelegt oder falsch geschrieben.

   Das Problem wurde behoben, und es werden keine Zeichen abgelegt/falsch geschrieben.
* Zendesk#31485 - DrmManager in 2.5

   Es ist ein Problem beim Erstellen von DRMManager über den neuen DRMManager(Kontext) aufgetreten. Die DRMService-Klasse wurde implementiert, die DRMManager bereitstellen würde.
* Zendesk#32794- 1080P-Auflösungsstream wird nicht auf Android wiedergegeben

   haben wir die Methoden SizeAvailableEvent und Previous, getHeight() und getWidth() von SizeAvailableEvent in 2.5 geändert, die verwendet wurden, um Frame-Höhe und Frame-Breite zurückzugeben, die vom Medienformat zurückgegeben wurden. Es gibt nun Ausgabehöhe und -breite zurück, die vom Decoder zurückgegeben werden.
* Zendesk #19359 Flash Player stürzt aufgrund der Position des Attributs #EXT-X-FAXS-CM im Manifest auf Einstellungsebene ab.

   Das Tag #EXT-X-FAXS-CM muss immer in der oberen Wiedergabeliste angezeigt werden, bevor einzelne Bitraten oder Segmente in der Wiedergabeliste angezeigt werden.

**Android TVSDK 2.5.2**

* Zendesk#17305 Artefakte in geschlossenen Bildunterschriften mit undurchsichtigem Hintergrund.

   setTreatSpaceAsAlphaNum-Eigenschaft in TextFormat verfügbar ist. Standardmäßig ist die Eigenschaft false. Legen Sie die Eigenschaft in einem Client auf &quot;True&quot;fest, um das Problem mit dem dunklen Bereich zu beheben.

* Zendesk#25097 CC-Anzeige hat visuelle Artefakte mit CC-Einstellungen.

   setTreatSpaceAsAlphaNum-Eigenschaft in TextFormat verfügbar ist. Standardmäßig ist die Eigenschaft false. Legen Sie die Eigenschaft in einem Client auf &quot;True&quot;fest, um das Problem mit dem dunklen Bereich zu beheben.

* Zendesk #31620 Die Benutzeragenten-Zeichenfolge, die aus dem TVSDK-Player entfernt wird, wird abgeschnitten.

   Die Benutzeragenten-Zeichenfolge wird nach 128 Zeichen nicht mehr abgeschnitten.

   Adobe Primetime-Versionszeichenfolge wird dem Systembenutzer-Agent hinzugefügt.

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

**Android TVSDK 3.11**

* Keine neuen Einschränkungen hinzugefügt.

### Bekannte Probleme und Einschränkungen in früheren Versionen

**Android TVSDK 3.10**

* Keine neuen Einschränkungen hinzugefügt.

**Android TVSDK 3.8**

* Keine neuen Einschränkungen hinzugefügt.

**Android TVSDK 3.7**

* Keine neuen Einschränkungen hinzugefügt.

**Android TVSDK 3.6**

* Keine neuen Einschränkungen hinzugefügt.

**Android TVSDK 3.5**

* Keine neue Einschränkung hinzugefügt.

**Android TVSDK 3.4**

* ID3, Untertitel, Unterstützung für Spätbindung Audio wurde für den CMAF-Stream (CBC) nicht überprüft.
* Auf einigen Geräten tritt ein Problem mit der geringen Reproduzierbarkeit auf, aufgrund dessen Videoverzerrungen bei der Trick-Wiedergabe in CMAF-Streams oben angezeigt werden können.

**Android TVSDK 3.3**

* clcp:c608 Beschriftungen werden für die Wiedergabe des CMAF-Streams nicht unterstützt.

**Android TVSDK 3.2**

* TVSDK 3.2 unterstützt keine CMAF Sample AES- und AES128-Streams-Wiedergabe.
* HEVC-CMAF-Streams bieten keine Unterstützung für die Wiedergabe von Untertiteln.
* Bei WV-verschlüsselten Streams wird eine grüne Färbung angezeigt, wenn die Suche um das nicht verschlüsselte Segment durchgeführt wird.
* CMAF-Streams unterstützen keine ID3-Ereignis.
* HLS-Streams unterstützen kein TTML-Untertitelformat.

**Android TVSDK 3.0**

* Die HEVC-Unterstützung weist in dieser Version folgende Einschränkungen auf

   * DRM wird nicht unterstützt
   * CC-Unterstützung (CEA 608/708) nicht überprüft
   * 4K-Unterstützung ist noch nicht vorhanden
   * Unterstützung für ID3-Tags nicht bestätigt

* Bei Ereignisse zum Anzeigenfortschritt spiegelt die Zeitleiste möglicherweise nicht die 100%ige Wiedergabedauer der Anzeige wider. Als Workaround können Sie `adcompleteevent` den Abschluss der Anzeigenwiedergabe kennen und die Benutzeroberfläche für verschiedene Zwecke aktualisieren, z. B. zum Aktualisieren der Zeitleiste, Entfernen der anzeigenbezogenen Benutzeroberfläche usw.
* Die von VMAP zurückgegebenen unzähligen Anzeigenaufrufe berücksichtigen nicht die Just-in-Time-Lookahead-Position.

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

* [Systemanforderungen](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-requirements.html)
* [TVSDK 3.10 für Android-Programmierhandbuch](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-overview-prod-audience-guide.html)
* [TVSDK Android Javadoc für API-Referenz](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [TVSDK Android C++ API-Dokument](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html) - Jede Java-Klasse verfügt über eine entsprechende C++-Klasse. Die C++-Dokumentation enthält mehr erklärende Informationen als die JavaScript-Dateien. In der C++-Dokumentation finden Sie daher ein tiefergehendes Verständnis der Java-API.
* [TVSDK 1.4 bis 2.5 für Android (Java)-Migrationshandbuch](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* Informationen zum Bearbeiten von Bildschirm-Ein-/Ausschalten-Szenarios finden Sie in der im Build enthaltenen `Application_Changes_for_Screen_On_Off.pdf` Datei.
* Siehe vollständige Hilfedokumentation auf der Seite &quot; [Adobe Primetime - Training und Support](https://helpx.adobe.com/support/primetime.html) &quot;.
