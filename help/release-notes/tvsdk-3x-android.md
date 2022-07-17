---
title: TVSDK 3.15 für Android - Versionshinweise
description: TVSDK 3.15 für Android - Versionshinweise beschreiben die neuen oder geänderten Funktionen, die gelösten und bekannten Probleme und die Geräteprobleme in TVSDK Android 3.15.
products: SG_PRIMETIME
topic-tags: release-notes
exl-id: cd2c64ef-dd42-4dc2-805f-eeb64a8a53d9
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '5516'
ht-degree: 0%

---

# TVSDK 3.15 für Android - Versionshinweise {#tvsdk-for-android-release-notes}

TVSDK 3.15 für Android - Versionshinweise beschreiben die neuen oder geänderten Funktionen, die gelösten und bekannten Probleme und die Geräteprobleme in TVSDK Android 3.15.

Der Android-Referenz-Player ist im Verzeichnis &quot;samples/&quot;Ihrer Distribution im Android TVSDK enthalten. In der zugehörigen Datei README.md wird erläutert, wie der Referenz-Player erstellt wird.

>[!NOTE]
>
>Um den Referenz-Player erfolgreich zu erstellen, wie in der mit der -Version verteilten README.md beschrieben, gehen Sie folgendermaßen vor:
>
>1. VideoHeartbeat.jar von herunterladen [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) (VideoHeartbeat-Bibliothek für Android v2.0.0)
>1. Extrahieren Sie VideoHeartbeat.jar in den Ordner libs/ .


TVSDK für Android bietet im Vergleich zu früheren Versionen viele Leistungsverbesserungen. Es bietet ein hochwertiges Anzeigeerlebnis und verfügt über alle Funktionen von Version 1.4, mit Ausnahme von Multi-CDN-Unterstützung.

