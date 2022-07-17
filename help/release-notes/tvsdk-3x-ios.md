---
title: TVSDK 3.13 für iOS - Versionshinweise
description: TVSDK 3.13 für iOS - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK iOS 3.13.
exl-id: adf8ab23-86d6-4113-b243-2709d5f7f829
source-git-commit: 59ea8008c828f3bdf275fea5cc2a59c37b0c4845
workflow-type: tm+mt
source-wordcount: '7575'
ht-degree: 0%

---

# TVSDK 3.13 für iOS - Versionshinweise {#tvsdk-for-ios-release-notes}

TVSDK 3.12 für iOS - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK iOS 3.12.

## System- und Softwareanforderungen {#system-software-requirements}

Stellen Sie vor dem Herunterladen von iOS 3.12 sicher, dass Ihre Hardware, Ihr Betriebssystem und Ihre Anwendungsversionen die folgenden Anforderungen erfüllen:

Betriebssystem: iOS 8.0 oder höher.

## iOS TVSDK 3.13

Mit der Version wird die Unterstützung für DEMUXED-&quot;HLS/CMAF&quot;-Anzeigen (Preroll, Midroll und Postroll) für LIVE-, VOD- und FER-Streams eingeführt.

Fehlerbehebungen für von Kunden gemeldete Probleme finden Sie unter [Gelöste Probleme](#resolved-issues). Einschränkungen finden Sie unter [bekannte Probleme und Einschränkungen](#known-issues-and-limitations).

### Neue Funktionen und Fehlerbehebungen in den vorherigen Versionen {#whats-new-previous}

**iOS TVSDK 3.12**

Es wurde ein Problem behoben, bei dem der Live-Stream nach 15 Minuten Wiedergabe fehlschlug.

**iOS TVSDK 3.11**

Fehlerbehebungen für Kundenprobleme, bei denen `isFallbackOnInvalidCreativeEnabled` und -Methode `customParams` verursacht den Absturz der Anwendung.

**iOS TVSDK 3.10**

* Es wurde ein Problem behoben, bei dem der TVSDK-Player nicht ausgelöst wurde. `PTMediaPlayerStatusError` Benachrichtigung, wenn das Netzwerk nicht verfügbar ist.

**iOS TVSDK 3.9**

* Es wurde ein Problem behoben, bei dem VTT-Untertitel nicht wiedergegeben werden konnten, was dazu führte, dass die App hängenblieb.

* iOS TVSDK 3.9 enthielt das aktualisierte Individualisierungs-Transportzertifikat.

**iOS TVSDK 3.8.0.83 Hotfix**

Das Hotfix enthielt das aktualisierte Individualisierungs-Transportzertifikat.

**iOS TVSDK 3.8**

Einhaltung von iOS 13 und Umgang mit iOS 13 `UIWebView` API-Einstellung.

**iOS TVSDK 3.7**

Hotfix für ein Szenario, in dem die Wiedergabe angehalten wurde, wenn viele Anfragen zur Anzeigenauflösung gleichzeitig gestellt wurden.

**iOS TVSDK 3.6**

**Korrekturen in der Eigenschaft &quot;wideXML&quot;der Klasse`PTNetworkAdInfo`**

Die `vastXML` -Eigenschaft nicht ordnungsgemäß festgelegt wurde und einen Null-Wert zurückgab.

**iOS TVSDK 3.5**

**Aktivieren von Hintergrund-Audio**

*Konfigurieren Sie Ihre App so, dass sie weiterhin Audio abspielt, wenn sie im Hintergrund ausgeführt wird.*

Um diese Funktion zu aktivieren, müssen wir die neue API festlegen `audioPlaybackInBackground` hinzugefügt in `PTMediaPlayer` -Klasse. Wenn diese API aktiviert ist, kann Ihre App Hintergrundaudio abspielen.

**iOS TVSDK 3.4.0.19 (Hotfix)**

Diese Version enthält eine Korrektur für die Anwendungsabstürze, die in einem Anzeigen-Failover-Szenario auftreten.

**iOS TVSDK 3.4**

**Zeitüberschreitung bei der Anzeigenauflösung**

* Mit TVSDK 3.4 können Benutzer jetzt den Timeout-Wert für die allgemeine Anzeigenauflösung und Manifestdownloads festlegen. Wenn innerhalb eines bestimmten Timeouts einige Anzeigen nicht aufgelöst wurden, gibt TVSDK die verbleibenden Anzeigen wieder.

* `PTAdMetadata: adRequestTimeout` Die API wird nicht mehr unterstützt und entfernt. Der Standardwert wurde auf 35 Sekunden festgelegt.

* Zwei neue alternative APIs wurden im `PTAdMetadataClass: adResolutionTimeout`  - Zeitüberschreitung für die gesamten Anzeigenauflösungsaufrufe adManifestTimeout - Zeitüberschreitung für Anzeigenmanifest-Downloads.

**Umsatzoptimierung**

TVSDK wurde aktiviert, um Problembereiche im Zusammenhang mit Werbe-Einfüge-Workflows zu identifizieren und einen Analyseendpunkt der Wahl zu melden.

**Version 3.3**

TVSDK 3.3 entspricht jetzt dem iOS 11 SDK. Alle veralteten APIs wurden durch geeignete Alternativen ersetzt.

**Version 3.2**

**Zusätzliche Protokollierungsunterstützung (Phase 2)**

Unterstützung für Fehlerbenachrichtigungen hinzugefügt, falls:

* Die HLS-Version der Anzeige verwendet eine höhere Ebene als Inhalte.

* Nur-Audio-Variante ist ausgeschlossen.

* Die VAST-/VMAP-Anfrage ist fehlgeschlagen.

**Version 3.1**

* **Zusätzliche Protokollierungsunterstützung**
Zusätzliche Unterstützung für beschreibende Benachrichtigungen bei Fehlern bei der Anzeigenwiedergabe.

* **Hinzugefügt [!DNL Fairplay] Verschlüsselte CMAF-Stream-Unterstützung**
   [!DNL Fairplay] Verschlüsselte CMAF-Streams mit AVC-Codec-Wiedergabe werden jetzt unterstützt.

**Version 3.0.1**

Keine neue Funktion oder Verbesserungen in dieser Version.

**Version 3.0**

* TVSDK 3.0 unterstützt HEVC-Streams.

* Just In Time - Beheben von Anzeigen, die näher an Anzeigenmarken liegen.

Hinzugefügt `enableDelayAdLoading` -Eigenschaft des booleschen Typs in der Benutzeroberfläche auf App-Ebene, um JIT zu aktivieren. Wenn `enableDelayAdLoading` ist NO, wird `setadMetadata.delayAdLoading`auf True (Eigenschaft der PTAdMetadata-Schnittstelle).

Wenn diese Eigenschaft aktiviert ist, löst TVSDK jede Werbeunterbrechung vor der Position basierend auf dem definierten Toleranzwert auf. Standardmäßig `delayAdTolerance` auf fünf Sekunden eingestellt ist.

**Version 1.4.45**

Zur Einhaltung von Xcode10 hat TVSDK von `libstdc++` nach `libc++`und daher wird als Mindestversion iOS 7 unterstützt. Zuvor war es iOS 6.

**Version 1.4.44**

Keine neue Funktion oder Verbesserungen in dieser Version.

**Version 1.4.43**

* TV-ähnliche Erlebnisse, wenn man mitten in einer Anzeige Mitglied werden kann, ohne das Tracking einer partiellen Anzeige auszulösen.\
   Beispiel: Der Benutzer schließt sich in der Mitte (40 Sekunden) einer 90-Sekunden-Werbeunterbrechung an, die aus drei 30-Sekunden-Anzeigen besteht. Dies ist 10 Sekunden nach der zweiten Anzeige in der Pause.

   * Die zweite Anzeige wird für die verbleibende Dauer (20 Sek.) gefolgt von der dritten Anzeige wiedergegeben.
   * Anzeigentracker für die abgespielte partielle Anzeige (zweite Anzeige) werden nicht ausgelöst. Die Tracker nur für die dritte Anzeige werden ausgelöst.

* Hinzugefügt `enableVodPreroll` -Eigenschaft des booleschen Typs in der PTAdMetadata-Benutzeroberfläche. Mit der -Eigenschaft kann die Pre-Roll-Funktion für einen VoD-Stream aktiviert werden. Wenn `enableVodPreroll` ist NO, PSDK gibt keine Pre-Roll-Wiedergabe aus. Dies hat jedoch keine Auswirkungen auf die Mid-Roll. Der Standardwert von `enableVodPreroll` ist JA.
* `closedCaptionDisplayEnabled` API von `PTMediaPlayer` -Schnittstelle ab iOS v1.4.43 als veraltet markiert. So bestimmen Sie, ob für eine bestimmte `PTMediaPlayerItem`, prüfen Sie die `subtitlesOptions` Eigenschaft von `PTMediaPlayerMediaItem`.

**Version 1.4.42**

In dieser Version werden keine neuen Funktionen hinzugefügt. Eine Liste der behobenen Probleme finden Sie unter [Gelöste Probleme](#resolved-issues).

**Version 1.4.41**

API-Änderungen:

* **isSecure**: Eine neue API wird eingeführt isSecure, um den Player vor der Aufzeichnung und Ausgabe eines Fehlers zu schützen. Der Standardwert ist &quot;true&quot;.

* **allowExternalRecording**: Es wurde eine neue API eingeführt, um die Spiegelung von Flugspielen für sichere Inhalte zu ermöglichen. Airplay-Spiegelung wird als Aufzeichnung behandelt. `allowExternalRecording` Wert muss auf `True`, um das Spiegeln von Flugzeugen zu ermöglichen oder `False` um die Spiegelung von Flugzeugen zu stoppen, um sichere Inhalte zu erhalten. Standardmäßig `value` ist wahr.

**Version 1.4.40**

Keine neuen Funktionen.

**Version 1.4.39**

* iOS TVSDK ist mit VHL 2.0.1 und VHL 2.0.1 mit Nielsen zertifiziert.

* iOS TVSDK wurde aktualisiert, um CRS-Anforderungen vom neuen Akamai-Host zu stellen `primetime-a.akamaihd.net`.

* Die neue Hostnamenkonfiguration ermöglicht eine skaliertere Bereitstellung von CRS-Assets über HTTP und HTTPS (SSL).

**Version 1.4.36**

VHL 2.0 in iOS TVSDK integrieren und zertifizieren : Die Barriere im `VideoHeartbeatsLibrary` Implementierung durch Verringerung der Komplexität der APIs.

**Version 1.4.34**

**Netzwerkanzeigen-Informationen**

TVSDK-APIs bieten jetzt zusätzliche Informationen zu VAST-Antworten von Drittanbietern. Anzeigen-ID, Anzeigensystem und VAST-Anzeigenerweiterungen werden im Abschnitt `PTNetworkAdInfo` -Klasse, die über  `networkAdInfo`  -Eigenschaft für ein Anzeigen-Asset. Diese Informationen können für die Integration mit anderen Ad Analytics-Plattformen wie **Moat Analytics**.

**Version 1.4.31**

* **Abrechnungsmetriken** Um Kunden aufzunehmen, die nur für ihre Verwendung zahlen möchten, anstatt einen festen Satz unabhängig von der tatsächlichen Verwendung zu verwenden, erfasst Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel Kunden abrechnen müssen.

   Jedes Mal, wenn TVSDK ein Stream-Startereignis generiert, beginnt der Player, HTTP-Nachrichten regelmäßig an das Abrechnungssystem der Adobe zu senden. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann sich für standardmäßige VOD, Pro VOD (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterscheiden. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, Ihr Vertrag mit Adobe bestimmt jedoch die tatsächlichen Werte.

* **Multi-CDN-Unterstützung für CRS-Anzeigen** TVSDK unterstützt jetzt Multi-CDN für CRS-Anzeigen. Durch die Bereitstellung von FTP-Details für CRS-Anzeigen können Sie andere CDN-Speicherorte als das standardmäßige CDN angeben, das sich im Besitz der Adobe befindet, z. B. [!DNL Akamai].

**Version 1.4.29**

Im `PTSDKConfig` -Klasse, die `forceHTTPS` API wurde hinzugefügt.

Die `PTSDKConfig` -Klasse bietet Methoden zum Durchsetzen von SSL für Anfragen an Adobe Primetime-Adentscheidungen-, DRM- und Video Analytics-Server. Weitere Informationen finden Sie unter `forceHTTPS` und `isForcingHTTPS` -Methoden für diese Klasse. Wenn ein Manifest über HTTPS geladen wird, behält TVSDK die Inhaltsverwendung von HTTPS bei und berücksichtigt diese Verwendung beim Laden relativer URLs aus diesem Manifest.

>[!NOTE]
>
>Anforderungen an Drittanbieter-Domänen wie Anzeigenverfolgungspixel, Inhalts- und Anzeigen-URLs und ähnliche Anforderungen werden nicht geändert. Inhaltsanbieter und Anzeigen-Server sind dafür verantwortlich, URLs bereitzustellen, die über HTTPS unterstützt werden.

**Version 1.4.18**

Das Primetime iOS TVSDK unterstützt jetzt JavaScript-Kreativelemente mit VPAID 2.0, um ein umfangreiches interaktives Inhalts-Anzeigenerlebnis zu ermöglichen. Weitere Informationen zu VPAID 2.0 finden Sie unter VPAID-Anzeigenunterstützung.

**Version 1.4.17**

* tvOS

   TVSDK unterstützt native tvOS-Anwendungen.
* Die folgenden Inhaltstypen können wiedergegeben werden:

   * VOD
   * Live
   * AES-128
   * Alternative Audio- und Untertitel
   * FER

* Die folgenden Arten von Anzeigen können angezeigt werden:

   * Allgemein
   * VAST2
   * VAST3
   * VMA

* Die folgenden Funktionen werden derzeit nicht unterstützt:

   * Digital Rights Management (DRM)
   * Anzeigenbanner
   * TV Markup Language (TVML)

**Version 1.4.13**

>[!NOTE]
>
>Das Nielsen-Modul wurde aus dem TVSDK-Build entfernt. TVSDK wird demnächst mit einem neuen Nielsen-Integrationsmodul aktualisiert.

**Ad Fallback, Daisy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103)**

Bei VAST-Anzeigen (Kreativen) mit aktivierter Ausweichregel behandelt das TVSDK eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht, stattdessen Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren. Weitere Informationen finden Sie unter Anzeigen-Fallback für VAST- und VMAP-Anzeigen.

**Version 1.4.9**

**Blackout-Signalisierung mit Ersatz für alternativen Inhalt**

Im Rahmen des TVSDK-Updates für Version 1.4 unterstützt Adobe jetzt auch das Wechseln in und das Rückgängigmachen von regionalen Blackouts gegenüber linearen Inhalten. Das TVSDK kann jetzt zwei Manifestdateien parallel, Hauptdatei und alternative verarbeiten, um Blackout-Signale zu überwachen, selbst wenn anstelle der ursprünglichen Programmierung alternative Programmierung angezeigt wird.

**Version 1.4.8**

**Video Heartbeats Library (VHL) aktualisiert auf Version 1.5**

* Möglichkeit zum Senden von Metadaten mit Videostart oder Video-/Anzeigen-/Kapitelstart als Kontextdaten.

* Weniger Netzwerk-Traffic: Heartbeats sind im Durchschnitt weniger und kleiner.

**Version 1.4.7**

* **On-Premise-Individualisierungsunterstützung**

Unterstützung für On-Premise-Installationen von Adobe Individualization Server, um die Individualisierungsanforderung des Kunden so anzupassen, dass sie an einen anderen Endpunkt gesendet wird.

* **Auflösungsbasierter Ausgabeschutz**

DRM-Richtlinien können jetzt die höchstzulässige Auflösung festlegen, je nach den Funktionen des Geräts zum Ausgabeschutz. Beispiel: _Wenn HDCP verfügbar ist, können Inhalte mit einer Auflösung von bis zu 1080p abgespielt werden. Ist kein HDCP verfügbar, können Inhalte mit einer Auflösung von bis zu 480p abgespielt werden._

**Version 1.4.4**

* **Aktualisierung der Video Heartbeats Library (VHL) auf Version 1.4.1.1**

   * Es wurde die Möglichkeit hinzugefügt, verschiedene Analytics-Anwendungsfälle von anderen SDKs oder Playern mit den Adobe Analytics-Video-Grundlagen zu bündeln.
   * Das Anzeigen-Tracking wurde optimiert, indem die `trackAdBreakStart` und `trackAdBreakComplete` -Methoden. Die Werbeunterbrechung wird aus der `trackAdStart` und `trackAdComplete` Methodenaufrufe.
   * Die `playhead` -Eigenschaft ist beim Tracking von Anzeigen nicht mehr erforderlich.
   * Der Experience Cloud-ID-Dienst wird nun unterstützt.

* **Nielsen SDK-Integration**

Das TVSDK unterstützt jetzt das Senden von mTVR- und MDPR ID3-Beacons an das Nielsen-SDK ohne benutzerdefinierte Integration. Laden Sie zunächst das Nielsen iOS App SDK 3.1.2.19 herunter und befolgen Sie die Anweisungen im iOS-Programmierhandbuch.

**Version 1.4.0**

* **Blackout-Signalisierung mit Ersatz für alternativen Inhalt**

Als Teil des TVSDK-Updates für 1.4 unterstützt das TVSDK jetzt auch das Wechseln in regionale Blackouts und das Zurückkehren aus linearen Inhalten. Das TVSDK kann jetzt zwei Manifestdateien parallel, Hauptdatei und alternative verarbeiten, um Blackout-Signale zu überwachen, selbst wenn anstelle der ursprünglichen Programmierung alternative Programmierung angezeigt wird.

* **C3-Anzeigen entfernen/ersetzen**

Jetzt ist keine zusätzliche Vorbereitung erforderlich, um neue Anzeigen dynamisch in Video-On-Demand-Assets (VOD) einzufügen, die aus dem C3-Fenster herauskommen. Das TVSDK bietet jetzt eine API zum Entfernen benutzerdefinierter Inhaltsbereiche und zum dynamischen Einfügen neuer Anzeigen. Diese leistungsstarke neue Funktion ist auch in Fällen nützlich, in denen Live-/lineare Inhalte während der Übertragung bereitgestellt werden und sofort zur Verwendung als On-Demand-Inhalt abgerufen werden, ohne dass genügend Zeit für die Bereinigung des Assets vorhanden ist.

## Gelöste Probleme {#resolved-issues}

Wenn die Lösung mit einem gemeldeten Problem verbunden ist, wird eine Zendesk-Referenz angezeigt, z. B. ZD#xxxxx.

<!-- 

Comment Type: draft

 <p>All TVSDK customers who use CRS are strongly encouraged to upgrade to TVSDK 1.4.39 or latest on iOS and Android. This upgrade is a drop-in replacement to the existing app implementation. After the upgrade, check for the CRS creative URL requests in a proxy tool (for example, Charles) to verify that the version in the path reflects version 3.1. For example:</p> 
 <p><span class="code">https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8</span></p> 

-->

<!--
Comment Type: draft

 <p>TVSDK versions earlier than version 1.4.28 sometimes exhibit a long delay in the startup time when ad-enabled content is played on devices that are running on iOS 10. To resolve this issue, upgrade to version 1.4.28 or later. Version 1.4.28 was released on August 31, 2016, and iOS 10 was released on September 13, 2016.</p> 
-->

**iOS TVSDK 3.13**

* (ZD 42085) - Probleme mit der Wiedergabe in CMAF-Streams.

* (ZD-43215) - Absturz, wenn der Player während einer Anzeige geschlossen wird.

* (ZD 43210) - Die iOS HLS-Wiedergabe friert ein, wenn der WebVTT-Untertitel aktiviert ist.

**iOS TVSDK 3.12**

* Der Live-Stream schlägt nach 15 Minuten Wiedergabe fehl, wenn TVSDK für iOS 3.10 verwendet wird.

### Behobene Probleme in den vorherigen Versionen {#resolved-issues-previous}

**iOS TVSDK 3.11**

* (ZD#40998) - Die `isFallbackOnInvalidCreativeEnabled` führt zum Absturz der Anwendung.

* (ZD#41289) - `NSInvalidArgumentException` mit der Methode `customParams` führt zum Absturz der Anwendung.

**iOS TVSDK 3.10**

(ZD#40943) - TVSDK-Player löst nicht aus `PTMediaPlayerStatusError` Benachrichtigung, wenn das Netzwerk nicht verfügbar ist.

**iOS TVSDK 3.9**

(ZD#40272) - iOS TVSDK kann VTT-Untertitel nicht mit dem Fehler 101001 wiedergeben und führt zum Einfrieren der App.

**iOS TVSDK 3.8**

* (ZD#40087) - iOS stürzt mit Player-Fehler für abgelaufenen VOD-Inhalt ab.

* (ZD#40083) - Pre-Roll-Anzeigen spielen nicht für Livestream mit `OpportunityGenerator` und der Player gibt Fehler.

* (ZD#39828) - `CurrentItem` -Eigenschaft fehlt die Nullability-Anmerkung und führt zum Absturz des Players, wenn der in der Benachrichtigung enthaltene Player-Status `PTMediaPlayerStatusStopped`.

**iOS TVSDK 3.7**

(ZD#38961) - Inhalt kann nach Abschluss der Wiedergabe eines Inhalts nicht im PiP-Fenster (Picture-in-Picture) wiedergegeben werden, wenn mehrere Inhalte für die Wiedergabe auf dem PiP konfiguriert sind.

**iOS TVSDK 3.6**

Keine neuen Probleme in dieser Version.

**iOS TVSDK 3.5**

Keine neuen Probleme in dieser Version.

**Version 3.3**

(ZD#37820) - Die Zulassungsliste für die benutzerdefinierte Kopfzeile HS-ID, HS-SSAI-TAG wurde hinzugefügt.

**Version 3.2**

* **Ticket#36588** : Player-Absturz wird beobachtet, wenn die MediaPlayer-STOP-Methode aufgerufen wird.

Es wurde ein zeitweiliger Absturz behoben, der beobachtet wurde, wenn die STOP-Methode für einige Streams mit Untertiteln aufgerufen wurde.

* **Ticket#37080** - Duplizierte Anforderungen für Manifestaufrufe.
Korrektur der doppelten Anfragen, die während der Wiedergabe für Manifest-URLs gestellt wurden. TVSDK führt jetzt einen Aufruf pro Manifest durch.

* **Ticket#37** - CRS-Normalisierungsregel schlägt mit dem EQ-Übereinstimmungstyp fehl. Es wurde ein Fall behoben, bei dem der Player zum Absturz führte, wenn mit der letzten Normalisierungsregel für Hostnamen mit dem Übereinstimmungstyp &quot;eq&quot;gefunden wurde.

**Version 3.1**

**Ticket #36313** - Intermittierende unvorhersehbare Ergebnisse während linearen Anzeigenunterbrechungen Feste zeitweise wiedergegebene Wiedergabe während linearen Werbeunterbrechungen im Live-Stream.

**Version 3.0.1**

**Ticket36948** - CRS - Die Reihenfolge der Asset-Auswahl ist in iOS 12 inkonsistent. Das für CRS ausgewählte Asset ist nicht immer die Variante mit der höchsten Qualität, die in einer VAST- oder VMAP-Antwort zurückgegeben wird.

**Version 3.0**

* **Ticket35311** - Der Player-Status wird während einer Unterbrechung des Anrufs nicht angehalten. Der Interrupt-Handler wurde hinzugefügt, um die Unterbrechung des Players zu verhindern. Nach einer Unterbrechung wird der Player-Status angehalten und anschließend wird die Wiedergabe fortgesetzt, wenn Sie auf die Wiedergabeschaltfläche klicken.

* **Ticket36685** - Live-Assets - Zeitabweichung mit Player-Zeitfortschritt und SCTE-Markierungszeit Die richtige Zeit wird für die SCTE-Markierungen berechnet, die vor dem Live-Point liegen.

* **Ticket36492** - `currentTime` und `localTime` werden nicht aktualisiert, wenn Sie während der aktuellen Zeit des angehaltenen Status Auf eine neue Position suchen, kann jetzt auf null gesetzt werden, falls der Player angehalten wird; früher wurde die aktuelle Zeit nur im Wiedergabestatus auf null gesetzt.

**Version 1.4.45**

* **Ticket36294** - iOS TVSDK funktioniert nicht mit Xcode 10 Korrektur der Kompilierungsprobleme mit TVSDK in XCode 10. Aufgrund der XCode-zehn-Anforderungen erfordern Apps, die auf TVSDK für iOS ab Version 1.4.45 basieren, ein minimales Bereitstellungsziel als iOS 7.0

* **Ticket36321** - Diskrepanz, beobachtet im angestrebten Bereich zwischen `PTMediaPlayer` und `AVPlayer` Instanz in _Wiedergabe_ state.

* **Ticket36493** - `libstdc++` Support für iOS 12 Korrektur der Kompilierungsprobleme mit TVSDK in iOS 12. Für Apps, die auf TVSDK für iOS ab Version 1.4.45 basieren, ist ein minimales Bereitstellungsziel als iOS 7.0 erforderlich.

**Version 1.4.44**

* **Ticket34683** - Der Fortschritt der Anzeigenwiedergabe wird negativ

Zusätzliche Prüfungen, die durchgeführt werden, um den Fall zu verarbeiten, wenn eine Abweichung zwischen der vom Anzeigen-Server gemeldeten Dauer und dem tatsächlichen Anzeigeninhalt besteht.

* **Ticket34801** - `currentTime` und `localTime` wurden nicht aktualisiert, wenn bei der Suche nach einer neuen Position während der Paused-Status Die aktuelle Zeit des Players kann jetzt auf null gesetzt werden, falls sich der Player im Pausenstatus befindet. früher wurde die aktuelle Zeit nur im Wiedergabestatus auf null gesetzt.

* **Ticket35037** - Wiedergabe von Rückhalteeinrichtungen mit schlechter URL beim Zurückkehren aus der signal-basierten Anzeigeneinfügung
Verbesserte Fehlerbehebung für das geschlossene Problem #34385 in Version 1.4.42. Der Code für die Prüfung und Ausnahmebehandlung von isCancelled wurde hinzugefügt, um die Vorgangswarteschlange stabiler zu machen.

**Version 1.4.43**

* (ZD#32990) - iOS: Wiedergabe von Inhalten anstelle von Anzeigen auf einigen Cue-Punkten. `selectedMediaOptionInMediaSelectionGroup` Die API, die Teil der AVPlayerItem-Oberfläche war, wurde jetzt unter `AVMediaSelection` in iOS 11. Das Problem wurde mit dieser neuen API behoben.

* (ZD#33683) TVSDK entfernt `==` aus den Metadaten-Zeichenfolgen. Das Problem wurde in der Parsing-Logik behoben.

* (ZD#33905) - iOS TVSDK führt Aufrufe an die Manifestdateien mit zwei Benutzeragenten durch. Das Problem mit dem Benutzeragenten wurde im ersten m3u8-Aufruf behoben (Neuinstallationsfall). Die M3u8-Benutzer verfügen jetzt über die gleichen Benutzeragenten für alle Aufrufe.

* (ZD#34293) - In LINEAR-Streams eingefügte Vorrollen werden in iOS11 nicht korrekt wiedergegeben. Das Problem wurde für Pre-Roll-Anzeigen behoben.

* (ZD#34684) - Wenn die Richtlinie zum Überspringen einer Anzeige angewendet wird, werden Pre-Roll-Anzeigenrahmen für einige Sekunden angezeigt. eine neue API, `enableVodPreroll` wurde eingeführt, um die Pre-Roll-Wiedergabe in der VOD-Wiedergabe zu deaktivieren. Der Standardwert für diese API lautet _Ja_. Die API stellt sicher, dass die Zuordnung von Anzeigeninhalten im Hauptinhalt übersprungen wird.

* (ZD#34765) - Nach dem Aufruf von `stop()`, werden nur wenige Transport Streams-Segmente heruntergeladen. Der `Stop()` API, um den Download der zusätzlichen Segmente zu vermeiden.

* (ZD#34865) - Pre-Roll-Anzeigen für [!DNL Livestream] in iOS abgeschnitten sind. Im Zusammenhang mit iOS11 wird dieses Problem durch das Hinzufügen einer zusätzlichen Prüfung behoben, um zu überprüfen, ob es sich bei dem Stream um Pre-Roll- oder Hauptinhalte handelt.

* (ZD#35093) - Es wurde ein Failover-Szenario behoben, bei dem die Wiedergabe nicht zum Backup-Stream wechselt, wenn die Primäre Variante des Streams beim Start fehlschlägt (gibt 404 zurück).

**1.4.42 (1.4.42.118)**

* (ZD#34385) - Die Wiedergabe wird beim Zurückkehren aus der signal-basierten Anzeigeneinfügung mit einer schlechten URL angehalten.

   Erhöhen Sie die maximale Anzahl gleichzeitiger Treffer für `CustomAVAssetLoaderOperations`, damit das Manifestlesen weiterhin ausgeführt werden kann.

* (ZD#34373) - Endbenutzer können nicht auf HDMI-verbundene Geräte streamen, wenn die Stream-Aufzeichnung verboten ist.

* (ZD#32678) - TVSDK erfasst nicht die richtigen Anzeigen-IDs in iOS.

   Die Anzeigen-ID des endgültigen Anzeigenmotivs wird jetzt in VHL-Pings erfasst, wenn VAST-/VMAP-Umleitungen vorhanden sind.

* (ZD#33904) - TVSDK ist nicht für AVFoundation-Benachrichtigungen registriert `AVAudioSessionMediaServicesWereLostNotification` und `AVAudioSessionMediaServicesWereResetNotification`.

   `PTMediaServicesWereLostNotification` und `PTMediaServicesWereResetNotification` kann jetzt in der Player-App registriert werden, um die Benachrichtigungen abzurufen, wenn Media-Dienste zurückgesetzt oder verloren gehen.

* (ZD#33815) - Kunden können ihre Priorisierungs- und Normalisierungs-CRS-Regeln nicht aktualisieren, ohne eine App-Aktualisierung erforderlich zu machen.

   Der `getCRSRulesJsonURL` und `setCRSRulesJsonURL` APIs für das iOS TVSDK .

**Version 1.4.41 (1.4.41.76)**

* (ZD #34464) - Probleme beim Erstellen einer Referenz-App mit TVSDK Version 1.4.41

   Ab dieser Version ist Xcode 9 für die Kompilierung von TVSDK für iOS erforderlich.
* (ZD #29456) - Airplay startet im Status &quot;Angehalten&quot;

   Fehlerkorrektur - Das Pausenproblem wurde behoben, das auftrat, wenn das Video bei der Eingabe von Airplay angehalten wurde.
* (ZD #30371) - AdBreak-Startzeitänderungen, wenn mehr als zwei Anzeigen in einen linearen Stream eingefügt werden

   Behebung des Fehlers, durch den beim Versuch, Inhalte auf Apple TV wiederzugeben, die Wiedergabe vollständig verhindert wurde
* (ZD #32146)- Nein `PTMediaPlayerStatusError` wird für HLS Live-Inhalte beim Blockieren der iOS 11 dev Beta empfangen

   Nein `PTMediaPlayerStatusError` wird für HLS Live- und VOD-Inhalte beim Blockieren mit Charles empfangen (Drop-Verbindung und 403).

* (ZD #29242) - Die Wiedergabe von Airplay-Videos schlägt mit aktivierten Anzeigen fehl.

   Wenn Anzeigen aktiviert sind und AirPlay die Wiedergabe eines Videos startet, wird die Videowiedergabe nie gestartet und es wird kein Fehler angezeigt.

* (ZD#3341) - `DRMInterface.h` Trigger erstellen Warnungen in Xcode 9.

   Es wurden zwei Blockprototypen in `DRMInterface.h` fehlten, da das Wort &quot;void&quot;in ihren Parameterlisten fehlte.

* (ZD#31979) - Wird nicht kompiliert/ausgeführt, wenn es für iPhone 7/iPhone7+ iOS 10 oder höher ist.

   Die Korrektur des Kompilierens von IB-Dokumenten für älter als iOS 7 wird nicht mehr unterstützt.

* (ZD#32920) - Leerer Bildschirm innerhalb einer Werbeunterbrechung und ohne Abschluss einer Werbeunterbrechung.

   Wenn eine Werbeunterbrechung Anzeigeninstanzen präsentiert und nach Abschluss einer Anzeigeninstanz ein leerer Bildschirm angezeigt wird.

* (ZD#32509) - iOS 11-Bildschirmaufzeichnung deaktivieren Deaktiviert die Bildschirmaufzeichnung in iOS 11.

* (ZD#33179) - Intermittierender Ereignisfehler auf iOS11.

   Behebung des Ereignisfehlers in iOS 11.

**Version 1.4.40** (1.4.40.72)

* (ZD #32465) - Player kann keine zusammengeführten Wiedergabelisten verarbeiten.

   Aufruf `finishLoadingWithError`(mit: Fehler) für die AV-Stiftung, um alternative Streams/Trigger-Failover zu testen.

* (ZD #31951) - TVSDK-Fehler während Lizenzrotationen.

   Fehlerkorrektur - Die Lizenzrotation funktioniert jetzt einwandfrei.
* (ZD #31951) - Leerer Bildschirm innerhalb einer Werbeunterbrechung und ohne Abschluss einer Werbeunterbrechung.

   Behebung eines Problems, bei dem Facebook VPAID-Anzeigen häufig mehrere CDATA-Blöcke in einer einzigen zurückgaben `<AdParameters>` VAST-Knoten.
* (ZD #33336) - iOS TVSDK - Anzeigen-Pods werden nicht ausgefüllt, obwohl von Freewheel genügend Anzeigen zurückgegeben werden.

   Eine über- und untergeordnete Beziehung zwischen Sequenzanzeige und Fallback-Anzeige und Sortierung basierend auf der übergeordneten Sequenz und dem Index wurde erstellt.

**Version 1.4.39** (1.4.39.43)

* (ZD #32178) - iOS TVSDK-Version ist inkorrekt.

   Die TVSDK-Versionsausgabe in den Protokolldateien war 1.0.211. Es wurde ein Fehler behoben, der die Ausgabe der richtigen Version ermöglichte.

* (ZD #32199) - Lazy Ad loading - Video wird für den Inhalt nicht angezeigt.

   Die lokale Zeitleiste von AdBreak, die zuvor nicht initialisiert wurde, wird jetzt vor der Verwendung aktualisiert.

* (ZD #27528) - Video, Audio oder beides frieren 1-45 Sekunden nach dem Start der Wiedergabe eines Assets ein, wenn das sekundäre Audio in iOS 1.2 auf &quot;Nicht Standard&quot;eingestellt ist.

   Bereiten Sie Audiospuren im Status Bereit vor und informieren Sie sie.

* (ZD #30411) - Sie können unerwartete Ergebnisse wie kein Audio oder falsches Audio erhalten, wenn Sie eine sekundäre Sap-Sprache wählen.

   Bereiten Sie Audiospuren im Status Bereit vor und informieren Sie sie.

* (ZD #32199) - Lazy Ad loading - Video wird für den Inhalt nicht angezeigt.

   Die lokale Zeitleiste von AdBreak, die zuvor nicht initialisiert wurde, wird jetzt vor der Verwendung aktualisiert.

* (ZD #27528) - Video, Audio oder beides frieren 1-45 Sekunden nach dem Start der Wiedergabe eines Assets ein, wenn das sekundäre Audio in iOS 1.2 auf &quot;Nicht Standard&quot;eingestellt ist.

   Bereiten Sie Audiospuren im Status Bereit vor und informieren Sie sie.

* (ZD #30411) - Sie können unerwartete Ergebnisse wie kein Audio oder falsches Audio erhalten, wenn Sie eine sekundäre Sap-Sprache wählen.

   Bereiten Sie Audiospuren im Status Bereit vor und informieren Sie sie.

**Version 1.4.38** (1.4.38.860)

* (ZD #29281) - iOS: Hinzufügen von AdSystem und Creative ID zu CRS-Anforderungen

Nutzung der kreativen ID und des AdSystem in CRS-Anforderungen basierend auf CRS-Normalisierungsregeln

* (ZD #29176) - Absturz auf `PTAdPolicyDeligate` `satAdBreakAsWatched:position`

Absturz aufgrund leerer AdBreak wird jetzt verarbeitet.

* (ZD #30125) - Programmatische Anzeigen funktionieren nicht auf der iOS-Plattform

Unterstützung für programmatische Anzeigen in iOS hinzugefügt.

* (ZD #30782) - #EXT-X-PROGRAM-DATE-TIME Notification

Das zeitgesteuerte Metadatenereignis wird nicht für das Tag # EXT-X-PROGRAM-DATE-TIME mit LIVE DRM-Streams ausgelöst.

**Version 1.4.37 (1.4.37.842)**

* (ZD #28950 ) - Problem mit der VOD-Wiedergabe

Problem bei der Wiedergabe, wenn das Tag # EXT-X-PLAYLIST-TYPE im Stream auf &quot;Event&quot;anstatt auf &quot;VOD&quot;gesetzt ist

* (ZD #29281) - iOS: Hinzufügen von AdSystem und Creative ID zu CRS-Anforderungen

Verwendung von Creative Id und AdSystem in CRS-Anforderungen basierend auf CRS-Normalisierungsregeln.

* (ZD #29462) - TremorHub-Anzeige in A&amp;E VOD, die zu einem Absturz in iOS-Apps führt

**Version 1.4.36 (1.4.36.835)**

* (ZD #29418) - Fälle mit einer Dauer von 0 (#EXT-X-CUE-OUT:0.000) führen dazu, dass iOS TVSDK die Wiedergabe stoppt oder abstürzt.

Das Problem wurde behoben und die Wiedergabe wird ordnungsgemäß gestartet.

* (ZD #29462) - Ad in VOD verursacht einen Absturz auf iOS TVSDK .

Das Problem wurde behoben. iOS TVSDK generiert eine `exception(AUDNetworkAdInfo::initWithAdId)` und nicht verarbeitet werden. Die Ausnahme ist auf eine leere Anzeigen-ID zurückzuführen.

* (ZD #29281) - Hinzufügen von AdSystem und Creative ID zu CRS-Anforderungen.

Fügen Sie AdSystem und CreativeId als neue Parameter in den Anforderungen 1401 und 1403 hinzu (alle anderen Parameter bleiben gleich).

**Version 1.4.35** (1.4.35.830)

* (ZD #27830) - Muss den Unterschied zwischen geschlossenen Untertiteln und Untertiteln in iOS programmgesteuert ermitteln.

TVSDK stellt nun die beiden Typen zur Verfügung, die zum Filtern des erforderlichen Beschriftungstyps verwendet werden können.

* (ZD #29160) - EXT-X-CUE-OUT-Anzeigen werden auf TVSDK iOS nicht richtig aufgeteilt.

Mit EXT-X-CUE-OUT-MIME-Anzeige wird jetzt wiedergegeben.

* (ZD #29100) - Die App stürzt ab, wenn der Benutzer zum Ende eines Films scrubbt.

Mehrere Abstürze im Zusammenhang mit der Synchronisierung wurden behoben.

* (ZD #28785), (ZD #27712) und (ZD #25076) - Die iOS-App stürzt während der großen Live-Ereignisse ab.

Mehrere Abstürze im Zusammenhang mit der Synchronisierung wurden behoben.

**Version 1.4.34** (1.4.34.815 für iOS 6.0+)

* (ZD #28481) - FER-Ausfall aufgrund des falschen Schlüssels, der am Ende einer Werbeunterbrechung für diese FER-Streams angehängt wird

Bei einem FER-Stream wird der Schlüssel vor der Werbeunterbrechung nach dem Ende der Werbeunterbrechung eingefügt. Dieses Problem wurde behoben, indem die *last seen key* am Ende der Werbeunterbrechung.

**Version 1.4.33** (1.4.33.803 für iOS 6.0+)

* (ZD# 21701) CRS für Unterkonten aktivieren

Aktiviert durch Senden der ursprünglichen kreativen URL für die CRS-Anforderung 1401 anstelle der normalisierten URL gemäß der Anforderung für das CRS-Backend.

* (ZD# 26218) - `PSDKResources.bundle` Ladeproblem

Dieses Problem wurde behoben, indem das Laden der Ressource so aktualisiert wurde, dass es von allen verfügbaren Bundles aussieht.

* (ZD# 27460) Midroll First Ad-Aufruf - POST zu `cdn.auditude.com` gibt 403 zurück.

Das neue CDN-Konto kann eine POST-CDN-Anfrage nicht verarbeiten. Dieses Problem wurde behoben, indem der Code aktualisiert wurde, um die `cdn.auditude.com` -Anzeigenanforderung GET anstelle von POST sein.

**Version 1.4.32** (1.4.32.792 für iOS 6.0+)

* (ZD# 27132) Unterstützung von Dezimalwerten für VMAP-Anzeigenunterbrechungen.

Wenn Inhalte nicht entlang der definierten Werbeunterbrechungen segmentiert wurden, führten Ganzzahlen zu unerwarteten Anzeigenplatzierungen. Das Problem wurde behoben, indem die Dezimalwerte nicht in Ganzzahlen konvertiert wurden.

* (ZD# 27189) AES-Inhalte mit dem Tag EXT-X-DISCONTINUITY-SEQUENCE werden nicht korrekt wiedergegeben.

Das Problem wurde behoben, indem das -Tag am Anfang der Wiedergabeliste platziert wurde.

**Version 1.4.31** (1.4.31.785 für iOS 6.0+)

* (ZD# 24528) Implementieren von TVSDK-Nutzungsmetriken für die Rechnungsstellung

Weitere Informationen finden Sie unter [Abrechnungsmetriken].

* (ZD# 24642) Bild-in-Bild-Unterstützung für TVSDK

Das Bild-im-Bild-Feature, das manchmal nicht richtig funktionierte, wurde behoben.

* (ZD# 25246) Falsche Anzeigenunterbrechungssignale

Dieses Problem wurde behoben, indem Diskontinuitäts-Tags über Variantenmanifeste hinweg ausgerichtet wurden.

* (ZD# 26218) Der Prozess zum Erstellen von Anwendungen wird beim Versuch, `PSDKLibrary.framework` im Anwendungs-Framework des Kunden

Dieses Problem wurde durch die Verpackung der `PSDKLibrary.framework` wie gewünscht.

* (ZD# 26364) Multi-CDN-Unterstützung für CRS-Anzeigen

Weitere Informationen finden Sie unter Mehrere CDN-Unterstützung für CRS-Anzeigenbereitstellung.

* (ZD# 27028) Verzögerung bei der Wiedergabe einiger Streams in iOS 10.

Dieses Problem wurde behoben, indem eine Problemumgehung für Streams ohne M3U8-Erweiterung bereitgestellt wurde.

**Version 1.4.30** (1.4.30.754 für iOS 6.0+)

In dieser Version wurden die folgenden Probleme für TVSDK behoben:

* (ZD# 24180) Fügen Sie der Zulassungsliste eine benutzerdefinierte Kopfzeile hinzu.

Der TVSDK-Zulassungsliste wurde eine neue benutzerdefinierte Kopfzeile hinzugefügt.

* (ZD# 25016) Failover-Stream wird zufällig ausgewählt, wenn ABR-Steuerungsparameter festgelegt werden

Dieses Problem wurde behoben, indem die ABR-Streams in der Reihenfolge beibehalten wurden, in der die ABR-Einstellungen mit dem `initialBitrate` -Einstellung in einem Stream, der Failover-URLs enthält. Dadurch wird verhindert, dass die Failover-Streams anstelle von &quot;primary&quot;wiedergegeben werden.

* (ZD# 25076) Absturz auf `PTAuditudeAdResolver loadComplete`

Das Problem, bei dem während des schnellen Starts/Stopps mehrerer PTMediaPlayer-Instanzen mit Anzeigen ein Absturz auftrat, wurde behoben.

* (ZD# 25960) Es werden keine zusätzlichen abonnierten Tags ausgelöst, die Benachrichtigungen zu Änderungen an Metadaten auslösen

Das Problem, dass ein abonniertes Tag nicht benachrichtigt wird, wenn es angezeigt wird, bevor das erste Segment im Manifest angezeigt wird, wurde behoben.

* (ZD# 26084) PSDK mit 106000.101000.-11833 Decoder konnte beim Übergang von der letzten Werbeunterbrechung zurück zu Unterhaltungsinhalten keinen Fehler finden

Wenn die letzte Startzeit der Werbeunterbrechung vom VMAP vor Abschluss der Gesamtdauer fällt, wird der Schlüssel unter bestimmten Bedingungen erst nach dem Ende der letzten Werbeunterbrechung eingefügt. Dieses Problem wurde behoben.

* Die Video Heartbeat Library (VHL) wurde auf Version 1.5.9 aktualisiert, um die folgenden Probleme zu beheben:

* (ZD #22351) VHL - Analytics: Dauer des Live-Video-Assets

Dieses Problem wurde behoben, indem die Variable  `assetDuration`  API zu `PTVideoAnalyticsTrackingMetadata` , um die Asset-Dauer für Live-/Linear-Streams zu aktualisieren und eine Logik zur Überprüfung des Live-Streams bereitzustellen.

* (ZD# 22675) VHL - Analytics: Aktualisieren der Dauer von Live-Video-Assets

Dieses Problem ist mit ZD #22351 identisch.

* (ZD #25908) VHL - Analytics: Adobe Heartbeat-Ereignisabsturz

Dieses Problem wurde behoben, indem die Implementierung so aktualisiert wurde, dass die neueste Version von VHL für iOS Version 1.5.9 verwendet wird, um Stabilität und Leistung zu verbessern.

* (ZD #25956) VHL - Analytics: Absturz bei wiederholter Videowiedergabe

Dieses Problem ist mit ZD #25908 identisch.

**Version 1.4.29** (1.4.29.743)

* (ZD# 23901) Anzeigen von Drittanbietern werden nicht wiedergegeben

Dieses Problem wurde behoben, indem zur URL-Struktur von CRS v3 gewechselt wurde, um die Zonen-ID in die neu gepackte URL aufzunehmen.

* (ZD #25183) Probleme mit der DRM-Wiedergabe auf tvOS und iOS

Dieses Problem wurde behoben, indem Unterstützung für mehrere Schlüssel-Tags bereitgestellt wurde, die für die Unterstützung mehrerer DRM benötigt werden.

* (ZD# 25334) TVSDK kann freigegebene cDVR-Inhalte nicht wiedergeben

Dieses Problem wurde behoben, indem TVSDK daran gehindert wurde, leere Zeichenfolgen in absolute URLs zu konvertieren.

* (ZD# 25347) Festlegen eines benutzerdefinierten HTTP-Headers auf AVURLAsset

Unterstützung von benutzerdefinierten Kopfzeilen für Segmentanforderungen über die `PTNetworkConfiguration` -Klasse hinzugefügt wurde.

**Version 1.4.28** (1.4.28.722)

* (ZD #24549) Mehrere Anzeigen-Tracking-Aufrufe

Dieses Problem wurde behoben, indem der Timeline-Manager aktualisiert wurde, um auf Benachrichtigungen zu einem bestimmten Objekt zu warten, wenn mehrere Player erstellt werden.

* (ZD #24758) `PTManifestLogger` unterstützt iOS 8 nicht

Dieses Problem wurde behoben, indem die Bibliothek des Logger-Dienstprogramms auf das Bereitstellungsziel der Version 7.0 aktualisiert wurde.

* (ZD #24775) Verzögerter Stream aufgrund von Anzeigen

Dieses Problem wurde behoben, indem die Dauer der Verschiebung auf Ereignisspiellisten korrekt berechnet wurde.

* (ZD #24799) Einige der Episoden werden nicht in der iOS APP wiedergegeben

Dieses Problem wurde durch die Verwendung des lokalen Webservers für Untertitel behoben, wenn die WebVTT-Dateien geografisch eingeschränkt sind.

**Version 1.4.27** (1.4.27.711) für iOS 6.0+

* (ZD #24089) - Optimierungen für die Anzeigenauflösung in langen DVR-Streams

Dieses Problem wurde behoben, indem mehrere Optimierungen hinzugefügt wurden, um die für die Verarbeitung des DVR-Fensters in Live-/linearen Streams erforderliche Zeit zu verkürzen.

* (ZD #21554) - TVSDK-Fehler-Beacons werden nicht ausgelöst für `application-type = video/mp4`

Dieses Problem wurde behoben, indem der Player die richtigen Fehler-Tracking-URLs für ungültige Asset-Formate pingen konnte.

* (ZD #24424) - Absturz des Typs `EXC_BAD_ACCESS KERN_INVALID_ADDRESS` von innen stammt `PSDKLib` für iOS auf neueren Hardwaregeräten.

Der Absturz, der aufgrund einer nicht zugewiesenen Medienplayer-Instanz aufgetreten ist, wenn die Wiedergabe zwischen verschiedenen Streams schnell umgeschaltet wird, wurde behoben.

* (ZD #24575) - Absturz in TVSDK auf 32-Bit-Geräten bei `enableDebugLog=true`

Das Problem im Protokollformat, das den Absturz auf 32-Bit-Geräten verursachte, wenn die Protokollierung aktiviert ist, wurde behoben.

**Version 1.4.26** (1.4.26.702) für iOS 6.0+

* (ZD# 20213) - TVSDK FW muss dynamisch/modularisiert für XCode7 sein

Korrigiert durch Aktualisierung der Bibliotheken mit Modulunterstützung

**Version 1.4.25** (1.4.25.684) für iOS 6.0+

* (ZD #19629) - Live-Video wird angehalten, wenn Airplay zu ATV 4 aufgerufen wird

Dieses Problem wurde behoben, indem eine Wartezeit hinzugefügt wurde, nachdem alte Elemente entfernt wurden, aber bevor neue Elemente zum `AVQueuePlayer`. Ohne Wartezeit werden Benachrichtigungen an das falsche Element gesendet.

* (ZD #19856) - Standardmäßig werden keine Untertitel angezeigt, wenn sie aktiviert sind

Die Probleme in der Webvtt-Wiedergabeliste, die dazu führten, dass die Untertitel nicht korrekt angezeigt wurden, wurden behoben.

* (ZD #21590) - Videoleistung und -verfolgung in den neuesten Origin Builds

Das Problem mit der fehlenden Videolänge in `VideoAnalytics` wurde behoben.

* (ZD #20202) - Beim Festlegen eines benutzerdefinierten Untertitelstils stürzt die iOS-App ab

Dieses Problem wurde behoben, indem beim Festlegen von Untertitelstilen zusätzliche Null-Objekt-Prüfungen hinzugefügt wurden.

* (ZD #20709) - Videolänge, die beim Video-Start-Tracking als 0 gemeldet wird

Dieses Problem ist mit dem (ZD #21590) identisch.

* (ZD #22280) - Analytics-Videolänge auf 0 gesetzt

Dieses Problem ist mit dem (ZD #21590) identisch.

* (ZD #22592) - Probleme mit Airplay in Primetime

Dieses Problem ist mit dem (ZD #19629) identisch.

* (ZD#22922) - Manueller Bitratenwechsel für iOS

Dieses Problem wurde behoben, indem eine Option zur Angabe der maximalen Bitrate bereitgestellt wurde.

* (ZD #23084) - Apple Compliance for IPv6-only Networks

Die Symbole, die von Apple für die IPv6-Kompatibilität nicht empfohlen wurden, wurden entfernt.

**Version 1.4.24** (1.4.24.661) für iOS 6.0+

* ZD #2548) - Primetime-Unterstützung für interaktive Werbung auf Mobilgeräten - VPAID 2.0

Dieses Problem wurde behoben, indem die Logik so aktualisiert wurde, dass die Player-Ansicht eingeblendet wird, wenn eine VPAID-Anzeige nicht wiedergegeben werden kann.

* (ZD #20101) - Benutzerdefinierte Kapitelimplementierung löst Kapitelstartereignis während der Anzeigenwiedergabe aus

Dieses Problem wurde durch die Aktualisierung von `VideoAnalyticsTracker` , um beim Übergang zwischen Kapitel- und Nicht-Kapitel-Begrenzungen den Kapitelstart/-abschluss richtig zu erkennen.

* (ZD #20784) - Analytics: Auslösen von Inhaltsbeendigungen für Live-Videoübergänge

Dieses Problem wurde behoben, indem eine Logik hinzugefügt wurde, um den Abschluss von Inhalten während einer Videoverfolgungssitzung manuell Trigger.

Die folgenden Bibliotheken wurden aktualisiert:

* AdobeMobile-Bibliothek auf 4.10.0
* VHL-Bibliothek zu 1.5.6
* VHL-Nielsen-Bibliothek zu 1.6.7
* (ZD #21855) - Untertitel werden nach dem Mid-Roll nicht abgespielt

In diesem Problem führten doppelte Diskontinuitäts-Tags dazu, dass nach der Mid-Roll keine Untertitel angezeigt wurden. Dieses Problem wurde behoben, indem die Diskontinuitäts-Tags entfernt wurden, die nebeneinander liegen.

* (ZD #21994) - String out-of-bounds in `PTHLSUtils`

Die wahrscheinlichste Ursache des Absturzes ist, wenn ein EXT-X-KEY über eine URL verfügt, die von Anführungszeichen umgeben ist.

* ZD #22074) - `AUDVAST` Absturz auf iOS einmal pro Minute

In Version 1.4.23 wurde der Absturz behoben, der durch das Vorhandensein unsicherer Zeichen in einer VAST-Umleitungs-URL verursacht wurde. TVSDK hat diese Anzeigen jedoch weiterhin übersprungen.

Dieses Problem wurde behoben, indem die unsicheren Zeichen verarbeitet und die Anzeigen wiedergegeben wurden.

* (ZD #22694) - `PTMediaPlayer`.  Ansicht nach Player ausgeblendet

Dieses Problem wurde behoben, indem die Logik so aktualisiert wurde, dass die Player-Ansicht eingeblendet wird, wenn eine VPAID-Anzeige nicht wiedergegeben werden kann.

**Version 1.4.23** (1.4.23.641) für iOS 6.0+

* (ZD #18016) - Keine Antwort vom Primetime SDK mit schlechter Netzwerkbedingung

Dieses Problem wurde behoben, indem die Fehlerbenachrichtigung bei einem schwerwiegenden Fehler von `AVFoundation` auftritt und damit die App den Neustart nach dem Fehler verarbeiten kann.

* (ZD #20580) - Absturz in `PTSplicerManager`

Dieses Problem wurde behoben, indem ein zusätzlicher Schutz vor gleichzeitigen Problemen bereitgestellt wurde, die den Absturz verursachen.

* (ZD #21782) - iOS-Fehlercode 10100

Das Problem, dass das TVSDK beim Starten der Wiedergabe in Adobe Access DRM-Streams einen 101000-Fehler zurückgab, wurde behoben.

* (ZD #21889) - Die Wiedergabe von Online-Anzeigen und Offline-Inhalten schlägt fehl

Das Problem, bei dem die Wiedergabe fehlschlug, nachdem eine Anzeige auf AES-verschlüsselten Offline-Inhalten fehlschlug, wurde behoben.

* (ZD #22074) - AUDVAST-Absturz tritt einmal pro Minute auf iOS auf

Dieses Problem wurde behoben, indem die Handhabung von VAST-Anzeigen-Tags von Drittanbietern verbessert wurde, die ungültige Zeichen in der URL enthalten.

* (ZD #2257) - TVSDK kann DRM-Stream nicht wiedergeben

Das Problem, bei dem das TVSDK, das beim Starten der Wiedergabe in Adobe Access DRM-Streams einen Fehler vom Typ 101000 zurückgab, wurde behoben.

**Version 1.4.22** (1.4.22.627) für iOS 6.0+

* (ZD #18709) - Absturz im TVSDK für iOS

Das Problem eines Absturzes in einigen Adobe Access DRM-geschützten Streams wurde behoben.

* (ZD #18850) - Aktualisieren der kreativen Auswahllogik basierend auf CRS-Regeln

Dieses Problem wurde behoben, indem eine .json -Konfigurationsdatei hinzugefügt wurde, um die Priorität der kreativen Auswahl anzugeben.

* (ZD #19770) - Protected AES Video Feed wird nicht mehr wiedergegeben

Das Problem, dass 302 umgeleitete Streams nicht abgespielt wurden, wurde behoben.

* (ZD #19629) - Live-Video wird angehalten, wenn Airplay zu ATV 4 aufgerufen wird

Dieses Problem wurde behoben, indem eine Behelfslösung für die Live-Videopause hinzugefügt wurde, wenn die Wiedergabe für Apple TV 4-Geräte aktiviert ist. Das Problem scheint eine Apple TV 4-Ausgabe zu sein.

* (ZD #21119) - Das TVSDK wird nach der Anzeigenwiedergabe angehalten

Unterstützung für AES-verschlüsselte Streams mit einer Sequenz IV während der Verwendung von Anzeigeneinfügungen hinzugefügt.

* (ZD #21125) - Rückgabe von Live-/linearen Werbeunterbrechungen früh

Es wurde Unterstützung für die Rückkehr von einer Werbeunterbrechung frühzeitig vor der Wiedergabe der Werbeunterbrechung bis zum Abschluss hinzugefügt. Die frühe Rückgabe wird durch ein benutzerdefiniertes Manifest-Tag angezeigt.

* (ZD #21224) - Airplay-Unterstützung für tokenisierte Streams von Akamai

APIs wurden zum `PTNetworkConfiguration` -Klasse zum Anhängen von Cookies als URL-Parameter an Segmente für bestimmte Akamai-tokenisierte Streams.

* (ZD #21287) - Fremdprotokoll

Ein Problem mit einigen Protokollanweisungen, die standardmäßig in der xcode-Konsole angezeigt werden, selbst wenn die Protokollierung deaktiviert ist, wurde behoben.

* (ZD #21446) - Ad Break-Ereignisse werden manchmal nicht vom TVSDK ausgelöst

In Ereignis-Streams werden Werbeunterbrechungen im vorherigen Release-Build nicht korrekt ausgelöst. Dieser Build behebt dieses Problem.

**Version 1.4.21** (1.4.21.605) für iOS 6.0+

* (ZD #20749) - Fallback überspringt nicht leere VAST-Antworten. Auslösen zusätzlicher Anzeigen-Tracking-URLs

Ein Problem mit doppelten Pings für Fallback-Anzeigen wurde behoben.

**Version 1.4.20** (1.4.20.590) für iOS 6.0+

* (ZD #18639) - Das TVSDK verwendet übermäßige CPU/Ressourcen für ein langes Hot-Recording-Asset.

Die übermäßige CPU-/Ressourcenbelegung wurde auf beiden Ebenen behoben. Zunächst muss die Funktion für die Zeitaktualisierung auf einer globalen Warteschlange anstatt des Haupt-Threads ausgeführt werden und die CPU-Auslastung für die Analyse des Manifests mit dem zuvor verarbeiteten und zwischengespeicherten m3u8 optimiert werden.

* (ZD #19349) - Pre-Roll-Anzeigen werden beim Einschränken der Netzwerkverbindung übersprungen.

Dieses Problem wurde behoben, indem ein Timeout-Ereignis (requestTimeout) für die Anwendung und die `adMetadata.adRequestTimeout` API zum Überschreiben des standardmäßigen 10-Sekunden-Timeouts.

* (ZD #19446) - Fehlende Benachrichtigung bei Live-Streams

Dieses Problem wurde behoben, indem die Anwendung das `EXT-X-PROGRAM-DATE-TIME` in Live-Streams.

* (ZD #19459) - Absturz bei der Vorbereitung von alternativem Audio mit `PTMediaPlayerItem` `prepareAudioOptionsWithAVMediaSelectionOptions`
* (ZD #19460) - Absturz - `[PTMediaPlayerItem prepareSubtitlesOptionsWithAVMediaSelectionOptions:nonForcedOptions:]`

Dieses Problem ist mit dem Zendesk #19459 identisch.

* (ZD #19574) - Das TVSDK gibt keine M3U8-Antwortdaten für DRM- oder Nicht-DRM-Inhalte zurück

Beim ersten Laden der Manifestdatei in `PTMediaPlayerItem.prepareToPlay`Wenn das Laden des Manifests fehlgeschlagen ist, meldet das TVSDK den Text der Fehlerantwort nicht an die Anwendung.

Dieses Problem wurde behoben, indem TVSDK die Fehlerantwort als Fehler an die Anwendung melden konnte.

* (ZD #19615) - Die Fallback-Logik funktioniert nicht

In der aktuellen Implementierung wurden Fallback-Anzeigen übersprungen und nicht neu verpackt, es sei denn, diese Anzeigen weisen das Format m3u8 auf. Dieses Problem wurde behoben, indem auch die Unterstützung für Neuverpackung von Fallback-Anzeigen hinzugefügt wurde.

* (ZD #19770) - Das TVSDK kann keine geschützten AES-Inhalte mit 302-Umleitung wiedergeben

Das Umleitungsproblem wurde behoben, da die Umleitungs-URL durch `cleanConnectionData` bevor sie zum Analysieren des Manifests verwendet werden konnte.

* (ZD #19856) - Untertitel werden für einige Bitraten nicht angezeigt, wenn sie standardmäßig aktiviert sind

Dieses Problem wurde behoben, indem der Fehler von iOS für die Streams behoben wurde, in denen die Untertitel nicht angezeigt wurden.

* (ZD #19868) - Das TVSDK stürzt ab, wenn ein ungültiger kreativer Benutzer zum Tracken gebracht wird

Der Absturz im TVSDK, bei dem die Zuordnung einer Instanz des riesigen Parsers fälschlicherweise aufgehoben wurde, wurde behoben.

* (ZD #20180) - VPAID-Anzeigen werden gelegentlich übersprungen

Der JavaScript-MIME-Typ wurde nicht immer einbezogen oder wurde als gültiger MIME-Typ betrachtet. Dieses Problem wurde behoben, indem JavaScript als gültiger MIME-Typ eingefügt wurde.

* (ZD #20749) - Fallback überspringt nicht leere VAST-Antworten. Auslösen zusätzlicher Anzeigen-Tracking-URLs

Das Problem, dass einige Kreative nicht neu verpackt werden, wurde behoben.

**Version 1.4.19** (1.4.19.563) für iOS 6.0+

* ZD #18639) - Das TVSDK verwendet übermäßige CPU/Ressourcen auf einem langwierigen Hot-Recording-Asset

Dieses Problem wurde behoben, indem das Umschreiben der DRM m3u8-Wiedergabeliste in Cache-Bit der Wiedergabeliste optimiert wurde, die zuvor umgeschrieben wurden. Dies ist am relevantesten, wenn Sie Live-m3u8-Streams wiedergeben, für die m3u8 nach jedem Segmentdownload heruntergeladen wird.

* (ZD#18956) - `player.drmManager` ist null, wenn der Haltepunkt im iOS Demo Player festgelegt ist

Dieses Problem wurde behoben, indem die `PTMediaPlayer.drmManager` API-Implementierung zur Übernahme von DRMManager aus dem DRM-Framework.

**Version 1.4.18** ( 1.4.18.557) für iOS 6.0+

* (ZD #18844) Tracking-Abspielleiste für Live-Inhalte im iOS-Player.

Dieses Problem wurde behoben, indem die Anwendungen einen eigenen Abspielleistenwert festlegen konnten.

* (Zendesk #18518) - Wenn der Videoname nicht angegeben ist, lautet der Name des TVSDK standardmäßig * PSDK-basierter Player.*

Dieses Problem wurde behoben, indem der Standardwert für den Player-Namen entfernt wurde.

**Version 1.4.17** (1.4.17.545) für iOS 6.0+

* (Zendesk #2228) - Verbessern Sie das TVSDK, um die JSON-Antwort des Abrufs eines Manifests zurückzugeben.

Anstatt einen Fehler zu senden, wenn der Inhalt nicht M3U8 ist, gibt das DRM-Framework eine Null-DRMMetadata zurück. Das Problem wurde behoben, indem Metadaten hinzugefügt wurden, um Inhalte verfügbar zu machen, wenn die Benachrichtigung M3U8_PARSER_ERROR auftritt.

* (Zendesk #2231) - Fehler beim Abrufen des Manifests, das in MediaPlayerNotification nicht verfügbar ist

Gleiche Auflösung wie Zendesk #2228

* (Zendesk #3304) - VAST 3.0 `[ERRORCODE]` Nicht befülltes Makro

Das Problem, bei dem die [!DNL Auditude] Das SDK kann kein Ping senden, wenn die Tracking-URL Leerzeichen am Anfang aufgelöst wurde.

* (Zendesk #17294) - Absturz [!DNL SecKeyRawSign]

Ein möglicher Absturz, bei dem der Code des Kunden die Schlüsselkette verwendet, wurde behoben.

* (Zendesk #18008) - Cookies für iOS8+ unterstützen tokenisierte Streams

Akamai-tokenisierte Streams erfordern, dass Cookies bei Segmentanfragen gesendet werden. Dies war in iOS 7 und früher nicht möglich. Ab iOS 8 hat Apple eine API hinzugefügt, mit der für Segmentanfragen Cookies übergeben werden können. Diese Unterstützung ist jetzt im TVSDK verfügbar. Es wurde auch Unterstützung für das Senden eines Benutzeragenten hinzugefügt, sofern verfügbar.

* (Zendesk #18166) - TVSDK 1.4.15 gibt Hunderte von Warnungen beim Kompilieren mit `DWARF` mit `dSYM` Dateioptionen

Alle Warnungen wurden behoben.

**Hinweis**: Für TVSDK wurden tvOS-kompatible Bibliotheken hinzugefügt.

**Version 1.4.16** (1.4.16.1454)

* Zendesk #3875 - Tab S stürzt während der Wiedergabe ab

Wiederherstellen der Abhängigkeit von OKHTTP [!DNL Auditude] für CRS, da TVSDK jetzt direkt die `httpurlconnection` anstatt curl. Das Problem wurde durch das Löschen von Ausnahmen behoben, bevor ein weiterer JNI-Aufruf durchgeführt wurde.

* (Zendesk #4487) - Tracking Linear Channel of Content

Das Problem wurde behoben, indem der Video Heartbeat-Tracker während einer linearen Stream-Wiedergabesitzung neu initialisiert wurde.

* (Zendesk #17919) - Android - Die Inhaltssuche verursacht den Heartbeat-Fehler

Das Problem bestand darin, den Heartbeat in einem Fehlerstatus zu beheben, wenn in einem Kapitel eine Suche vorhanden war

* (Zendesk #18053) - Anwendung, die TVSDK verwendet, stürzt auf Marshmallow ab

Das TVSDK stürzte unter Android™ M OS ab, wenn die TVSDK-Bibliothek einen Neon-Code verwendet, der YUV unterstützt `->` RGB-Farbkonvertierung. Dieses Problem wurde behoben, indem die Funktionen aktualisiert wurden, die dieses Problem verursachen, indem eine Nicht-Neon-Version von `code`.

* (Zendesk #18072) - Android M - Application Crash

Dieser Absturz tritt beim Aufrufen von `MediaCodecList` und `MediaCodecInfo` APIs bei der Überprüfung, ob Profil und Ebene unterstützt werden. Adobe sucht nach Google-Support für weitere Einblicke. Dieses Problem wurde behoben, indem eine temporäre Problemumgehung bereitgestellt wurde, indem alle Codec-Informationen vorzeitig geladen wurden, um zu vermeiden, dass diese APIs nur dann aufgerufen werden, wenn Codec-Informationen benötigt werden.

* (Zendesk #18074) - Arabische Untertitel, die nicht mit Android™ 6.0 auf Nexus funktionieren

Dieses Problem wurde durch die Unterstützung der Android™ CTS-Schriftzuordnung behoben.

**Version 1.4.15** (1.4.15.512) für iOS 6.0+

**Hinweis**: Das Nielsen-Modul wurde aus dem TVSDK-Build entfernt, aber das TVSDK wird bald mit einem neuen Nielsen-Integrationsmodul aktualisiert.

* (ZD #2228) - Fehler beim Abrufen des Manifests, der in nicht verfügbar ist `MediaPlayerNotification`

Metadaten wurden hinzugefügt, um Inhalte bei der Benachrichtigung verfügbar zu machen `M3U8_PARSER_ERROR` auftritt.

* (ZD #4437) - Abstürze innerhalb des Adobe Primetime SDK

Fehlerkorrektur - Es wurde ein gemeldeter Absturz bei der Vorbereitung von Untertiteln/alternativen Audioinhalten behoben.

* (ZD #4487) - Tracking Linear Channel of Content

Zulässige Neuinitialisierung des Video Heartbeat Tracker während einer linearen Stream-Wiedergabesitzung.

**Version 1.4.14** (1.4.14.498) für iOS 6.0+

* (ZD #17260) - Absturz bei `playlistManagerForURL`

Es wurde ein zeitweiliger Absturz aufgrund von Gleichzeitigkeitsproblemen behoben.

**Version 1.4.13** (iOS 6.0+)

* (ZD #3304) - VAST 3.0 `[ERRORCODE]` Nicht befülltes Makro

   * Der Fehlercode 400 wird angezeigt, wenn die Inline-Anzeige schlechte Kreativinhalte aufweist.
   * `[ERRORCODE]` -Makro ist URL-kodiert.

* (ZD #3865) Heartbeat-Integration mit IMA-Anzeigen

Es wurde ein Fehler behoben, durch den die Videolänge falsch gemeldet wurde.

* TVSDK-Demo-Player wurde aktualisiert, um iOS 9 zu unterstützen

Um iOS 9 ordnungsgemäß zu unterstützen, müssen Sie die Ausnahmen der Application Transportation Security konfigurieren. Für die Demo ist das ATS vollständig deaktiviert.

**Version 1.4.12** (1.4.12.464) für iOS 6.0+

* (ZD #4521) Client-seitiges CRS-Testen und SSAI

Fehlerhaftes Reverse MD5 in 3P-URL behoben.

**Version 1.4.12** (1.4.12.463) für iOS 6.0+

* (ZD #2751) CSAI und CRS / Verbesserung: Umgang mit dynamischen Elementen in bestimmten URLs von Mediendateien.

Der Creative Repackaging Service wurde aktualisiert, um Anzeigen mit dynamischen kreativen URLs ordnungsgemäß zu verarbeiten.

* (ZD #3654) Memory Leak in PSDK-Version nach 1.3.4.166

Speicherleck in `drmFramework` mit regelmäßiger Wiedergabe auf iOS 8.2-Geräten

* (ZD #3988) Die Vorbereitung wird bei der Suche nach der ersten Wiedergabe übersprungen.

Es wurde ein Fehler behoben, sodass Anzeigenrichtlinien ordnungsgemäß deaktiviert werden konnten.

* (ZD #4017) iOS-API anfordern, die Anzeigenwiedergabe bei der Rückwärtssuche zu erzwingen

Behoben mit Fehlerbehebung für ZD #4279

* (ZD #4279) HLS TVSDK-Anzeigeneinfügung -302 Umleitungsproblem auf iOS und Desktop

Es wurde ein Fehler behoben, der auftrat, wenn ein Anzeigen-Asset eine relative Umleitungs-URL verwendete

**Version 1.4.9** (1.4.9.427) für iOS 6.0+

* (ZD #3075) Problem mit der Interneterreichbarkeit - iOS

Es wurde eine Benachrichtigung hinzugefügt, die erkennt, wann die Wiedergabe angehalten wurde.

* (ZD #3193) Anfrage für eine API zur Profiländerung in TVSDK

Aktualisiert `PTPlaybackInformation` , um die aktualisierte angegebene Bitrate anzuzeigen. Aktualisiert `BITRATE_CHANGE` -Benachrichtigung, um die Zuverlässigkeit und Genauigkeit der gemeldeten Bitraten des M3U8 zu verbessern.

* (ZD #3324) Problem mit der Meldung von Primetime-Anzeigen, wenn keine Anzeigenmedien in VMAP vorhanden sind

TVSDK unterstützt das Ping leerer Tracking-URLs für Werbeunterbrechungen und überprüft jetzt das Start von Werbeunterbrechungen und das Abschließen von Pings für leere Werbeunterbrechungen.

**Version 1.4.8** (1.4.8.402)

* (ZD #3158) IOS 7 stürzt bei vollständiger Ereigniswiedergabe ab

**Version 1.4.7** (1.4.7.382)

* (ZD #2197) Tracking von Anzeigenfehlern. Es wurde eine Benachrichtigung hinzugefügt, dass das Asset Manifest nicht geladen werden konnte.
* (ZD #2894) Player führt vier Manifestanforderungen auf oberster Ebene während der Wiedergabe durch.
* (ZD #2992) [!DNL Auditude] Melden Sie seltsame Dauern und Kennungen.

**Version 1.4.6**(1.4.6.325)

* (ZD #2197) Tracking von Anzeigenfehlern. Benachrichtigung hinzugefügt, dass Asset-Manifest nicht geladen werden konnte

**Version 1.4.5** (1.4.5.283)

* (ZD #2141) Analytics-Implementierung für [!DNL TreeHouse] App hinzugefügt `AdobeAnalyticsPlugin.a` Bibliothek zum Erstellen des Pakets .
* Aktualisierung der Video Heartbeats-Bibliothek auf 1.4.1.2
* (PTPALY-4226) (im Zusammenhang mit ZD #2423) Das Ausführen von DRM Reset kann zum Löschen der Daten des Anwendungsdokuments führen.

**Version 1.4.4** (1.4.4.242)

* Video Heartbeats Library (VHL) aktualisiert auf Version 1.4.1.

* (ZD #2435) TV SDK-Dokumentation zu Aktualisierungen der Analyseanforderungen

**Version 1.4.2** (1.4.2.210: iOS 6.0+)

* (ZD #1129) `_player.currentItem.audioOptions` Leer zurückgeben
* (ZD #2109) Primetime PSDK 1.4.1.125 funktioniert nicht mit Xcode 5.1.1
* (ZD #2137) Absturz im PSDK in iOS, wenn DRM-Metadaten nicht geladen werden können

**Version 1.4.1**(1.4.1.125)

* (ZD #1107) [!DNL CocoaLumberjack] doppelte Symbole
* (ZD #1644) Ändern des iOS-Benutzeragenten für Targeting und Reporting
* (ZD #1850) Im iOS SDK enthaltene Cocoa Lumberjack-Dateien
* (ZD#1908) Benutzerdefinierte Tags werden von PSDK ignoriert, wenn mehr als 1 vorhanden ist

**Version 1.4.0** (1.4.0.32)

* Zendesk #1024 - Funktion zum Entfernen von Anzeigen aus dem Stream über Manifest

## Gerätezertifizierung und -unterstützung {#device-certification-and-support}

>[!NOTE]
>
>Die folgenden Funktionen sind **not** unterstützt im TVSDK :
>
>* Langsames Bewegen auf allen Plattformen oder Versionen.
>* Live Trick Play.


**Version 1.4.43**

* TVSDK 1.4.43 ist für iOS 11 zertifiziert.

**Version 1.4.29**

* TVSDK 1.4.29 wurde für iOS 10 zertifiziert.

**Version 1.4.28**

* TVSDK 1.4.28 wurde für iOS 10 Beta 7 zertifiziert.
* DRM-Unterstützung zum Erzwingen von HTTPS durch Hinzufügen von  `forceHTTPS`  und `isForcingHTTPS` APIs.
* Aktualisierung der VHL-Bibliotheken auf Version 1.5.8, der Adobe Mobile-Bibliotheken auf Version 4.8.4 und der Bibliothek des Logger-Dienstprogramms auf das Bereitstellungsziel der Version 7.0.

**Version 1.4.19**

Diese Version des TVSDK wurde mit dem FairPlay-Support für iOS und tvOS zertifiziert.

**Version 1.4.17**

* tvOS

   Diese Version des TVSDK enthält Unterstützung für tvOS und wurde für unverschlüsselte HLS-Streams zertifiziert.

   **Hinweis**: Beachten Sie die folgenden Kompilierungsrichtlinien:

   * TVSDK tvOS-Unterstützung ist auf DRM-verschlüsselte Streams ohne Adobe beschränkt. Sie müssen den Verweis auf `drmNativeInterface.framework` in Ihren tvOS-Build-Einstellungen. AES-verschlüsselte Streams werden weiterhin unterstützt.
   * Apple erfordert, dass alle Apple TV-Anwendungen für Bitcode aktiviert sind. Daher müssen Sie dieses Flag in Ihren Projekteinstellungen aktivieren.

## Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

* Aufgrund der Einstellung der iOS UIWebView-Klasse in iOS TVSDK 3.6 ab:
   * VPAID-Anzeigen werden in iPad 13 nicht wie erwartet abgespielt.
   * Companion-Anzeigen werden nicht wie erwartet abgespielt.

* In iOS TVSDK werden alle Anzeigen dem Inhaltsmanifest zugeordnet. Anzeigenverhalten werden durch Suche basierend auf der Dauer des Inhalts und der Anzeigensegmente implementiert. Wenn die Segmentdauer also nicht genau ist, endet die Suche möglicherweise nicht immer im exakten Rahmen am Anfang oder Ende der Werbeunterbrechung. Selbst wenn die Dauer des Frames beträgt, gibt es eine Toleranz, die die Plattform selbst der Suche auferlegt, und es können einige Frames oder Anzeigen oder Inhalte angezeigt werden. Dies ist eine Einschränkung der Plattform und der Funktionsweise von Anzeigen-Insertion mit TVSDK in iOS.
* Die Entscheidung zum Überspringen erfolgt in diesem Fall beim Suchereignis. Da die Anzeigensegmentdauer im Manifest jedoch nicht genau die tatsächliche Dauer der Anzeige darstellt, ist die Suche nicht frame-genau. Daher sehen Sie einige Frames von Anzeigen, wenn die Anzeigenrichtlinien angewendet werden.
* Es kann vorkommen, dass die Lizenzrotation nicht auf iOS 11 abgespielt wird und auf iOS 9.x und iOS 10.x gut wiedergegeben wird.
* Wenn die Wiedergabe über AirPlay aktiv ist, werden VPAID-Anzeigen in VPAID 2.0-Unterstützung übersprungen.
* Die `drmNativeInterface.framework` wird nicht korrekt verknüpft, wenn das minimale Ziel auf iOS7 (oder höher) gesetzt ist.
Problemumgehung: Spezifizieren Sie explizit die `libstdc++.6.dylib` Bibliothek wie folgt: Navigieren Sie zu **[!UICONTROL Target]** > **[!UICONTROL Build Phases]** > **[!UICONTROL Link Binary With Libraries]** und hinzufügen `libstdc++.6.dylib`.
* Eine Post-Roll-Anzeige wird nicht zum Ersetzen der API eingefügt.
* Bei der Suche in einer Werbeunterbrechung (ohne sie zu verlassen) werden doppelte Benachrichtigungen zu Anzeigenstart und Werbeunterbrechung ausgegeben.
* Einstellung `currentTimeUpdateInterval` hat keine Wirkung.
Hinweis: In bestimmten iOS-Versionen lädt das Betriebssystem die Ressourcen nicht in die `PSDKLibrary.framework` automatisch. Es ist wichtig, die `PSDKResources.bundle` auf die Bundle-Ressourcen des Programms: Navigieren Sie zu **Build-Phasen** und kopieren Sie Bundle-Ressourcen.
* Die Referenz-App kann nicht mit Xcode 8 oder niedrigeren Versionen erstellt werden. Ab iOS TVSDK-Version 1.4.41 verwenden Sie zum Kompilieren Xcode 9.
* VPAID-Anzeigen berücksichtigen nicht die `delayAdLoadingTolerance` -Wert.
* 24077 - Bei bestimmten HLS-Inhalten mit Untertiteln stürzt der Player bei ab _Anhalten_ oder _Zurücksetzen_ -Methode.
* Detaillierte Fehlerbenachrichtigungen sind nicht verfügbar, wenn die Option Just in Time Ad Resolving aktiviert ist.
* Fehlerbenachrichtigungen werden gemäß der Anzeigenauflösungszeit und nicht gemäß Anzeigensequenz protokolliert.
* Die HEVC-Unterstützung weist in dieser Version folgende Einschränkungen auf
   * DRM wird nicht unterstützt
   * CC (CEA 608/708)-Unterstützung nicht verfügbar, da sie in CMAF nicht unterstützt wird.
   * 4K-Unterstützung ist noch nicht verfügbar.
   * ID3-Tags unterstützen nicht verfügbar, da sie in CMAF nicht unterstützt werden.
   * Nicht verschraubte Live-HEVC-Streams nicht verifiziert.
   * Die Unterstützung für HEVC-Anzeigen wurde nicht überprüft.
* Wenn JIT aktiviert ist und die Toleranz auf 10 Sekunden eingestellt ist, wird für die erste MIME-Anzeigenunterbrechung kein VAST-Aufruf angezeigt, wenn VMAP > VAST-Weiterleitungsanzeigen vorhanden sind.
* Damit das Zeitlimit für die Anzeigenauflösung ordnungsgemäß funktioniert, erwartet der Player bei jeder Aktualisierung der Wiedergabeliste während der Live-Stream-Wiedergabe eine zugeordnete Wiedergabeliste innerhalb von 20 Sekunden. Wenn innerhalb dieses Intervalls keine zugeordnete Wiedergabeliste empfangen wird, wird ein interner Fehler ausgegeben und der Player wird angehalten.

## Hilfreiche Ressourcen {#helpful-resources}

* [TVSDK 3.4 für iOS-Programmierhandbuch](/help/programming/tvsdk-3x-ios-prog/ios-3x-introduction/ios-3x-overview/ios-3x-overview.md)
* [TVSDK iOS 3.4 API-Referenz](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v34/index.html)
* Die vollständige Hilfedokumentation finden Sie unter [Adobe Primetime - Lernen und Support](https://experienceleague.adobe.com/docs/primetime.html) Seite.