Die umfassenden Funktionen, die unterstützt und nicht unterstützt werden, finden Sie im Abschnitt [Funktionsmatrix](#feature-matrix) Abschnitt der Versionshinweise.

## Android TVSDK 3.15

Diese Version behebt das Problem, dass die Anwendung mehrmals abstürzt, wenn ein Creative-Tag fehlt oder wenn [!UICONTROL url CDATA] ist leer in [!UICONTROL VAST] Antwort.

Informationen zu den Fehlerbehebungen in dieser und früheren Versionen finden Sie unter [In TVSDK für Android behobene Probleme](#resolved-issueszd).

### Neue Funktionen und Verbesserungen in den vorherigen Versionen

**Android TVSDK 3.14**

Diese Version behebt das Problem, dass die Anwendung abstürzt, wenn [!UICONTROL CDATA] -Knoten ist für jeden der [!UICONTROL ClickTracking], [!UICONTROL CustomClick] oder [!UICONTROL CompanionClickTracking] -Elemente in der VAST-Antwort.

**Android TVSDK 3.13**

Der weitläufige DRM-Stream friert bzw. zeigt schwarze Rahmen auf ABR-Switches auf FireTV-Geräten an, darunter Geräte der dritten Generation von Fire TV Pendant und Fire TV Cube der 1. und 2. Generation.

Um das Problem zu beheben, legen Sie die API fest `MediaPlayer.flushVideoDecoderOnHeaderChange(true)` für die angegebenen Fire TV-Geräte vor dem Start der Wiedergabe. Der Standardwert ist &quot;false&quot;.

**Android TVSDK 3.12**

Die Gradle-Version der Primetime Reference-Anwendung wurde auf Version 5.6.4 aktualisiert.

Um die Referenz-App mit Android Studio einzurichten und auszuführen, befolgen Sie die Anweisungen aus der ReadMe-Datei, die mit TVSDK zip verfügbar ist unter `TVSDK_Android_x.x.x.x/samples/PrimetimeReference/src/README.md`.

Die wichtigsten in der aktuellen Version behobenen Kundenprobleme werden im Abschnitt [gelöste Probleme](#resolved-issues) Abschnitt.

**Android TVSDK 3.11**

* **Box-Abruf für PSSH (Protection System Specific Header) zulässig** - TVSDK ermöglicht das Abrufen des Schutzsystem-spezifischen Header-Felds, das mit der aktuell geladenen Medienressource verknüpft ist. Neue API `getPSSH()` hinzugefügt `com.adobe.mediacore.drm.DRMManager`.

Weitere Informationen finden Sie unter [Widevine DRM](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md).

**Android TVSDK 3.10**

Die Version konzentrierte sich auf die Behebung der wichtigsten Kundenprobleme, wie in [gelöste Probleme](#resolved-issues) Abschnitt.

**Android TVSDK 3.9**

* **Sichere Bereitstellung über HTTPS** - Android TVSDK 3.9 führte die sicheren Bereitstellungsfunktionen über HTTPS ein, um Inhalte sicher und mit beispielloser Skalierung und Leistung bereitzustellen.

   Um eine sichere Bereitstellung über HTTPS zu ermöglichen, wurde eine neue API in `NetworkConfiguration` -Klasse.

   `public void setForceHTTPS (boolean value)`

   `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **Unterstützung vor der Rollout mit der Funktion &quot;Teil-Werbeunterbrechung&quot;** - Mit dieser Verbesserung unterstützt TVSDK 3.8 Pre-Roll-Anzeigen mit PABI (Teil Ad-Break Feature).

Die Pre-Roll-Anzeige wird wiedergegeben, sofern verfügbar, und dann wird der Inhalt ab dem Live-Point wiedergegeben, der das Erlebnis des Live-Fernsehens emuliert.

**Android TVSDK 3.7**

* Für umfangreiche Testinhalte eine neue API `setMediaDrmCallback` in der DRMManager-Klasse bereitgestellt wird, um die Standardimplementierung der MediaDRMCallback-Schnittstelle zu überschreiben.

   `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* AppCrash-Fehler behoben, aufgrund dessen AppCrash nicht verarbeitet wurde `MediaPlayerEvent.ITEM_UPDATED` in der C++-Schicht (Android 64 Bit).

**Android TVSDK 3.6**

* **Erweitern Ihrer Apps für die 64-Bit-Anforderung** - Die native Bibliothek `(libAVEAndroid.so)` wurde aktualisiert und in zwei Versionen verfügbar gemacht. Der vorhandene native Speicherort der Armeabi-Bibliothek (32 Bit) wurde von `/framework/Player to /framework/Player/armeabi` und eine zusätzliche arm64-v8a-Bibliothek (64 Bit) in `/framework/Player/arm64-v8a.`

**Version 3.5**

* **Just-in-time-Anzeigenauflösung** - TVSDK 3.5 entfernt die Unterstützung der wiedergegebenen Anzeigen aus der Timeline.

* **Unterstützung für Offline-Wiedergabe aktiviert** - Bei der Offline-Wiedergabe können Benutzer jetzt Videoinhalte auf ihre Geräte herunterladen und sie ansehen, wenn sie nicht angemeldet sind. Detaillierte Informationen finden Sie unter[Offline-Wiedergabe mit Android](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf).&quot;

**Version 3.4**

* TVSDK unterstützt jetzt die Wiedergabe von CMAF-Streams für CBC-verschlüsselte und einfache Streams.

**Version 3.3**

* **API-Änderungen**

   * Eine neue API wird hinzugefügt zu `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` um Netzwerkfehler und Zeitüberschreitungen zu verarbeiten.
      * wobei (n) die Anzahl der weiteren Versuche ist.

**Version 3.2**

* **Unterstützung für parallele Anzeigenauflösung und Manifestdownload**

   * TVSDK 3.2 unterstützt die gleichzeitige Auflösung anstelle der sequenziellen Auflösung für alle Anzeigen-Anfragen und Werbeunterbrechungen außer VMAP.

   * Alle Anzeigenmanifeste in einer Werbeunterbrechung werden gleichzeitig heruntergeladen.

* **Unterstützung für Anzeigenauflösung und Manifestdownload-Timeout.**

   * Benutzer können jetzt den Timeout-Wert für die allgemeine Anzeigenauflösung und Manifestdownloads festlegen.  Im Fall von VMAP gilt der Timeout-Wert für einzelne Werbeunterbrechungen, da alle Werbeunterbrechungen sequenziell aufgelöst werden.

* **Neue APIs in der AdvertisingMetadata-Klasse eingeführt:**

   * `void setAdResolutionTimeout(int adResolutionTimeout)`

   * `int getAdResolutionTimeout()`

   * `void setAdManifestTimeout(int adManifestTimeout)`

   * `int getAdManifestTimeout()`

* **Unter den APIs aus der AdvertisingMetadata-Klasse entfernt:**

   * `void setAdRequestTimeout(int adRequestTimeout)`

   * `int getAdRequestTimeout()`

* **Aktivierung der Wiedergabe von Streams mit AC3/EAC3-Audio-Codec**

   * `void alwaysUseAC3OnSupportedDevices(boolean val)` in `MediaPlayer` class

* **TVSDK unterstützt die Wiedergabe von CMAF- und Nur-Streams für verschlüsselte Widevine CTR.**

* **Die Wiedergabe von 4K HEVC-Streams wird jetzt unterstützt.**

* **Parallel-Anzeigenaufrufanforderungen** - TVSDK ruft jetzt 20 Anfragen für Anzeigenaufrufe parallel vor.

**Version 3.0**

* **TVSDK 3.0 unterstützt HEVC-Streams (High Efficiency Video Coding).**

* **Just in Time - Beheben von Anzeigen, die näher an Anzeigenmarken liegen**
Die verzögerte Anzeigenauflösung löst jetzt jede Werbeunterbrechung unabhängig voneinander. Zuvor war die Anzeigenauflösung ein zweistufiger Ansatz: Pre-Roll-Slots wurden vor dem Start der Wiedergabe aufgelöst und alle Mid-/Post-Roll-Slots nach dem Start der Wiedergabe kombiniert. Mit dieser verbesserten Funktion wird jede Werbeunterbrechung jetzt zu einem bestimmten Zeitpunkt vor dem Anzeigen-Cue-Punkt aufgelöst.

>[!NOTE]
>
>Die verzögerte Anzeigenauflösung wurde jetzt standardmäßig deaktiviert und muss explizit aktiviert werden.

Eine neue API wird hinzugefügt zu `AdvertisingMetadata::setDelayAdLoadingTolerance` , um die mit diesen Advertising-Metadaten verknüpfte Toleranz beim verzögerten Laden der Anzeige zu erhalten.\
Die Suche ist jetzt unmittelbar nach der Vorbereitung zulässig. Das Suchen über Werbeunterbrechungen führt zu einer sofortigen Lösung, bevor die Suche abgeschlossen ist.\
Signaturmodi `SERVER_MAP` und `MANIFEST_CUES` werden unterstützt.

Weitere Informationen finden Sie unter [TVSDK 3.0 für Android-Programmierhandbuch](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/c-lazy-ad-resolving.md) bei API- und Ereignisänderungen.

* **Aktualisiert `targetSdkVersion` der neuesten Version**

Aktualisiert `targetSdkVersion` von 19 bis 27 für ein reibungsloses Funktionieren.

* **Placement.Type getPlacementType() ist jetzt eine Methode auf der Schnittstelle TimelineMarker**

   Diese Methode gibt den Platzierungstyp Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL oder Placement.Type.POST_ROLL zurück. Wenn eine Werbeunterbrechung nicht aufgelöst wurde, gibt die getDuration() -Methode auf der TimelineMarker-Oberfläche 0 zurück.

**Version 2.5.6.**

* **TVSDK 2.5 unterstützt Android P.**

* **Aktivieren von Hintergrund-Audio**

   Um die Audiowiedergabe zu aktivieren, wenn die App von vorne in den Hintergrund wechselt, sollte das Programm aufrufen `enableAudioPlaybackInBackground` API von MediaPlayer mit &quot;true&quot;als Argument, wenn der Player im Status &quot;PREPARED&quot;ist.

* **alwaysUseAudioOutputLatency(boolean val) in MediaPlayer-Klasse**

Verwenden Sie bei Festlegung die Latenz der Ausgabe in der Berechnung des Audio-Zeitstempels.
Boolesche Parameter val - True verwendet die Latenz der Audioausgabe bei der Berechnung des Audiozeitstempels.

* **Optimiert, um das beste Wiedergabeerlebnis zu erhalten, selbst wenn die Bandbreitengeschwindigkeit plötzlich abnimmt**

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

   Jetzt einschließlich `AdSystem` und `CreativeId` als neue Parameter in den Anforderungen 1401 und 1403.

* **API setEncodeUrlForTracking in NetworkConfiguration-Klasse entfernt** als die unsicheren Zeichen in einer URL kodiert werden sollen.

**Version 2.5.4**

Android TVSDK v2.5.4 bietet die folgenden Updates und API-Änderungen:

* Änderungen am Standardwert für `WebViewDebbuging`

   `WebViewDebbuging` Wert auf `Fals`e standardmäßig verwendet. Um sie zu aktivieren, rufen Sie `setWebContentsDebuggingEnabled(true)` in der Anwendung.

* **Aktualisierung der OpenSSL- und Curl-Version**

   libcurl wurde auf Version 7.57.0 und OpenSSL auf Version 1.0.2k aktualisiert.

* Zugriff auf Anwendungsebene für VAST-Antwortobjekt

   Neue API eingeführt `NetworkAdInfo::getVastXml()` , der Zugriff auf das VAST-Antwortobjekt zur Anwendung bietet.

**Version 2.5.3**

Android TVSDK v2.5.3 bietet die folgenden Updates und API-Änderungen.

* Alle TVSDK-Kunden, die CRS verwenden, sollten ihre Apps mit TVSDK 2.5.3.85 oder höher unter Android aktualisieren. Dies ist ein Abbruch-in-Ersatz für die vorhandene App-Implementierung. Überprüfen Sie nach dem TVSDK-Upgrade in einem Proxy-Tool (z. B.: Charles) und bestätigen Sie, dass der Hostname und die Version im Pfad wie in der Beispiel-URL-Struktur unten dargestellt sind.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* Benutzeragent von TVSDK anpassbar: haben wir einige neue APIs hinzugefügt, um die Benutzeragenten anzupassen.

   * `setCustomUserAgent(String value)`
   * `getCustomUserAgent()`

* Cookies zwischen Android-Anwendung und TVSDK freigeben: Android TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der JAVA-Ebene (gespeichert im CookieStore der Android-App) und der C++ TVSDK-Ebene. Jetzt ist es möglich, die Cookies in der nativen C++-Ebene festzulegen und/oder zu ändern, da sie dem Java Cookie Store angezeigt werden.

* API-Änderungen:

   * Ein neues Ereignis `CookiesUpdatedEvent` hinzugefügt. Er wird vom Medienplayer gesendet, wenn sein Cookie aktualisiert wird.

   * Eine neue API wird hinzugefügt zu `NetworkConfiguration::set/ getCustomUserAgent()` , um benutzerdefinierten Benutzeragenten zu verwenden.

   * Eine neue API wird hinzugefügt zu `NetworkConfiguration::set/ getEncodedUrlForTracking` , um die Codierung von unsicheren Zeichen zu erzwingen.

   * Eine neue API wird hinzugefügt zu `NetworkConfiguration::getNetworkDownVerificationUrl()` , um im Falle eines Failover eine URL für die Netzwerküberprüfung festzulegen.

   * Eine neue Eigenschaft wird hinzugefügt zu `TextFormat::treatSpaceAsAlphaNum` , die definieren, ob der Raum beim Anzeigen von Untertiteln als alphanumerisch behandelt werden soll.

* Änderungen in `SizeAvailableEvent`. Zuvor `getHeight()` und `getWidth()` Methoden `SizeAvailableEvent` in 2.5.2 verwendet, um die Frame-Höhe und die Frame-Breite zurückzugeben, die vom Medienformat zurückgegeben wurden. Jetzt werden die Ausgabehöhe und die vom Decoder zurückgegebene Ausgabebreite zurückgegeben.

* Änderungen im Pufferverhalten: Das Pufferverhalten ändert sich. Es bleibt dem App-Entwickler überlassen, was er tun möchte, falls er leer ist. 2.5.3 verwendet die Wiedergabepuffergröße bei Pufferleersituationen.

**Version 2.5.2**

Android TVSDK v2.5.2 bietet wichtige Fehlerbehebungen und einige API-Änderungen.

**Version 2.5.1**

Die wichtigen neuen Funktionen, die in Android 2.5.1 veröffentlicht wurden.

* **Leistungsverbesserungen -** Die neue TVSDK 2.5.1-Architektur bietet eine Reihe von Leistungsverbesserungen. Basierend auf Statistiken aus einer Benchmarking-Studie von Drittanbietern bietet die neue Architektur eine 5fache Reduzierung der Startzeit und 3,8fache Reduzierung der Dropped Frames im Vergleich zum Branchendurchschnitt:

* **Sofortiges Aktivieren für VOD und Live -** Wenn Sie Sofort aktivieren, initialisiert und puffert das TVSDK Medien vor dem Start der Wiedergabe. Da Sie mehrere MediaPlayerItemLoader-Instanzen gleichzeitig im Hintergrund starten können, können Sie mehrere Streams puffern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, beginnt die Wiedergabe auf dem neuen Kanal sofort. TVSDK 2.5.1 unterstützt auch das Instant On für **live** auch Streams. Die Live-Streams werden beim Verschieben des Live-Fensters erneut gepuffert.

* **Verbesserte ABR-Logik -** Die neue ABR-Logik basiert auf der Pufferlänge, der Änderungsrate der Pufferlänge und der gemessenen Bandbreite. Dadurch wird sichergestellt, dass die ABR bei Bandbreitenschwankungen die richtige Bitrate auswählt und die Anzahl der tatsächlichen Bitratenwechsel optimiert, indem die Geschwindigkeit überwacht wird, mit der sich die Pufferlänge ändert.

* **Teilsegmentdownload/Untersegmentierung -** TVSDK reduziert die Größe jedes Fragments weiter, um die Wiedergabe so bald wie möglich zu starten. Das ts-Fragment muss alle zwei Sekunden einen Schlüsselframe aufweisen.

* **Verzögerte Anzeigenauflösung -** TVSDK wartet nicht auf die Auflösung von Nicht-Pre-oll-Anzeigen, bevor die Wiedergabe gestartet wird, wodurch die Startzeit verkürzt wird. APIs wie Suche und Trick-Play sind immer noch nicht erlaubt, bis alle Anzeigen aufgelöst sind. Dies gilt für VOD-Streams, die mit CSAI verwendet werden. Vorgänge wie Suchen und Vorwärts sind erst nach Abschluss der Anzeigenauflösung zulässig. Bei Live-Streams kann diese Funktion nicht für die Anzeigenauflösung während eines Live-Ereignisses aktiviert werden.

* **Persistente Netzwerkverbindungen -** Mit dieser Funktion kann TVSDK eine interne Liste persistenter Netzwerkverbindungen erstellen und speichern. Diese Verbindungen werden für mehrere Anforderungen wiederverwendet, anstatt für jede Netzwerkanforderung eine neue Verbindung zu öffnen und sie anschließend zu zerstören. Dies erhöht die Effizienz und verringert die Latenz im Netzwerkcode, was zu einer schnelleren Wiedergabeleistung führt.
Wenn TVSDK eine Verbindung öffnet, fordert es den Server auf, eine *Keep-Alive* Verbindung. Einige Server unterstützen diese Art von Verbindung möglicherweise nicht. In diesem Fall greift TVSDK zurück, um für jede Anfrage erneut eine Verbindung herzustellen. Auch wenn persistente Verbindungen standardmäßig aktiviert sind, verfügt TVSDK jetzt über eine Konfigurationsoption, damit Apps persistente Verbindungen bei Bedarf deaktivieren können.

* **Paralleler Download -** Durch das parallele Herunterladen von Video und Audio statt in Serien werden Starterverzögerungen reduziert. Diese Funktion ermöglicht die Wiedergabe von HLS Live- und VOD-Dateien, optimiert die verfügbare Bandbreitennutzung von einem Server, verringert die Wahrscheinlichkeit, in Puffersituationen zu gelangen, und minimiert die Verzögerung zwischen Download und Wiedergabe.

* **Parallele Anzeigendownloads -** TVSDK ruft Anzeigen parallel zur Inhaltswiedergabe vor dem Drücken der Werbeunterbrechung ab, wodurch Anzeigen und Inhalte nahtlos wiedergegeben werden können.

* **Wiedergabe**

* **MP4-Inhaltswiedergabe -** MP4-Kurzclips müssen nicht neu transkodiert werden, um sie im TVSDK wiederzugeben.

   >[!NOTE]
   >
   >ABR-Switching, Trick Play, Anzeigeneinfügung, späte Audiobindung und Untersegmentierung werden für die MP4-Wiedergabe nicht unterstützt.

* **Trick play with adaptive bit rate (ABR) -** Mit dieser Funktion kann TVSDK im Trick Play-Modus zwischen iFrame-Streams wechseln. Sie können Nicht-iFrame-Profile verwenden, um Tricks mit geringeren Geschwindigkeiten abzuspielen.

* **Smoother Trick Play -** Diese Verbesserungen verbessern das Benutzererlebnis:

   * Adaptive Auswahl der Bitrate und Framerate bei der Trickwiedergabe basierend auf der Bandbreite und dem Pufferprofil

   * Verwenden Sie den Haupt-Stream anstelle des IDR-Streams, um eine schnelle Wiedergabe mit bis zu 30 fps zu ermöglichen.

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

   * **VHL 2.0 -** Dies ist die neueste optimierte VHL-Integration (Video Heartbeats Library) für die automatische Erfassung von Nutzungsdaten für Adobe Analytics. Die Komplexität der APIs wurde verringert, um die Implementierung zu erleichtern. VHL-Bibliothek herunterladen [v2.0.0 für Android](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) und extrahieren Sie die JAR-Datei im Ordner &quot;libs&quot;.

* **SizeAvaliableEventListener**

   * `getHeight()` und `getWidth()` Methoden `SizeAvailableEvent` gibt nun die Ausgabe in Höhe und Breite zurück. Das Anzeigeseitenverhältnis kann wie folgt berechnet werden:

      ```java
      SizeAvailableEvent e;
      DAR = e.getWidth()/ e.getHeight();
      ```

      Das Speicherseitenverhältnis in Bezug auf die Sar-Breite und die Sar-Höhe kann auch zur Berechnung der Frame-Breite und der Frame-Höhe verwendet werden:

      ```java
      SAR = e.getSarWidth()/e.getSarHeight();
      frameHeight = e.getHeight();
      frameWidth = e.getWidth()/SAR;
      ```

* **Cookies**

   * Android TVSDK unterstützt jetzt den Zugriff auf JAVA-Cookies, die im CookieStore der Android-Anwendung gespeichert sind. Es wird eine Callback-API (onCookiesUpdated) bereitgestellt, um aufzuzeichnen, sobald ein neues Cookie als Teil von **Set-Cookie** Antwortheader. Diese Cookies sind als Liste von HttpCookie(s) verfügbar, die für einen anderen URI/eine andere Domäne verwendet werden, indem diese Cookie-Werte mithilfe von CookieStore für diesen bestimmten URI/diese Domäne festgelegt werden. Gleichermaßen werden die Cookie-Werte in TVSDK mit der CookieStore Add API aktualisiert.

## Funktionsmatrix {#feature-matrix}

TVSDK für Android unterstützt eine Reihe von Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.

In den unten stehenden Funktionstabellen zeigt ein &quot;Y&quot;an, dass die Funktion in der aktuellen Version unterstützt wird.

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | VOD + Live | Y |
| FER - Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | FER VOD | Y |
| Suchen, wann eine Anzeige wiedergegeben wird | VOD + Live | Nicht unterstützt |
| HEVC-Wiedergabe | VOD + Live | Nur fMP4-Container |
| AC3 und EAC3 | VOD + Live | Nicht unterstützt |
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
| Einfügen einer partiellen Werbeunterbrechung | Live | Y |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| AES-Verschlüsselung | VOD + Live | Y |
| AES-Beispielverschlüsselung | VOD + Live | Y |
| Tokenisierte Streams | VOD + Live | Y |
| Widevine DRM | VOD + Live | Nur fMP4-Container |
| Primetime DRM | VOD + Live | Y |
| Externe Wiedergabe (RBOP) | VOD + Live | Nur Primetime DRM |
| Lizenzrotation | VOD + Live | Nur Primetime DRM |
| Hauptrolle | VOD + Live | Nur Primetime DRM |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Adobe Analytics VHL-Integration | VOD + Live | Y |
| Rechnungsstellung | VOD + Live | Y |

## Gelöste Probleme {#resolved-issues}

Wenn die Lösung mit einem gemeldeten Problem verbunden ist, wird eine Zendesk-Referenz angezeigt, z. B. ZD#xxxxx.

**Android TVSDK 3.15**

Dieser Abschnitt enthält eine Zusammenfassung des Problems, das in der Android-Version TVSDK 3.14 behoben wurde.

* ZD#46903 - Anwendung stürzt mehrmals ab, wenn kreatives Tag fehlt oder wenn [!UICONTROL url CDATA] ist leer in [!UICONTROL VAST] Antwort.

**Android TVSDK 3.14**

* ZD#46903 - Anwendungsabstürze bei [!UICONTROL CDATA] -Knoten ist für jeden der [!UICONTROL ClickTracking], [!UICONTROL CustomClick] oder [!UICONTROL CompanionClickTracking] Element in [!UICONTROL VAST] Antwort.

### Behobene Probleme in den vorherigen Versionen

**Android TVSDK 3.12**

* ZD#40584 - Die Primetime-Referenz-App wird nicht mit der neuesten Gradle-Version erstellt.

**Android TVSDK 3.11**

* ZD#41252 - Koreanische Zeichen in WebVTT, die nach Android 7.1 fehlen.

**Android TVSDK 3.10**

* ZD#40340 - Anwendungsabstürze mit dem Fehler &quot;App nicht antworten&quot;beim Versuch der Wiedergabe nach dem Blockieren aller TS (TypeScript)-Dateien.

**Android TVSDK 3.8**

* Es wurden keine neuen Probleme hinzugefügt.

**Android TVSDK 3.7**

* Es wurden keine neuen Probleme hinzugefügt.

**Android TVSDK 3.6**

* Es wurden keine neuen Probleme hinzugefügt.

**Version 3.5**

* ZD#37503 - JSON-Antworten für die CRS-Regeln werden zwischengespeichert, um doppelte Anforderungen zu vermeiden.

**Version 3.4**

* ZD#37996 - Es wurde ein Problem bezüglich des Problems der Choppy-Wiedergabe für lineare und VOD CMAF HEVC-Streams behoben.
* ZD#37706 - Es wurde ein Problem mit durcheinandergewürfelten Untertiteln behoben.
* ZD#37622 - Es wurde ein Problem mit tödlichen URISyntaxErrors für bestimmte Anzeigen behoben.
* ZD#36938 - Es wurde ein Problem behoben, bei dem die Bitrate nach unten zur mittleren Bitrate wechselte und dann zur höchsten Bitrate wechselte, nachdem die Trick-Wiedergabe beendet wurde.

**Version 3.3**

* ZD#37394 - CMAF-Assets werden schnell vorwärts zu Artefakten, nachdem sich die Geschwindigkeit geändert hat.
   * Es wurde ein Problem behoben, das bei einer Profiländerung während der Trickwiedergabe auftrat.
* ZD#37396 - Anzeigen-Tracking-Ereignisse fehlen für einige Mid-Roll- und Post-Roll-Ereignisse.
   * Ein spezieller Fall für Anzeigen-Tracking-Ereignisse wurde behoben.
* ZD#37491 - HTTP-Statuscode mit Fehlermeta ist nicht vorhanden.
   * Es wurde daran gearbeitet, Netzwerkfehler zu übertragen, die höher im Stapel waren.
* ZD#37808 - Zulassungsliste New Custom Header.
   * SSAI_TAG-Unterstützung wurde als Teil dieser Korrektur hinzugefügt.
* ZD#37622 - URISyntax-Fehler von bestimmten Anzeigen-Pods.
   * Fehlerkorrektur - Es wurde ein Problem mit dem Absturz der Stream-Wiedergabe behoben, wenn die benutzerdefinierte Android-App Anzeigen mit nicht kodiertem % bereitgestellt wird
* ZD#37631 - Übergeordneter Manifestwiederholungsmechanismus für Android TVSDK.
   * Es wurde eine neue API in der Netzwerkkonfiguration für die Verarbeitung dieser Verbesserung hinzugefügt. Wenn diese API nicht verwendet wird, wird das Manifest nicht erneut versucht. Wenn es verwendet wird, wird es erneut versucht, Manifest für die Verarbeitung von Netzwerkfehlern und Timeouts zu verwenden.

**Version 3.2**

* ZD#37493 - Tracking-Beacons für die Live-Wiedergabe werden nicht zeitweise für die erste Anzeige in Folge ausgelöst.
* ZD#36985- Tracking-Beacons werden nicht für leere Werbeunterbrechungen in VMAP-Antworten gesendet.
* ZD#37134 - TVSDK gibt zeitweise die falsche ID für VMAP-Antworten aus.

**Version 3.0**

* ZD#33740 - TVSDK gibt unmittelbar nach dem Erstellen eines MediaPlayer-Objekts und dem Aufruf von replaceCurrentResource() eine unnötige Warnung aus

   * Die frühere Fehlerbehebung wurde verbessert, indem &quot;Wiederherstellen&quot;nur aufgerufen wird, wenn der Player ausgesetzt ist.

* ZD#36442 - Jede neue Wiedergabe trennt die Remote-Debugging-Sitzung, wodurch das Debugging unmöglich wird.

   * Debug ist in der Webansicht standardmäßig nicht möglich, da das Debugging nicht standardmäßig aktiviert ist. Die App sollte das Debugging bei Bedarf aktivieren, indem setWebContentsDebuggingEnabled(true) für ein Objekt aufgerufen wird, das von MediaPlayer.getCustomAdView() zurückgegeben wird.

* ZD#33688 - Unterstützung für Just-in-Time und Auflösung

   * Werbeunterbrechungen werden in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst.

* ZD#36441 - Die Dauer des Live-Fensters nimmt über 5 Minuten hinweg zu und verursacht mehrere Probleme.

   * Es wurde ein Problem behoben, bei dem virtualStartTime beim Berechnen des virtuellen Live-Punkts zweimal hinzugefügt wurde, was zu diesem Problem führte.

**Android TVSDK 2.5.6**

* ZD #34992 - Die Sprache ist in &quot;Geschlossene Beschriftung&quot;leer.

   * Es wurde ein Fall behoben, bei dem TVSDK #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS vom Hauptmanifest nicht analysiert hat, um die Details des Untertiteltracks abzurufen.

* ZD #35078 - Android P validation.

   * TVSDK 2.5.6 wurde mit den neuesten Beta-Builds für Android P validiert. Keine Probleme aufgrund des neuen Android-Betriebssystems gefunden.

* ZD #34149 - Der Player fordert weiterhin Manifeste an, auch wenn ein Fehler auftritt.

   * Fehlerkorrektur - TVSDK führt jetzt keine wiederholten Aufrufe mehr durch, selbst wenn alle Profile ausfallen (404-Fehler).

* ZD #31533 - Abspielen von Audio auf Android, nachdem die App in den Hintergrund gesendet wurde.

   * Hinzugefügt `enableAudioPlaybackInBackground` API von MediaPlayer, die mit &quot;True&quot;als Argument aufgerufen werden sollte (wenn der Player im Status &quot;VORBEREITT&quot;ist), um die Wiedergabe von Audio zu aktivieren, wenn die App im Hintergrund ausgeführt wird.

**Android TVSDK 2.5.5**

* ZD #21647 - Android TVSDK benachrichtigt 640 x 368, wenn die tatsächliche Videogröße 640 x 360 beträgt.

   * Aufgrund der Variablen m_nOutputHeight (innerhalb von AndroidMCVideoDecoder) wird die Frame-Höhe anstelle der tatsächlichen Ausgabehöhe aktualisiert. Es wurden relevante Änderungen an der Funktion getVideoFrame vorgenommen, um m_nOutputHeight korrekt zu berechnen.

* ZD #26614 - Urgent - Adserving/programmgesteuert von Drittanbietern - Fehler bei der Bereitstellung von Impressionen.

   * Die frühere Korrektur wurde verbessert, indem die Groß-/Kleinschreibung in XML-Parsing verarbeitet wurde, bei der das Problem reproduzierbar war, wenn &quot;Leerzeichen&quot;vor dem &quot;Gleichheitszeichen&quot;liegt, wie &lt;vast version=&quot;2.0&quot;>

* ZD #29296 - Android: Fügen Sie AdSystem und Creative ID zu CRS-Anforderungen hinzu.

   * Jetzt einschließlich &#39;AdSystem&#39; und &#39;CreativeId&#39; als neue Parameter in den Anfragen 1401 und 1403.

* ZD #33062 - TVSDK stürzt beim Auftreten des Pipe-Zeichens in der VAST-Antwort unter dem CDATA-Knoten ab

   * API setEncodeUrlForTracking in NetworkConfiguration-Klasse wurde als unsichere Zeichen in einer URL, die kodiert werden soll, entfernt

* ZD #33063 - CRS-Dateiauswahllogik war fehlerhaft - TVSDK sendete keine CRS-Anforderung für das Webm-Format, sondern schickte sie stattdessen für 3gpp-Dateien.

   * Die Logik wurde jetzt korrigiert. Bei der Verwendung von Mediendateien mit Webm- und 3gpp-Format muss eine CRS-Anfrage für Webm gesendet werden. Bei Verwendung der beiden Mediendateien im 3gpp-Format wird die CRS-Anforderung für die höchste Bitrate-3gpp-Datei gesendet.

* ZD #33125 - Die Android-App stürzt mit einem bestimmten DoubleClick-Tag im VMAP ab.

   * Das Szenario wurde behoben, um den Absturz zu vermeiden.

* ZD #32256 - License Rotation &amp; Key Rotation Issue - Adobe Access

   * Die Segmentinitialisierung mit den DRM-Metadaten für SampleAES-Inhalt wurde korrigiert. Funktioniert problemlos mit AES128-Inhalten.

* ZD #33619 - Schnelle Weiterleitung eines wachsenden Playlist-Inhalts, der in der Nähe des Live-Punkts im Pufferstatus steckte.

   * Handle den Fall beim Überqueren des Live-Punkts im Trick Play-Modus

* ZD #34151 - TimedMetadata-Objekte nicht in der Reihenfolge.

   * Zwei TimedMetadata-Ereignisse wurden in zufälliger Reihenfolge angezeigt, wenn sie zur gleichen Zeit in der Timeline gehörten. Die ursprüngliche Reihenfolge wurde manifestiert.

* ZD #34189 - Problem beim Versuch, eine Werbeunterbrechung zu beginnen.

   * Das Problem betraf SSAI-Anzeigen, die mit Diskontinuität zugeordnet werden. Die Ursache war ein Verhalten, wenn wir versuchen, solche Anzeigen zu beginnen, wir nach einem Keyframe suchen und ihn nicht finden. Der Grund dafür war, dass der Audio-Zeitstempel der Anzeige vor dem Min-Video-Zeitstempel lag. Daher suchen wir am Ende nach einem Schlüsselframe mit falschen fragmentDump-Daten. Jetzt behoben.

* ZD #34528 - Videoauflösung, die nicht über 640x360 hinaus auf dem Dongle der 3. Generation von FireTV aktualisiert wird.

   * Die Fehlerbehebung wurde um die neuesten Firmware-Updates erweitert.

* ZD #34793 - TVSDK 2.5.x wurde zum Absturz mit dem benutzerdefinierten Content Resolver verwendet, wenn VideoEngine davon ausging, dass die auditudeSettings verfügbar sind und nicht.

   * Der Absturz erfolgte aufgrund eines Funktionsaufrufs an einem gemeinsam genutzten Null-Zeiger (auditudeSettings). Es wurde eine bedingte Prüfung in VideoEngineTimeline::placeToSourceTimeline() hinzugefügt, um sicherzustellen, dass auditudeSettings verfügbar ist, bevor irgendetwas für dieses Objekt aufgerufen wird.

* ZD #32584 - Es ist nicht möglich, auf vollständige Informationen im Abschnitt &lt;extensions> -Knoten einer VAST-Antwort.

   * Es wurde ein Problem mit der XML-Analyse behoben, sodass NetworkAdInfo jetzt die vollständigen Informationen im Abschnitt &lt;extensions> Knoten

* ZD #35086 - Bei bestimmten VMAP-Antworten werden keine vollständigen Erweiterungsdaten vom Player abgerufen.

   * Das Problem war spezifisch für die Erweiterung XML, da das XML-Parsing nicht funktionierte, wenn die Erweiterung XML doppelte Anführungszeichen im Attributwert enthielt. Korrektur des Problems.

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Wiedergabesitzung zur Aktivierung des Remote-Debugging von Webansichten.

WebViewDebbuging ist standardmäßig auf False festgelegt. Um das Debugging zu aktivieren, legen Sie mithilfe von setWebContentsDebuggingEnabled(true) den Wert true über die Anwendung fest.

* ZenDesk#33011 - Die Anzeigen-Timeline wird im Fall einer fehlgeschlagenen CRS-Anforderung nicht aufgelöst.

   Wenn eine CRS-Anfrage an eine Anzeige fehlschlägt, wird die Timeline aufgelöst und die verbleibenden Anzeigen werden wiedergegeben.

* ZenDesk#34528 - Die Videoauflösung wird auf dem Dongle der dritten Generation von FireTV nicht über 640x360 aktualisiert.

   Die Videoauflösung schaltet sich als Bitratenschalter hoch.

* ZenDesk#33192 - AudioTrack hat einen Nullnamen, wenn die Verfolgung über AudioUpdatedEventListener::onAudioUpdated abgerufen wird.

   In einigen Szenarien zum FireTV-Stick wurde das onAudioUpdate-Ereignis ausgelöst, wenn kein tatsächliches Audio-Update vorhanden war. Dieses Problem wurde jetzt behoben.

**Android TVSDK 2.5.3**

* Zendesk#32216 - Benutzerdefiniertes Tag-Abonnement für TimedMetadata funktioniert nicht.

   Wir geben ID3-Daten als Byte-Array (zur Unterstützung von APIC- oder generischen Daten) an den Client zurück, während in Version 1.4 eine Zeichenfolge zurückgegeben wird. Das Byte-Array verarbeitet das von null beendete Zeichen nicht selbst. Daher zeigte es dem Client Sonderzeichen an. Dieses Problem wurde jetzt behoben.
* Zendesk#32670 - Player kann nicht auf redundante Playlist gesetzt werden

   Dies funktioniert jetzt einwandfrei und setNetworkDownVerificationUrl funktioniert erwartungsgemäß.
* Zendesk#32369 - Die verdeckte Beschriftung zeigt unterschiedliche Farbverläufe oder Artefakte.

   Problem mit CC-Fehlern wurde im aktuellen Build behoben
* Zendesk#25590 - Verbesserung: TVSDK-Cookie-Store ( C++ zu JAVA )

   Android TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der JAVA-Ebene (gespeichert im CookieStore der Android-App) und der C++ TVSDK-Ebene.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 scheint nicht über die Fehlerbehebung für PTPLAY-20269 zu verfügen

   Dieses Problem wurde behoben und in den Zweig 2.5.2 integriert.
* Zendesk#31806 - Auditude sticks bei der Vorbereitung

   Der Player blieb im Status &quot;Vorbereiten&quot;hängen, da die Antwort-XML ein leeres Tag enthielt. Jetzt wurde das Problem behoben.
* Zendesk#31727 - TVSDK 2.5 Zeichen für geschlossene Beschriftungen werden entfernt oder falsch geschrieben.

   Das Problem wurde behoben, und es werden keine Zeichen durch Ablegen/Fehlschreiben ersetzt.
* Zendesk#31485 - DrmManager in 2.5

   Es gab ein Problem beim Erstellen von DRMManager über den neuen DRMManager (Kontext). Implementierung der DRMService-Klasse, die DRMManager bereitstellt.
* Zendesk#32794- 1080P Auflösungsstream wird nicht auf Android wiedergegeben

   Wir haben die Methoden SizeAvailableEvent und Previous, getHeight() und getWidth() von SizeAvailableEvent in 2.5 geändert, um die Frame-Höhe und die Frame-Breite zurückzugeben, die vom Medienformat zurückgegeben wurden. Jetzt werden die Ausgabehöhe und die Ausgabebreite zurückgegeben, die jeweils vom Decoder zurückgegeben wurden.
* Zendesk #19359 Flash Player stürzt aufgrund der Position des Attributs #EXT-X-FAXS-CM im Manifest auf Setebene ab.

   Das Tag #EXT-X-FAXS-CM muss immer auf der oberen Wiedergabeliste stehen, bevor einzelne Bitraten oder Segmente in der Wiedergabeliste angezeigt werden.

**Android TVSDK 2.5.2**

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

**Android TVSDK 2.5.1**

* Gerätespezifischer Absturz (Samsung Galaxy Tab 4); VOD DRM LBA mit Auditude und klicken Sie auf Anzeigen.
* VHL - Beim Start von Inhalten ab einem Versatz werden falsche Heartbeat-Aufrufe gesendet.
* Wenn VPAID-Anzeigen wiedergegeben werden, ruft der VHL-Heartbeat das Ereignis auf:type:Abspielanzeige fehlt.
* Nachdem der Player den Status ABGESCHLOSSEN erhalten hat, wechselt er für Post-Roll-Anzeigen wieder zum PLAYING-Status mit SKIP adBreakPolicy .
* Cookies werden nicht an ausgehende Anzeigen-Callbacks angehängt.
* Anzeigen-Cue-Punkte sind nicht sichtbar.
* HLS mit separatem EAC3 SAP Track wird nicht geladen.
* Der Player stürzt ab, wenn TVSDK nach der Wiederherstellung des Media-Players den Intent &quot;Bildschirm ein&quot;erhält.

## Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

**Android TVSDK 3.11**

* Keine neuen Einschränkungen hinzugefügt.

### Bekannte Probleme und Einschränkungen in den vorherigen Versionen

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

* ID3, verdeckte Untertitel, Unterstützung für verspätete BindungsAudio wurde für den CMAF-Stream (CBC) nicht überprüft.
* Auf einigen Geräten tritt ein Problem mit geringer Reproduzierbarkeit auf, aufgrund dessen Videoverzerrungen bei der Trickwiedergabe in CMAF-Streams oben angezeigt werden können.

**Android TVSDK 3.3**

* cp:c608 Beschriftungen werden für die CMAF-Stream-Wiedergabe nicht unterstützt.

**Android TVSDK 3.2**

* TVSDK 3.2 unterstützt keine CMAF Sample AES- und AES128-Streams-Wiedergabe.
* HEVC-CMAF-Streams bieten keine Unterstützung für die Wiedergabe von Untertiteln.
* Für WV-verschlüsselte Streams wird eine grüne Farbgebung angezeigt, wenn um das nicht verschlüsselte Segment herum gesucht wird.
* CMAF-Streams unterstützen keine ID3-Ereignisse.
* HLS-Streams unterstützen kein TTML-Untertitelformat.

**Android TVSDK 3.0**

* Die HEVC-Unterstützung weist in dieser Version folgende Einschränkungen auf

   * DRM wird nicht unterstützt
   * CC-Unterstützung (CEA 608/708) nicht überprüft
   * 4K-Unterstützung ist noch nicht vorhanden
   * ID3-Tags unterstützen nicht verifiziert

* Bei Ereignissen zum Anzeigenfortschritt spiegelt die Timeline-Leiste möglicherweise nicht die hundertprozentige genaue Anzeigenwiedergabedauer wider. Als Problemumgehung kann `adcompleteevent` um die Fertigstellung der Anzeigenwiedergabe zu erfahren und die Benutzeroberfläche für verschiedene Zwecke zu aktualisieren, z. B. die Timeline-Leiste zu aktualisieren, die anzeigenbezogene Benutzeroberfläche zu entfernen usw.
* Die von VMAP zurückgegebenen umfangreichen Anzeigenaufrufe berücksichtigen nicht die Just-in-Time-Lookahead-Position.

**Android TVSDK 2.5.6**

* Mehrere VMAP-Werbeunterbrechungen gleichzeitig werden nicht unterstützt.

**Android TVSDK 2.5.3**

Diese Version weist die folgenden Probleme auf:

* Die Live-Videowiedergabe kann auf Geräten mit geringer Auslastung oder unter schlechten Netzwerkbedingungen Probleme bei der Audio-Video-Synchronisierung aufweisen.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. Auch FER mit Versatz funktioniert nicht.
* Die Wiedergabe wird möglicherweise blockiert, wenn der Inhalt von &quot;Spätbindung an Audio&quot;gesucht wird.
* Gelegentlich können WebVTT-Untertitel für LIVE-Inhalte nicht mehr synchron sein.
* Gelegentlich kann nach einer Werbeunterbrechung eine schnelle Wiedergabe einiger Frames auftreten.
* Manchmal wird der Fehler 303 für &quot;Tripple Wrapper Ad Breaks&quot;ausgegeben, auch wenn Anzeigen wiedergegeben werden.

**Android TVSDK 2.5.2**

Diese Version weist die folgenden Probleme auf:

* Die Live-Videowiedergabe kann auf Geräten mit geringer Auslastung Probleme mit der Audio-Video-Synchronisierung haben.
* Die Wiedergabe kann beim Suchen nach dem Ende des VOD-Mediums anhalten.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. Außerdem funktioniert FER mit Versatz nicht.

**Android TVSDK 2.5.1**

Diese TVSDK-Version weist die folgenden Probleme auf:

* Die Live-Videowiedergabe kann auf Geräten mit geringer Auslastung Probleme mit der Audio-Video-Synchronisierung haben.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. Außerdem funktioniert FER mit Versatz nicht.
* Wenn in der VMAP-XML ein leeres VAST-Tag ohne ein explizites schließendes Tag (&lt;/vast>) und ohne einen Zeilenumbruch danach wird die VMAP-XML nicht richtig analysiert und Anzeigen werden möglicherweise nicht wiedergegeben.
* VPAID-Post-Roll wird nicht unterstützt.

## Hilfreiche Ressourcen {#helpful-resources}

* [Systemanforderungen](/help/programming/tvsdk-3x-android-prog/android-3x-introduction/android-3x-requirements.md)
* [TVSDK 3.10 für Android-Programmierhandbuch](/help/programming/tvsdk-3x-android-prog/android-3x-introduction/overview-prod-audience-guide/android-3x-overview-prod-audience-guide.md)
* [TVSDK Android Javadoc für API-Referenz](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [TVSDK Android C++ API-Dokument](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html) - Jede Java-Klasse verfügt über eine entsprechende C++-Klasse. Die C++-Dokumentation enthält mehr erklärendes Material als die Javadocs. Weitere Informationen zur Java-API finden Sie in der C++-Dokumentation .
* [Migrationshandbuch für TVSDK 1.4 bis 2.5 für Android (Java)](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* Informationen zur Handhabung von Ein-/Ausschaltszenarien für den Bildschirm finden Sie im Abschnitt `Application_Changes_for_Screen_On_Off.pdf` im Build enthaltene Datei.
* Die vollständige Hilfedokumentation finden Sie unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
