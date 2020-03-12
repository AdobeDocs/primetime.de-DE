---
title: TVSDK 1.4 für iOS-Versionshinweise
seo-title: TVSDK 1.4 für iOS-Versionshinweise
description: TVSDK 1.4 für iOS-Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme und Geräteprobleme in TVSDK iOS 1.4
seo-description: TVSDK 1.4 für Android - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme und Geräteprobleme in TVSDK iOS 1.4
uuid: c1df12bd-aa21-47e8-ade4-1e497882ce9b
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 452f8699-7857-49ab-9caa-22204b19fe4a
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# TVSDK 1.4 für iOS-Versionshinweise {#tvsdk-for-ios-release-notes}

TVSDK 1.4 für iOS-Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK iOS 1.4.

## Neue Funktionen {#new-features}

**Version 1.4.45**

* Um Xcode10 zu erfüllen, hat TVSDK von &quot;`libstdc++`&quot; zu &quot;`libc++`&quot; verschoben, und infolgedessen ist die Mindestversion iOS 7 unterstützt. Früher war es iOS 6.

**Version 1.4.44**

* Keine neue Funktion oder Verbesserungen in dieser Version.

**Version 1.4.43**

* TV-ähnliche Erfahrung, in der Mitte einer Anzeige mitmachen zu können, ohne die Verfolgung einer partiellen Anzeige auszulösen.\
   Beispiel: Der Benutzer schließt sich in der Mitte (40 Sekunden) einer 90-Sekunden-Werbeunterbrechung an, die aus drei 30-Sekunden-Anzeigen besteht. Dies ist 10 Sekunden nach der zweiten Anzeige in der Pause.

   * Die zweite Anzeige wird während der verbleibenden Dauer (20 Sekunden) und die dritte Anzeige abgespielt.
   * Anzeigentracker für die teilweise wiedergegebene Anzeige (zweite Anzeige) werden nicht ausgelöst. Die Tracker für nur die dritte Anzeige werden ausgelöst.

* Die Eigenschaft enableVodPreroll des booleschen Typs wurde in der PTAdMetadata-Schnittstelle hinzugefügt. Mit der Eigenschaft kann die Pre-Roll-Funktion für einen VoD-Stream aktiviert werden. Wenn enableVodPreroll NO ist, wird PSDK nicht Pre-Roll abgespielt. Dies hat jedoch keine Auswirkungen auf die Zwischenrollen. Der Standardwert von enableVodPreroll ist YES.
* Die API der PTMediaPlayer-Schnittstelle für &quot;closeCaptionDisplayEnabled&quot;wird ab iOS v1.4.43 als nicht mehr unterstützt markiert. Um festzustellen, ob für ein bestimmtes PTMediaPlayerItem Untertitel verfügbar sind, überprüfen Sie die Eigenschaft &quot;subtitlesOptions&quot;von PTMediaPlayerMediaItem.

**Version 1.4.42**

Diese Version enthält keine neuen Funktionen. Eine Liste der behobenen Probleme finden Sie unter Behobene Probleme.

**Version 1.4.41**

API-Änderungen:

* **isSecure**: Eine neue API ist isSecure eingeführt, um den Player vor der Aufzeichnung und Ausgabe eines Fehlers zu schützen. Der Standardwert ist true.
* **allowExternalRecording**: Eine neue API wird eingeführt, um die Spiegelung von Airplay für sichere Inhalte zu ermöglichen. Airplay-Spiegelung wird als Aufzeichnung behandelt. Daher muss der Wert allowExternalRecording auf &#39;True&#39; gesetzt werden, damit Airplay-Spiegelung möglich ist, oder auf &#39;False&#39; eingestellt werden, um die Spiegelung von Airplay für sicheren Inhalt zu stoppen. Der Standardwert ist true.

**Version 1.4.40**

Keine neuen Funktionen.

**Version 1.4.39**

* iOS TVSDK ist mit VHL 2.0.1 und mit VHL 2.0.1 mit Nielsen zertifiziert.
* iOS TVSDK wird aktualisiert, um CRS-Anforderungen vom neuen Akamai-Host zu erstellen `primetime-a.akamaihd.net`.
* Die neue Hostnamenkonfiguration bietet CRS-Asset-Versand sowohl über HTTP als auch über HTTPS (SSL) in größerem Umfang.

**Version 1.4.36**

VHL 2.0 in iOS TVSDK integrieren und zertifizieren: Reduzieren Sie die Barriere in der VideoHeartbeatsLibrary-Implementierung, indem Sie die Komplexität der APIs verringern.

**Version 1.4.34**

* Netzwerkanzeigeninformationen

   TVSDK-APIs bieten jetzt zusätzliche Informationen zu VAST-Antworten von Drittanbietern. Anzeigen-ID, Anzeigensystem und VAST-Anzeigenerweiterungen werden in einer `PTNetworkAdInfo` Klasse bereitgestellt, auf die über eine Eigenschaft eines Anzeigenassets zugegriffen `networkAdInfo` werden kann. Diese Informationen können für die Integration mit anderen Ad-Analytics-Plattformen wie **Moat Analytics** verwendet werden.

**Version 1.4.31**

* **Abrechnungsmetriken** Um Kunden, die nur für ihre Verwendung bezahlen möchten, anstelle eines festen Satzes unabhängig von der tatsächlichen Verwendung aufzunehmen, erfasst Adobe Nutzungsmetriken und ermittelt anhand dieser Metriken, wie viel die Kunden bezahlen müssen.

Jedes Mal, wenn TVSDK ein Stream-Beginn-Ereignis generiert, sendet der Player regelmäßig HTTP-Nachrichten an das Rechnungssystem von Adobe. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann für standardmäßige VOD-, Pro-VOD- (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterschiedlich sein. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, aber Ihr Vertrag mit Adobe legt die tatsächlichen Werte fest.

* **Multi-CDN-Unterstützung für CRS** AdsTVSDK unterstützt jetzt Multi-CDN für CRS-Anzeigen. Durch Angabe von FTP-Details für CRS-Anzeigen können Sie andere CDN-Orte als das standardmäßige, von Adobe gehörende CDN wie Akamai angeben.

**Version 1.4.29**

In der PTSDKConfig-Klasse wurde die forceHTTPS-API hinzugefügt.

Die PTSDKConfig-Klasse stellt Methoden zum Erzwingen von SSL für Anforderungen bereit, die an Adobe Primetime-Anzeigen, DRM- und Video Analytics-Server gesendet werden. Weitere Informationen finden Sie unter `forceHTTPS` und `isForcingHTTPS` -Methoden für diese Klasse. Wenn ein Manifest über HTTPS geladen wird, behält TVSDK die Inhaltsverwendung von HTTPS bei und berücksichtigt diese Verwendung beim Laden von relativen URLs aus diesem Manifest.

**Hinweis**: Anforderungen an Drittanbieter-Domänen wie Anzeigenverfolgungspixel, Inhalts- und Anzeigen-URLs und ähnliche Anforderungen werden nicht geändert. Es liegt in der Verantwortung der Inhaltsanbieter und Anzeigenserver, URLs bereitzustellen, die über HTTPS unterstützt werden.

**Version 1.4.18**

Primetime iOS TVSDK unterstützt jetzt VPAID 2.0-JavaScript-Kreative, um eine umfassende interaktive In-Stream-Anzeigenerfahrung zu ermöglichen.

Weitere Informationen zu VPAID 2.0 finden Sie unter [VPAID-Anzeigenunterstützung](../programming/tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-vpaid-2.0-ads.md).

**Version 1.4.17**

* tvOS

   TVSDK unterstützt native tvOS-Anwendungen.
* Folgende Inhaltstypen können wiedergegeben werden:

   * VOD
   * Live
   * AES-128
   * Alternative Audio- und Untertitel
   * FER

* Die folgenden Arten von Anzeigen können angezeigt werden:

   * Basis
   * VAST2
   * VAST3
   * VMA

* Die folgenden Funktionen werden derzeit nicht unterstützt:

   * Digital Rights Management (DRM)
   * Anzeigenbanner
   * TV Markup Language (TVML)

**Version 1.4.13**

**Hinweis**: Das Nielsen-Modul wurde aus dem TVSDK-Build entfernt, das TVSDK wird demnächst mit einem neuen Nielsen-Integrationsmodul aktualisiert.

* **Ad Fallback, Dissy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103)**

Bei VAST-Anzeigen (kreativen Elementen) mit aktivierter Ausweichregel behandelt das TVSDK eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht stattdessen, Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Weitere Informationen finden Sie unter [Ad-Fallback für VAST- und VMAP-Anzeigen](../programming/tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-ad-fallback.md).

**Version 1.4.9**

* **Blackout-Signalisierung durch Austausch alternativer Inhalte**

Als Teil des 1.4 TVSDK Updates unterstützen wir jetzt auch das Eingehen in und Rückgängigmachen von regionalen Stromausfällen gegen lineare Inhalte. Das TVSDK kann nun zwei Manifestdateien parallel, main und alternative verarbeiten, um die Blackout-Signale auch dann zu überwachen, wenn anstelle der ursprünglichen Programmierung eine alternative Programmierung angezeigt wird.

**Version 1.4.8**

* **Video Heartbeats Library (VHL) aktualisiert auf Version 1.5**

   * Möglichkeit zum Senden von Metadaten mit Video-Beginn und/oder Video/Anzeige/Beginn als Kontextdaten
   * Weniger Netzwerkverkehr - Heartbeats sind im Durchschnitt weniger und kleiner

**Version 1.4.7**

* **Unterstützung der Personalisierung vor Ort**

Unterstützung für lokale Installationen von Adobe Individualization Server, um die Individualisierungsanforderung des Kunden an einen anderen Endpunkt anzupassen.

* **Auflösungsbasierter Ausgabeschutz**

Die DRM-Richtlinien können jetzt die höchste zulässige Auflösung festlegen, je nach Ausgabeschutzfunktionen des Geräts. Beispiel: &quot;Wenn HDCP verfügbar ist, können Sie Inhalte mit einer Auflösung von bis zu 1080p abspielen lassen, und wenn HDCP nicht verfügbar ist, können Sie Inhalte mit einer Auflösung von bis zu 480p abspielen.&quot;

**Version 1.4.4**

* **Video Heartbeats Library (VHL) aktualisieren auf Version 1.4.1.1**

   * Es wurde die Möglichkeit hinzugefügt, verschiedene Anwendungsfälle für Analysen - von anderen SDKs oder Playern - mit Adobe Analytics Video Essentials zu bündeln.
   * Die Anzeigenverfolgung wurde optimiert, indem die Methoden trackAdBreakStart und trackAdBreakComplete entfernt wurden. Die Werbeunterbrechung wird aus den trackAdStart- und trackAdComplete-Methodenaufrufen abgeleitet.
   * Die Eigenschaft playhead ist bei der Verfolgung von Anzeigen nicht mehr erforderlich.
   * Unterstützung für die Marketing Cloud-Besucher-ID hinzugefügt.

* **Nielsen SDK-Integration**

   * TVSDK unterstützt jetzt das Senden von mTVR- und MDPR-ID3-Beacons an das Nielsen-SDK ohne benutzerdefinierte Integration. Laden Sie zunächst das Nielsen iOS App SDK 3.1.2.19 herunter.

**Version 1.4.0**

* **Blackout-Signalisierung durch Austausch alternativer Inhalte**

   * Als Teil des 1.4 TVSDK Updates unterstützt das TVSDK jetzt auch das Eingehen und Zurückkehren von regionalen Blackouts gegen lineare Inhalte. Das TVSDK kann nun zwei Manifestdateien parallel, main und alternative verarbeiten, um die Blackout-Signale auch dann zu überwachen, wenn anstelle der ursprünglichen Programmierung eine alternative Programmierung angezeigt wird.

* **C3-Anzeigen entfernen/ersetzen**

   * Jetzt ist keine zusätzliche Vorarbeit erforderlich, um dynamisch neue Anzeigen in Video-on-Demand-Assets (VOD) einzufügen, die aus dem C3-Fenster herauskommen. Das TVSDK bietet jetzt eine API zum Entfernen benutzerdefinierter Inhaltsbereiche und zum dynamischen Einfügen neuer Anzeigen. Diese leistungsstarke neue Funktion ist auch in Fällen nützlich, in denen während der Übertragung Live-/Lineare Inhalte erscheinen und sofort zur Verwendung als On-Demand-Inhalte heruntergezogen werden, ohne dass genügend Zeit zum &quot;Bereinigen&quot;des Assets erforderlich ist.

## Gerätezertifizierung und Unterstützung in 1.4 {#device-certification-and-support-in}

>[!NOTE]
>
>Die folgenden Funktionen werden im TVSDK **nicht** unterstützt:
>
>* Langsames Bewegen auf jeder Plattform oder Version.
>* Live-Trick-Spiel.


**Version 1.4.43**

* TVSDK 1.4.43 ist für iOS 11 zertifiziert.

**Version 1.4.29**

* TVSDK 1.4.29 wurde für iOS 10 zertifiziert.

**Version 1.4.28**

* TVSDK 1.4.28 wurde für iOS 10 Beta 7 zertifiziert.
* DRM-Unterstützung, um HTTPS durch Hinzufügen von forceHTTPS- und isForcingHTTPS-APIs zu erzwingen.
* Die VHL-Bibliotheken wurden auf Version 1.5.8, die Adobe Mobile-Bibliotheken auf Version 4.8.4 und die Protokollprogrammbibliothek auf die Zielgruppe zur Bereitstellung der Version 7.0 aktualisiert.

**Version 1.4.19**

Diese Version des TVSDK wurde mit dem FairPlay-Support für iOS und tvOS zertifiziert.

**Version 1.4.17**

* tvOS

   Diese Version des TVSDK enthält Unterstützung für tvOS und wurde für unverschlüsselte HLS-Streams zertifiziert.

   **Hinweis**: Beachten Sie die folgenden Kompilierungsrichtlinien:

   * TVSDK tvOs-Unterstützung ist auf DRM-verschlüsselte Streams ohne Adobe beschränkt. Sie müssen den Verweis auf &quot;drmNativeInterface.framework&quot;in den tvOS-Buildeinstellungen entfernen. AES-verschlüsselte Streams werden weiterhin unterstützt.
   * Apple erfordert, dass alle Apple TV-Anwendungen Bitcode aktivieren. Daher müssen Sie dieses Flag in den Projekteinstellungen aktivieren.

## Behobene Probleme in 1.4 {#resolved-issues-in}

<!-- 

Comment Type: draft

<note type="note"> 
 <p>All TVSDK customers who use CRS are strongly encouraged to upgrade to TVSDK 1.4.39 or latest on iOS and Android. This upgrade is a drop-in replacement to the existing app implementation. After the upgrade, check for the CRS creative URL requests in a proxy tool (for example, Charles) to verify that the version in the path reflects version 3.1. For example:</p> 
 <p><span class="code">https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8</span></p> 
</note>

 -->

<!-- 

Comment Type: draft

<note type="note"> 
 <p>TVSDK versions earlier than version 1.4.28 sometimes exhibit a long delay in the startup time when ad-enabled content is played on devices that are running on iOS 10. To resolve this issue, upgrade to version 1.4.28 or later. Version 1.4.28 was released on August 31, 2016, and iOS 10 was released on September 13, 2016.</p> 
</note>

 -->

**Version 1.4.45{#ios-tvsdk}**

* Ticket #36294 - iOS TVSDK funktioniert nicht mit Xcode 10

   * Korrektur der Kompilierungsprobleme mit TVSDK unter XCode 10. Aufgrund der XCode 10-Anforderungen erfordern Apps, die auf TVSDK für iOS 1.4.45 basieren, eine Mindestbereitstellungszeit als iOS 7.0

* Ticket #36321 - Diskrepanz im suchbaren Bereich zwischen der PTMediaPlayer- und der AVPlayer-Instanz im Status &quot;Abspielen&quot;.
* Ticket #36493 - `libstdc++` Unterstützung unter iOS 12

   * Korrektur der Kompilierungsprobleme mit TVSDK unter iOS 12. Für Apps, die auf TVSDK für iOS 1.4.45 basieren, ist eine Mindestbereitstellungs-Zielgruppe als iOS 7.0 erforderlich

**Version 1.4.44**

* Ticket #34683 - Fortschrittszeit bei der Anzeigenwiedergabe läuft negativ

   * Zusätzliche Überprüfungen, die durchgeführt werden, um den Fall zu behandeln, wenn eine Abweichung zwischen der vom Anzeigen-Server gemeldeten Dauer und dem tatsächlichen Anzeigeninhalt besteht.

* Ticket #34801 - currentTime und localTime wurden bei der Suche nach einer neuen Position während des Status &quot;Angehalten&quot;nicht aktualisiert

   * Die aktuelle Zeit des Spielers kann jetzt auf null gesetzt werden, falls der Player angehalten ist; früher wurde die aktuelle Zeit nur im Wiedergabestatus auf null gesetzt.

* Ticket Nr. 35037 - Wiedergabe wird bei der Rückkehr von der signalbasierten Anzeigeneinfügung mit einer schlechten URL angehalten.

   * Verbesserte Korrektur für das geschlossene Problem 34385 in Version 1.4.42. Es wurde Code für die Prüfung und Ausnahmebehandlung mit isCanceled hinzugefügt, um die Warteschlange der Vorgänge robuster zu gestalten.

**Version 1.4.43**

* (ZD#32990) - iOS: Wiedergabe von Inhalten anstelle von Anzeigen auf einigen Cue-Points. Die API &#39;selectedMediaOptionInMediaSelectionGroup&#39;, die Teil der AVPlayerItem-Schnittstelle war, wurde jetzt unter AVMediaSelection in iOS 11 verschoben. Das Problem wurde mit dieser neuen API behoben.
* (ZD#33683) TVSDK wurde == Suffix aus den Metadaten-Zeichenfolgen entfernt. Das Problem wurde in der Parsing-Logik behoben.
* (ZD#33905) - iOS TVSDK ruft die Manifestdateien mit zwei Benutzeragenten auf. Das Problem mit dem Benutzeragenten wurde im ersten m3u8-Aufruf behoben (Neuinstallation). M3u8&#39;s haben die gleichen Benutzeragenten für alle Anrufe jetzt.
* (ZD#34293) - In LINEAR-Streams eingefügte Rollen werden unter iOS11 nicht korrekt wiedergegeben. Das Problem wurde bei Preroll-Anzeigen behoben.
* (ZD#34684) - Wenn die Richtlinie zum Überspringen von Anzeigen angewendet wird, werden die Pre-Roll-Anzeigenrahmen für einige Sekunden angezeigt. Eine neue API, enableVodPreroll, wurde eingeführt, um die Wiedergabe von Vorspänen in vod-Wiedergabe zu deaktivieren. Der Standardwert für diese API ist &quot;Ja&quot;. Die API stellt sicher, dass das Zuordnen von Werbeinhalten im Hauptinhalt übersprungen wird.
* (ZD#34765) - Nach dem Aufruf von stop() werden immer noch wenige Segmente zu Transport-Streams heruntergeladen. Die Stopp()-API wurde verbessert, um den Download der zusätzlichen Segmente zu vermeiden.
* (ZD#34865) - Pre-Roll-Anzeigen für Livestream werden unter iOS abgeschnitten. Im Zusammenhang mit iOS11 wird dieses Problem durch Hinzufügen einer zusätzlichen Prüfung zur Bestätigung, ob der Stream Pre-Roll oder Hauptinhalt ist, behoben.
* (ZD#35093) - Es wurde ein Failover-Szenario behoben, bei dem, wenn die primäre Variante des Streams beim Start fehlschlug (gibt 404 zurück), die Wiedergabe nicht in den Sicherungsstream wechselt.

**Version 1.4.42 (1.4.42.118)**

* (ZD#34385) - Wiedergabe wird bei der Rückkehr von der signalbasierten Anzeigeneinfügung mit einer schlechten URL angehalten.

   Erhöhen Sie die maximale Anzahl gleichzeitiger Werte für CustomAVAssetLoaderOperations, damit die Manifestlesungen weiterhin ausgeführt werden können.
* (ZD#34373) - Endbenutzer können nicht an HDMI-verbundene Geräte streamen, wenn die Stream-Aufzeichnung deaktiviert ist.
* (ZD#32678) - TVSDK erfasst nicht die richtigen Anzeigen-IDs unter iOS.

   Die Anzeigen-ID des finalen Werbekreativen wird jetzt im Fall von VAST/VMAP-Umleitungen in VHL-Pings aufgenommen.
* (ZD#33904) - TVSDK ist nicht für AVFoundation-Benachrichtigungen AVAudioSessionMediaServicesWereLostNotification und AVAudioSessionMediaServicesWereResetNotification registriert.

   PTMediaServicesWereLostNotification und PTMediaServicesWereResetNotification können jetzt in der Player-App registriert werden, um die Benachrichtigungen abzurufen, wenn Media-Dienste zurückgesetzt oder verloren gehen.

* (ZD#33815) - Kunden können ihre CRS-Regeln für Priorisierung und Normalisierung nicht aktualisieren, ohne dass eine App-Aktualisierung erforderlich ist.

   Die APIs getCRSRulesJsonURL und setCRSRulesJsonURL wurden zum iOS TVSDK hinzugefügt.

**Version 1.4.41 (1.4.41.76)**

* (ZD #34464) - Erstellen einer Referenz-App mit TVSDK Version 1.4.41

   Ab dieser Version ist Xcode 9 für die Kompilierung von TVSDK für iOS erforderlich.
* (ZD #29456) - Airplay-Beginn im Status &quot;Angehalten&quot;

   Korrektur des Pausenproblems, das beim Anhalten des Videos beim Einstieg in Airplay auftrat.
* (ZD #30371) - Zeitänderungen des AdBreak-Beginns, wenn mehr als 2 Anzeigen in den linearen Stream eingefügt werden

   Korrektur des Fehlers, der die Wiedergabe von Inhalten auf Apple TV verhindert hat, wenn versucht wurde, diese vollständig wiederzugeben
* (ZD #32146)- Beim Blockieren von iOS 11 dev beta wird kein PTMediaPlayerStatusError für HLS Live-Inhalte empfangen

   Für HLS Live- und VOD-Inhalte beim Blockieren mit Charles wird kein PTMediaPlayerStatusError empfangen (Drop-Verbindung und 403)
* (ZD #29242) - Airplay Video Play-back schlägt fehl, wenn Anzeigen aktiviert sind

   Wenn Anzeigen aktiviert sind und AirPlay aktiviert ist, um mit der Wiedergabe eines Videos zu beginnen, wird die Videowiedergabe nie zu Beginn und es wird kein Fehler angezeigt
* (ZD#33341) - DRMInterface.h löst Buildwarnungen in Xcode 9 aus

   Es wurden zwei Blockprototypen in DRMInterface.h behoben, bei denen das Wort &quot;void&quot;in den Listen der Parameter fehlte
* (ZD#31979) - Wird nicht kompiliert/ausgeführt, wenn iOS 10 oder höher für iPhone 7/iPhone 7+ ist

   Das Kompilieren von IB-Dokumenten für frühere Versionen als iOS 7 wird nicht mehr unterstützt
* (ZD#32920) - weißer leerer Bildschirm innerhalb einer Werbeunterbrechung und ohne Abschluss der Werbeunterbrechung

   Wenn ein Werbeunterbrechung Anzeigeninstanzen anzeigt und nach Abschluss einer Anzeigeninstanz ein weißer leerer Bildschirm angezeigt wird
* (ZD#32509) - Deaktivieren der Bildschirmaufzeichnung &quot;iOS 11&quot;Deaktivieren der Bildschirmaufzeichnung unter iOS 11

* (ZD#33179) - Zeitweiliger Ereignis-Fehler unter iOS 11

   Korrektur des Fehlers des Ereignisses unter iOS 11

**Version 1.4.40** (1.4.40.72)

* (ZD #32465) - Player kann keine zusammengeführten Playlisten verarbeiten.

   Aufruf von &quot;completeLoadingWithError&quot;(mit: Fehler) für AV-Stiftung, um alternative Streams/Auslöserfailover auszuprobieren.

* (ZD #31951) - TVSDK-Fehler bei Lizenzrotationen.

   Problem mit der Lizenzrotation behoben.
* (ZD #31951) - Weißer leerer Bildschirm innerhalb einer Werbeunterbrechung und ohne Abschluss der Werbeunterbrechung.

   Behebung eines Problems, bei dem Facebook VPAID-Anzeigen häufig mehrere CDATA-Blöcke in einem einzigen \&amp;lt;AdParameters\&amp;gt zurückgaben; VAST-Knoten.
* (ZD #33336) - [iOS] TVSDK - Anzeigen-Pods werden nicht ausgefüllt, obwohl genügend Anzeigen von FreeWheel zurückgegeben wurden.

   Erstellt eine über-/untergeordnete Beziehung zwischen Sequenzanzeige und Fallback-Anzeige und Sortierung basierend auf der übergeordneten Sequenz und dem Index.

**Version 1.4.39** (1.4.39.43)

* (ZD #32178) - iOS TVSDK-Version ist nicht korrekt.

   Die Ausgabe der TVSDK-Version in den Protokolldateien war 1.0.211. Es wurde behoben, um die richtige Version auszugeben.

* (ZD #32199) - Laden von Lazy Ad - Video wird für den Inhalt nicht angezeigt.

   Die lokale Zeitleiste von Adbreak, die zuvor nicht initialisiert wurde, wird jetzt vor der Verwendung aktualisiert.

* (ZD #27528) - Video, Audio oder beides frieren 1-45 Sekunden nach dem Abspielen eines Assets ein, wenn das sekundäre Audio unter iOS 1.2 auf &quot;Nicht-Standard&quot;eingestellt ist.

   Bereiten Sie Audiospuren im Bereitschaftszustand vor und informieren Sie sie.

* (ZD #30411) - Es kann vorkommen, dass unerwartete Ergebnisse wie keine Audio- oder falsche Audiowiedergabe vorliegen, wenn Sie eine sekundäre SAP-Sprache wählen.

   Bereiten Sie Audiospuren im Bereitschaftszustand vor und informieren Sie sie.

* (ZD #32199) - Laden von Lazy Ad - Video wird für den Inhalt nicht angezeigt.

   Die lokale Zeitleiste von Adbreak, die zuvor nicht initialisiert wurde, wird jetzt vor der Verwendung aktualisiert.

* (ZD #27528) - Video, Audio oder beides frieren 1-45 Sekunden nach dem Abspielen eines Assets ein, wenn das sekundäre Audio unter iOS 1.2 auf &quot;Nicht-Standard&quot;eingestellt ist.

   Bereiten Sie Audiospuren im Bereitschaftszustand vor und informieren Sie sie.

* (ZD #30411) - Es kann vorkommen, dass unerwartete Ergebnisse wie keine Audio- oder falsche Audiowiedergabe vorliegen, wenn Sie eine sekundäre SAP-Sprache wählen.

   Bereiten Sie Audiospuren im Bereitschaftszustand vor und informieren Sie sie.

**Version 1.4.38** (1.4.38.860)

* (ZD #29281) - iOS: Hinzufügen von AdSystem- und Creative-ID zu CRS-Anforderungen

Verwendung von kreativen IDs und AdSystem in CRS-Anforderungen basierend auf CRS-Normalisierungsregeln

* (ZD #29176) - Absturz bei PTAdPolicyDeligate satAdBreakAsWatched:position

Absturz aufgrund leerer AdBreak wird jetzt behandelt.

* (ZD #30125) - Programmatische Anzeigen funktionieren nicht auf der iOS-Plattform

Unterstützung für programmatische Anzeigen in iOS hinzugefügt.

* (ZD #30782) - #EXT-X-PROGRAMM-DATE-TIME Notification

Zeitgesteuertes Metadaten-Ereignis wird nicht für # EXT-X-PROGRAMM-DATE-TIME-Tag mit LIVE DRM-Streams ausgelöst.

**Version 1.4.37 (1.4.37.842)**

* (ZD #28950) - Problem mit der VOD-Wiedergabe

Wiedergabeproblem, wenn # EXT-X-PLAYLIST-TYPE-Tag im Stream auf Ereignis anstatt auf VOD eingestellt ist

* (ZD #29281) - iOS: Hinzufügen von AdSystem- und Creative-ID zu CRS-Anforderungen

Verwendung von Creative ID und AdSystem in CRS-Anforderungen basierend auf CRS-Normalisierungsregeln.

* (ZD #29462) - TremorHub-Anzeige in A&amp;E VOD, die einen Absturz in iOS-Apps verursacht

**Version 1.4.36 (1.4.36.835)**

* (ZD #29418) - Ereignisse mit der Dauer 0 (#EXT-X-CUE-OUT:0.000) führen dazu, dass iOS TVSDK die Wiedergabe stoppt oder abstürzt.

Das Problem wurde behoben, und die Wiedergabe-Beginn waren korrekt.

* (ZD #29462) - Anzeige in VOD, die einen Absturz auf iOS TVSDK verursacht.

Das Problem wurde behoben. iOS TVSDK löst eine Ausnahme aus (AUDNetworkAdInfo::initWithAdId) und verarbeitet sie nicht. Die Ausnahme ist auf eine leere Anzeigen-ID zurückzuführen.

* (ZD #29281)- Hinzufügen AdSystem- und Creative-ID für CRS-Anforderungen.

Schließen Sie AdSystem und CreativeId als neue Parameter in die Anforderungen 1401 und 1403 ein (alle anderen Parameter bleiben gleich).

**Version 1.4.35** (1.4.35.830)

* (ZD #27830) - Muss den Unterschied zwischen Untertiteln und Untertiteln in iOS programmgesteuert bestimmen.

TVSDK stellt nun die beiden Typen zur Verfügung, die zum Filtern des erforderlichen Beschriftungstyps verwendet werden können.

* (ZD #29160) - EXT-X-CUE-OUT-Anzeigen-Hinweise werden unter TVSDK iOS nicht korrekt geteilt.

Mit EXT-X-CUE-OUT midroll und jetzt abspielen.

* (ZD #29100) - Die App stürzt ab, wenn der Benutzer bis zum Ende eines Films scrollt.

Mehrere Abstürze im Zusammenhang mit der Synchronisierung wurden behoben.

* (ZD #28785), (ZD #27712) und (ZD #25076) - Die iOS-App stürzt während der großen Live-Ereignis ab.

Mehrere Abstürze im Zusammenhang mit der Synchronisierung wurden behoben.

**Version 1.4.34** (1.4.34.815 für iOS 6.0+)

* (ZD# 28481) - FER-Ausfall aufgrund des fehlerhaften Schlüssels, der am Ende einer Werbeunterbrechung für diese FER-Streams angehängt wird

Bei einem FER-Stream wird der Schlüssel vor der Werbeunterbrechung nach dem Ende der Werbeunterbrechung eingefügt. Dieses Problem wurde behoben, indem der *zuletzt angezeigte Schlüssel* am Ende der Werbeunterbrechung angehängt wurde.

**Version 1.4.33** (1.4.33.803 für iOS 6.0+)

* (ZD# 21701) Aktivieren von CRS für Unterkonten

Aktiviert, indem die ursprüngliche kreative URL für die CRS-Anforderung 1401 anstelle der normalisierten URL gesendet wird, wie es für das CRS-Back-End erforderlich ist.

* (ZD# 26218) - Problem beim Laden von PSDKResources.bundle

Dieses Problem wurde behoben, indem das Laden der Ressourcen aktualisiert wurde, um alle verfügbaren Pakete anzuzeigen.

* (ZD# 27460) Midroll first Ad call - POST to cdn.auditude<span></span>.com return 403.

Das neue CDN-Konto kann eine POST-CDN-Anforderung nicht bearbeiten. Dieses Problem wurde behoben, indem der Code aktualisiert wurde, damit die `cdn.auditude.com` Anzeigenanforderung GET anstelle von POST lautet.

**Version 1.4.32** (1.4.32.792 für iOS 6.0+)

* (ZD# 27132) Unterstützung von Dezimalwerten für VMAP-Werbeunterbrechungen.

Wenn Inhalte nicht entlang der definierten Werbeunterbrechungen segmentiert wurden, verursachten Ganzzahlen unerwartete Anzeigenplatzierungen. Das Problem wurde behoben, indem die Dezimalwerte nicht in Ganzzahlen konvertiert wurden.

* (ZD# 27189) AES-Inhalte mit dem EXT-X-DISCONTINUITY-SEQUENCE-Tag werden nicht korrekt wiedergegeben.

Das Problem wurde behoben, indem das Tag am Anfang der Wiedergabeliste platziert wurde.

**Version 1.4.31** (1.4.31.785 für iOS 6.0+)

* (ZD# 24528) Implementieren von TVSDK-Nutzungsmetriken für die Rechnungsstellung

Weitere Informationen finden Sie unter [Rechnungsmetriken](../programming/tvsdk-1.4-for-ios/c-psdk-ios-1.4-billing/c-psdk-ios-1.4-billing.md).

* (ZD# 24642) Bild-in-Bild-Unterstützung für TVSDK

Das Bild-im-Bild-Feature, das in einigen Fällen nicht richtig funktionierte, wurde behoben.

* (ZD# 25246) Falsche Werbeunterbrechungssignale

Dieses Problem wurde behoben, indem Diskontinuitäts-Tags über Variantenmanifeste hinweg ausgerichtet wurden.

* (ZD# 26218) Der Vorgang zum Erstellen von Anwendungen wird kompliziert, wenn versucht wird, PSDKLilibrary.framework in das Anwendungsframework des Clients einzubeziehen

Dieses Problem wurde behoben, indem das PSDKLilibrary.framework wie gewünscht verpackt wurde.

* (ZD# 26364) Multi-CDN-Unterstützung für CRS-Anzeigen
<!-- 
Comment Type: draft
For more information, see [Multiple CDN support for CRS Ad Delivery](http://help.adobe.com/en_US/primetime/psdk/ios/1.4/index.html#PSDKs-concept-Multiple_CDN_support_for_CRS_ad_delivery).
-->
* (ZD# 27028) Verzögerung bei der Wiedergabe einiger Streams in iOS 10.

Dieses Problem wurde behoben, indem eine Problemumgehung für Streams ohne M3U8-Erweiterung bereitgestellt wurde.

**Version 1.4.30** (1.4.30.754 für iOS 6.0+)

Die folgenden Probleme wurden in dieser Version für TVSDK behoben:

* (ZD# 24180) Hinzufügen einer benutzerdefinierten Kopfzeile zur weißen Liste

Der White-Liste TVSDK wurde eine neue benutzerdefinierte Kopfzeile hinzugefügt.

* (ZD# 25016) Failover-Stream wird zufällig ausgewählt, wenn ABR-Steuerungsparameter eingestellt werden

Dieses Problem wurde behoben, indem die ABR-Streams in der Reihenfolge beibehalten wurden, in der die ABR-Einstellungen mit der Einstellung initialBitrate für einen Stream bereitgestellt wurden, der Failover-URLs enthält. Dadurch wird vermieden, dass die Failover-Streams statt primär abgespielt werden.

* (ZD# 25076) Absturz bei PTAuditudeAdResolver loadComplete

Das Problem, bei dem während des schnellen Beginns/Stopps mehrerer PTMediaPlayer-Instanzen mit Anzeigen ein Absturz auftrat, wurde behoben.

* (ZD# 25960) Es gibt keine weiteren abonnierten Tags, die Metadaten-Änderungsbenachrichtigungen auslösen

Das Problem, bei dem ein abonniertes Tag nicht benachrichtigt wird, wenn es vor dem ersten Segment im Manifest angezeigt wird, wurde behoben.

* (ZD# 26084) PSDK zum Auswerfen eines 106000.101000.-11833-Decoder wurde beim Übergang vom letzten Werbeunterbrechungsereignis zum Unterhaltungsinhalt nicht fehlerfrei gefunden

Wenn die letzte Werbeunterbrechungszeit vom VMAP vor Abschluss der Gesamtdauer liegt, wird unter bestimmten Umständen der Beginn erst nach Ende der letzten Werbeunterbrechung eingefügt. Dieses Problem wurde behoben.

* Die Video Heartbeat Library (VHL) wurde auf Version 1.5.9 aktualisiert, um die folgenden Probleme zu beheben:

   * (ZD #22351) VHL - Analytics: Dauer des Live-Video-Assets

Dieses Problem wurde behoben, indem die assetDuration-API hinzugefügt wurde, um die Asset-Dauer für Live/Lineare Streams zu aktualisieren und eine Logik zur Überprüfung des Live-Streams bereitzustellen. `PTVideoAnalyticsTrackingMetadata`

* (ZD# 22675) VHL - Analytics: Aktualisieren der Dauer von Live-Video-Assets

Diese Ausgabe ist mit der ZD #22351 identisch.

* (ZD #25908) VHL - Analytics: Adobe Heartbeat Ereignis Crash

Dieses Problem wurde behoben, indem die Implementierung aktualisiert wurde, um die neueste Version von VHL für iOS Version 1.5.9 zur Verbesserung der Stabilität und Leistung zu verwenden.

* (ZD #25956) VHL - Analytics: Absturz beim wiederholten Abspielen von Videos

Diese Ausgabe ist mit der ZD #25908 identisch.

**Version 1.4.29** (1.4.29.743)

* (ZD# 23901) Anzeigen von Drittanbietern werden nicht wiedergegeben

Dieses Problem wurde behoben, indem zur URL-Struktur von CRS v3 gewechselt wurde, um die Zonen-ID in die neu gepackte URL aufzunehmen.

* (ZD #25183) Probleme mit der DRM-Wiedergabe unter tvOS und iOS

Dieses Problem wurde behoben, indem Unterstützung für mehrere Schlüssel-Tags bereitgestellt wurde, die für die Unterstützung mehrerer DRM erforderlich sind.

* (ZD# 25334) TVSDK kann keine gemeinsamen cDVR-Inhalte wiedergeben

Dieses Problem wurde behoben, indem TVSDK daran gehindert wurde, leere Zeichenfolgen in absolute URLs zu konvertieren.

* (ZD# 25347) Festlegen eines benutzerdefinierten HTTP-Headers auf AVURLAsset

Unterstützung für benutzerdefinierte Header für Segmentanforderungen über die PTNetworkConfiguration-Klasse wurde hinzugefügt.

**Version 1.4.28** (1.4.28.722)

* (ZD #24549) Mehrere Aufrufe zur Anzeigenverfolgung

Dieses Problem wurde behoben, indem der Timeline-Manager aktualisiert wurde, um nach Benachrichtigungen über ein bestimmtes Objekt zu suchen, wenn mehrere Player erstellt wurden.

* (ZD #24758) PTManifestLogger unterstützt iOS 8 nicht

Dieses Problem wurde behoben, indem die Protokollprogrammbibliothek auf die Zielgruppe zur Bereitstellung der Version 7.0 aktualisiert wurde.

* (ZD #24775) Verzögerter Stream aufgrund von Anzeigen

Dieses Problem wurde behoben, indem die Dauer-Drift auf Ereignis-Playlists korrekt berechnet wurde.

* (ZD #24799) Einige Episoden werden auf iOS-APP nicht wiedergegeben

Dieses Problem wurde durch die Verwendung eines lokalen Webservers für Untertitel behoben, wenn die WebVTT-Dateien geografisch eingeschränkt sind.

**Version 1.4.27** (1.4.27.711) für iOS 6.0+

* (ZD #24089) - Optimierungen für die Anzeigenauflösung bei langen DVR-Streams

Dieses Problem wurde behoben, indem mehrere Optimierungen hinzugefügt wurden, um die für die Verarbeitung des DVR-Fensters in Live-/linearen Streams erforderliche Zeit zu verkürzen.

* (ZD #21554) - TVSDK-Fehlerbeacons, die nicht für application-type = video/mp4 ausgelöst werden

Dieses Problem wurde behoben, indem der Player die korrekten Fehlerverfolgungs-URLs für ungültige Asset-Formate ping.

* (ZD #24424) - Absturz des Typs EXC_BAD_ACCESS KERN_INVALID_ADDRESS stammt von PSDKLib für iOS auf neueren Hardwaregeräten.

Der Absturz, der aufgrund einer nicht zugeordneten Media Player-Instanz aufgetreten ist, wenn die Wiedergabe schnell zwischen verschiedenen Streams umgeschaltet wird, wurde behoben.

* (ZD #24575) - Absturz in TVSDK auf 32-Bit-Geräten, wenn enableDebugLog=true

Das Problem im Protokollformat, das den Absturz auf 32-Bit-Geräten verursachte, wenn die Protokollierung aktiviert ist, wurde behoben.

**Version 1.4.26** (1.4.26.702) für iOS 6.0+

* (ZD# 20213) - TVSDK FW muss dynamisch/modularisiert für XCode7 sein

   * Korrigiert durch Aktualisierung der Bibliotheken mit Modulunterstützung

**Version 1.4.25** (1.4.25.684) für iOS 6.0+

* (ZD #19629) - Live-Video wird angehalten, wenn Airplay in ATV 4 aufgenommen wird

Dieses Problem wurde behoben, indem eine Wartezeit hinzugefügt wurde, nachdem alte Elemente entfernt wurden, aber bevor neue Elemente zum AVQueuePlayer hinzugefügt wurden. Ohne Wartezeit werden Benachrichtigungen an das falsche Element gesendet.

* (ZD #19856) - Es werden keine Untertitel angezeigt, wenn sie standardmäßig aktiviert sind

Die Probleme in der Webvtt-Playlist, die dazu geführt haben, dass die Untertitel nicht korrekt angezeigt wurden, wurden behoben.

* (ZD #21590) - Videoleistung und Videoverfolgung in den neuesten Herkünfte

Das Problem mit der fehlenden Videolänge in VideoAnalytics wurde behoben.

* (ZD #20202) - Durch Festlegen des Stils für benutzerdefinierte Untertitel stürzt die iOS-App ab

Dieses Problem wurde behoben, indem beim Festlegen von Untertitelstilen zusätzliche Null-Objekt-Prüfungen hinzugefügt wurden.

* (ZD #20709) - Videolänge, die bei der Videoverfolgung als 0 gemeldet wird

Dieses Problem ist mit dem Problem (ZD #21590) identisch.

* (ZD #22280) - Analytics-Videolänge auf 0 eingestellt

Dieses Problem ist mit dem Problem (ZD #21590) identisch.

* (ZD #22592) - Probleme mit Airplay in Primetime

Dieses Problem ist mit dem Problem (ZD #19629) identisch.

* (ZD#22922) - Manuelles Umschalten der Bitrate für iOS

Dieses Problem wurde behoben, indem eine Option zur Angabe der maximalen Bitrate bereitgestellt wurde.

* (ZD #23084) - Apple Compliance for IPv6-only Networks

Die Symbole, die von Apple für die IPv6-Kompatibilität nicht empfohlen wurden, wurden entfernt.

**Version 1.4.24** (1.4.24.661) für iOS 6.0+

* ZD #2548) - Primetime-Unterstützung für interaktive Werbung auf Mobilgeräten - VPAID 2.0

Dieses Problem wurde behoben, indem die Logik aktualisiert wurde, um die Player-Ansicht wieder einzublenden, wenn eine VPAID-Anzeige nicht abgespielt werden konnte.

* (ZD #20101) - Bei der Implementierung benutzerdefinierter Kapitel wird das Ereignis des Kapitels Beginn während der Anzeigenwiedergabe ausgelöst

Dieses Problem wurde behoben, indem VideoAnalyticsTracker aktualisiert wurde, um beim Übergang zwischen Kapitel- und Nicht-Kapitelgrenzen den Beginn/Abschluss von Kapiteln korrekt zu erkennen.

* (ZD #20784) - Analytics: Auslösen von Inhaltsbeendigungen für Live-Video-Transitionen

Dieses Problem wurde behoben, indem eine Logik hinzugefügt wurde, die den Abschluss von Inhalten während einer Videoverfolgungssitzung manuell auslöst.

Die folgenden Bibliotheken wurden aktualisiert:

* AdobeMobile-Bibliothek auf 4.10.0
* VHL-Bibliothek zu 1.5.6
* VHL-Nielsen-Bibliothek zu 1.6.7
* (ZD #21855) - Untertitel werden nach dem Mid-Roll nicht abgespielt

Bei diesem Problem wurden Duplikat-Diskontinuitäts-Tags dazu geführt, dass Untertitel nach dem Mid-Roll nicht angezeigt wurden. Dieses Problem wurde behoben, indem die Tags für die Diskontinuität entfernt wurden, die sich nebeneinander befinden.

* (ZD #21994) - String out-of-bounds in PTHLSUtils

Die wahrscheinlichste Ursache des Absturzes ist, wenn ein EXT-X-KEY eine URL hat, die von Anführungszeichen umgeben ist.

* ZD #22074) - AUDVAST-Absturz unter iOS einmal pro Minute

In Version 1.4.23 wurde der Absturz behoben, der durch das Vorhandensein unsicherer Zeichen in einer VAST-Umleitungs-URL verursacht wurde. TVSDK übersprungen diese Anzeigen jedoch weiterhin.

Dieses Problem wurde behoben, indem die unsicheren Zeichen behandelt und die Anzeigen abgespielt wurden.

* (ZD #22694) - PTMediaPlayer.  Ansicht wird vom Player ausgeblendet

Dieses Problem wurde behoben, indem die Logik aktualisiert wurde, um die Player-Ansicht wieder einzublenden, wenn eine VPAID-Anzeige nicht abgespielt werden konnte.

**Version 1.4.23** (1.4.23.641) für iOS 6.0+

* (ZD #18016) - Keine Antwort des Primetime SDK mit einer schlechten Netzwerkbedingung

Dieses Problem wurde behoben, indem die Fehlerbenachrichtigung verbessert wurde, wenn ein schwerwiegender Fehler von AVFoundation auftritt, und die App den Neustart nach dem Fehler verarbeiten konnte.

* (ZD #20580) - Absturz in PTSplicerManager

Dieses Problem wurde behoben, indem ein zusätzlicher Schutz vor gleichzeitigen Problemen bereitgestellt wurde, die den Absturz verursachen.

* (ZD #21782) - iOS-Fehlercode 10100

Das Problem, bei dem das TVSDK einen Fehler vom Typ 101000 zurückgab, während die Wiedergabe auf Adobe Access DRM-Streams gestartet wurde, wurde behoben.

* (ZD #21889) - Wiedergabe von Online-Anzeigen und Offlineinhalten schlägt fehl

Das Problem, bei dem die Wiedergabe fehlschlug, nachdem eine AES-verschlüsselte Offlineinhalte behoben wurde.

* (ZD #22074) - AUDVAST-Absturz unter iOS einmal pro Minute

Dieses Problem wurde behoben, indem die Behandlung von VAST-Anzeigen-Tags von Drittanbietern, die ungültige Zeichen in der URL enthalten, verbessert wurde.

* (ZD #22257) - TVSDK kann DRM-Stream nicht wiedergeben

Das Problem, bei dem das TVSDK, das einen Fehler 101000 zurückgegeben hat, während die Wiedergabe auf Adobe Access DRM-Streams gestartet wurde, behoben wurde.

**Version 1.4.22** (1.4.22.627) für iOS 6.0+

* (ZD #18709) - Absturz im TVSDK für iOS

Das Problem mit einem Absturz in einigen geschützten Streams von Adobe Access DRM wurde behoben.

* (ZD #18850) - Aktualisieren der Logik der kreativen Auswahl auf Grundlage von CRS-Regeln

Dieses Problem wurde behoben, indem eine JSON-Konfigurationsdatei hinzugefügt wurde, um die Priorität für die kreative Auswahl anzugeben.

* (ZD #19770) - Geschützter AES-Video-Feed wird nicht mehr wiedergegeben

Das Problem, dass 302 umgeleitete Streams nicht spielten, wurde behoben.

* (ZD #19629) - Live-Video wird angehalten, wenn Airplay in ATV 4 aufgenommen wird

Dieses Problem wurde behoben, indem eine Behelfslösung für die Live-Video-Pause hinzugefügt wurde, wenn die Wiedergabe von Airplay für Apple TV 4-Geräte aktiviert ist. Das Problem scheint eine AppleTV 4-Ausgabe zu sein.

* (ZD #21119) - Das TVSDK wird nach der Wiedergabe der Anzeige angehalten

Unterstützung für AES-verschlüsselte Streams mit einer Sequenz IV beim Einfügen von Anzeigen hinzugefügt.

* (ZD #21125) - Frühzeitige Rückkehr von Live-/linearen Werbeunterbrechungen

Es wurde Unterstützung für die Rückkehr von einer Werbeunterbrechung frühzeitig vor der Wiedergabe der Werbeunterbrechung bis zum Abschluss hinzugefügt. Die frühe Rückkehr wird durch ein benutzerdefiniertes Manifest-Tag angezeigt.

* (ZD #21224) - Airplay-Unterstützung für getinkte Streams von Akamai

APIs wurden zur PTNetworkConfiguration-Klasse hinzugefügt, um Cookies als URL-Parameter für Segmente für bestimmte Akamai-tokenisierte Streams anzuhängen.

* (ZD #21287) - Fremdprotokoll

Es wurde ein Problem behoben, bei dem einige Protokollanweisungen standardmäßig in der xcode-Konsole angezeigt wurden, selbst wenn die Protokollierung deaktiviert ist.

* (ZD #21446) - Ereignis von Werbeunterbrechungen, die manchmal nicht vom TVSDK ausgelöst werden

Bei EREIGNIS-Streams werden Werbeunterbrechungen im vorherigen Release-Build nicht korrekt ausgelöst. Dieser Build behebt dieses Problem.

**1.4.21** (1.4.21.605) für iOS 6.0+

* (ZD #20749) - Bei einem Fallback werden nicht leere VAST-Antworten übersprungen. Extra-Anzeigenverfolgungs-URLs ausgelöst

Ein Problem mit Duplikat-Pings für Fallback-Anzeigen wurde behoben.

**1.4.20** (1.4.20.590) für iOS 6.0+

* (ZD #18639) - Das TVSDK verwendet übermäßige CPU/Ressourcen für ein langwieriges Aufzeichnungselement

Die übermäßige CPU-/Ressourcenauslastung wurde auf den beiden Ebenen behoben. Zuerst, indem die Funktion zum Aktualisieren der Zeit auf einer globalen Warteschlange anstatt auf dem Haupt-Thread ausgeführt wird, und indem die CPU-Auslastung für die Analyse des Manifests mit dem zuvor verarbeiteten und zwischengespeicherten m3u8 optimiert wird.

* (ZD #19349) - Pre-Roll-Anzeigen werden beim Einschränken der Netzwerkverbindung übersprungen.

Dieses Problem wurde behoben, indem ein Timeout-Ereignis (requestTimeout) für die Anwendung und die AdMetadata bereitgestellt wurde.  adRequestTimeout-API zum Überschreiben des standardmäßigen 10-Sekunden-Timeouts.

* (ZD #19446) - Fehlende Benachrichtigung bei Live-Streams

Dieses Problem wurde behoben, indem die Anwendung die EXT-X-PROGRAMM-DATE-TIME für Live-Streams abonnieren konnte.

* (ZD #19459) - Absturz beim Vorbereiten von Alternativaudio mit PTMediaPlayerItem prepareAudioOptionsWithAVMediaSelectionOptions
* (ZD #19460) - Absturz - [PTMediaPlayerItem prepareSubtitlesOptionsWithAVMediaSelectionOptions:nonForcedOptions:]

Dieses Problem ist mit Zendesk #19459 identisch.

* (ZD #19574) - Das TVSDK gibt keine M3U8-Antwortdaten für DRM- oder Nicht-DRM-Inhalte zurück

Beim ersten Laden der Manifestdatei in PTMediaPlayerItem.prepareToPlay meldet das TVSDK bei fehlgeschlagenem Laden nicht den Hauptteil der Fehlerantwort auf die Anwendung.

Dieses Problem wurde behoben, indem TVSDK die Fehlerantwort als Fehler an die Anwendung melden konnte.

* (ZD #19615) - Fallback-Logik funktioniert nicht

In der aktuellen Implementierung wurden Ausweichanzeigen übersprungen und nicht neu verpackt, es sei denn, diese Anzeigen haben das Format m3u8. Dieses Problem wurde behoben, indem auch die Unterstützung für das Umpacken von Fallback-Anzeigen hinzugefügt wurde.

* (ZD #19770) - Das TVSDK kann keine geschützten AES-Inhalte mit 302-Umleitung wiedergeben

Das Umleitungsproblem wurde behoben, da die Umleitungs-URL von cleanConnectionData gelöscht wurde, bevor sie zur Analyse des Manifests verwendet werden konnte.

* (ZD #19856) - Untertitel werden für einige Bitraten nicht angezeigt, wenn sie standardmäßig aktiviert sind

Dieses Problem wurde behoben, indem der Fehler von iOS für die Segmente der Streams behoben wurde, in denen die Untertitel nicht angezeigt werden.

* (ZD #19868) - Das TVSDK stürzt ab, wenn ein ungültiger Kreativelemente mit dem Traffic versehen wird

Der Absturz im TVSDK, bei dem eine Instanz des riesigen Parsers falsch verzögert wurde, wurde behoben.

* (ZD #20180) - VPAID-Anzeigen werden gelegentlich übersprungen

Der JavaScript-Mime-Typ wurde nicht immer einbezogen oder als gültiger Mime-Typ betrachtet. Dieses Problem wurde behoben, indem JavaScript als gültiger MIME-Typ einbezogen wurde.

* (ZD #20749) - Bei einem Fallback werden nicht leere VAST-Antworten übersprungen. Extra-Anzeigenverfolgungs-URLs ausgelöst

Das Problem, dass einige der kreativen Elemente nicht neu verpackt werden, wurde behoben.

**Version 1.4.19** (1.4.19.563) für iOS 6.0+

* ZD #18639) - Das TVSDK verwendet übermäßige CPU/Ressourcen für ein langwieriges Aufzeichnungselement

Dieses Problem wurde behoben, indem die DRM m3u8-Wiedergabelistenumformulierung in Cache-Teile der Wiedergabeliste optimiert wurde, die zuvor umgeschrieben wurden. Dies ist besonders relevant, wenn Sie Live-m3u8-Streams wiedergeben, für die m3u8 nach jedem Segmentdownload heruntergeladen wird.

* (ZD#18956) - player.drmManager ist null, wenn der Haltepunkt im iOS Demo Player festgelegt ist

Dieses Problem wurde behoben, indem die Implementierung der PTMediaPlayer.drmManager-API aktualisiert wurde, um DRMManager vom DRM-Framework abzurufen.

**Version 1.4.18** (1.4.18.557) für iOS 6.0+

* (ZD #18844) Tracking-Abspielkopf für Live-Inhalte im iOS-Player.

Dieses Problem wurde behoben, indem die Anwendungen ihren eigenen Playhead-Wert festlegen konnten.

* Zendesk #18518 - Wenn der Videoname nicht angegeben ist, lautet der Name des TVSDK standardmäßig *PSDK-basierter Player.*

Dieses Problem wurde behoben, indem der Standardwert für den Namen des Players entfernt wurde.

**Version 1.4.17** (1.4.17.545) für iOS 6.0+

* Zendesk #2228 - Enhance the TVSDK to return JSON response of the fetching of a manifest

Anstatt einen Fehler zu senden, wenn der Inhalt nicht M3U8 ist, gibt das DRM-Framework eine Null-DRMMetadata zurück. Das Problem wurde behoben, indem Metadaten hinzugefügt wurden, um Inhalte verfügbar zu machen, wenn die Benachrichtigung M3U8_PARSER_ERROR erfolgt.

* Zendesk #2231 - Fehler beim Abrufen des in MediaPlayerNotification nicht verfügbaren Manifests zurückgegeben

Gleiche Auflösung wie Zendesk #2228

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` -Makro nicht gefüllt

Das Problem, bei dem das Auditude-SDK keinen Ping sendet, wenn die Tracking-URL zu Beginn Leerzeichen enthält, wurde behoben.

* Zendesk #17294 - Absturz SecKeyRawSign

Ein möglicher Absturz, bei dem der Code des Kunden die Schlüsselkette verwendet, wurde behoben.

* Zendesk #18008 - Cookies für iOS8+ unterstützen, um Tokenisierte Streams zu unterstützen

Akamai-tokenisierte Streams erfordern, dass Cookies bei Segmentanforderungen gesendet werden, was unter iOS 7 und früher nicht möglich war. Ab iOS 8 hat Apple eine API hinzugefügt, mit der Cookies für Segmentanforderungen übergeben werden können. Diese Unterstützung ist jetzt im TVSDK verfügbar. Es wurde auch Unterstützung für das Senden eines Benutzeragenten hinzugefügt, falls verfügbar.

* Zendesk #18166 - TVSDK 1.4.15 gibt beim Kompilieren mit DWARF mit dSYM-Dateioptionen Hunderte von Warnungen aus

Alle Warnungen wurden behoben.

**Hinweis**: tvOS-kompatible Bibliotheken wurden für TVSDK hinzugefügt.

**Version 1.4.16** (1.4.16.1454)

* Zendesk #3875 - Tabulator-S stürzt während der Wiedergabe ab

Rückgängigmachen der Abhängigkeit von OKHTTP auf Auditude für CRS, da TVSDK jetzt direkt die HTTPLILLconnection statt curl verwendet. Das Problem wurde durch Löschen von Ausnahmen behoben, bevor ein weiterer JNI-Aufruf durchgeführt wurde.

* Zendesk #4487 - Tracking Linear Kanal of Content

Das Problem wurde behoben, indem der Video Heartbeat-Tracker während einer linearen Stream-Wiedergabesitzung erneut initialisiert wurde.

* Zendesk #17919 - Android - Inhaltssuche verursacht Heartbeat-Fehler

Das Problem bestand darin, den Heartbeat in einem Fehlerstatus zu beheben, wenn eine Suche in einem Kapitel stattgefunden hat

* Zendesk #18053 - Anwendung mit TVSDK stürzt bei Marshmallow ab

Das TVSDK stürzte unter Android M OS ab, wenn die TVSDK-Bibliothek Neoncode verwendet, der YUV -> RGB-Farbkonvertierung vornimmt. Dieses Problem wurde behoben, indem die Funktionen aktualisiert wurden, die dieses Problem verursachen, indem Code verwendet wird, der nicht Neon ist.

* Zendesk #18072 - Android M - Anwendungsabsturz

Dieser Absturz tritt beim Aufrufen der MediaCodecList- und MediaCodecInfo-APIs auf, wenn geprüft wird, ob das Profil und die Ebene unterstützt werden. Adobe sucht nach der Unterstützung von Google, um weitere Informationen zu erhalten. Dieses Problem wurde behoben, indem eine temporäre Bearbeitung bereitgestellt wurde, indem alle Codec-Informationen frühzeitig geladen wurden, um zu vermeiden, dass diese APIs nur dann aufgerufen werden, wenn Codec-Informationen benötigt werden.

* Zendesk #18074 - Arabische Untertitel, die nicht auf Nexus mit Android 6.0 funktionieren

Dieses Problem wurde behoben, indem Unterstützung für die Android CTS-Schriftzuordnung bereitgestellt wurde.

**Version 1.4.15** (1.4.15.512) für iOS 6.0+

**Hinweis**: Das Nielsen-Modul wurde aus dem TVSDK-Build entfernt, aber das TVSDK wird demnächst mit einem neuen Nielsen-Integrationsmodul aktualisiert.

* (ZD #2228) - Fehler beim Abrufen des Manifests in MediaPlayerNotification nicht verfügbar

Metadaten wurden hinzugefügt, um Inhalte anzuzeigen, wenn die Benachrichtigung M3U8_PARSER_ERROR eintritt.

* (ZD #4437) - Abstürze innerhalb des Adobe Primetime-SDK

Ein gemeldeter Absturz beim Vorbereiten von Untertiteln/alternativen Audiodaten wurde behoben.

* (ZD #4487) - Tracking Linear Kanal of Content

Zulässige erneute Initialisierung des Video Heartbeat-Trackers während einer linearen Stream-Wiedergabesitzung.

**Version 1.4.14** (1.4.14.498) für iOS 6.0+

* (ZD #17260) - Absturz bei playlistManagerForURL

Es wurde ein zeitweiliger Absturz aufgrund von Parallelitätsproblemen behoben.

**Version 1.4.13** (iOS 6.0+)

* (ZD #3304) - VAST 3.0- `[ERRORCODE]` Makro nicht gefüllt

   * Der Fehlercode 400 wird angezeigt, wenn Inline-Anzeige ein falsches kreatives Element enthält.
   * `[ERRORCODE]` Makro wird URL-kodiert.

* (ZD #3865) Heartbeat-Integration mit IMA-Anzeigen

Es wurde ein Fehler behoben, durch den die Videolänge falsch gemeldet wurde.

* TVSDK-Demo-Player zur Unterstützung von iOS 9 aktualisiert

Um iOS 9 ordnungsgemäß zu unterstützen, müssen Sie die Ausnahmen von Application Transportation Security konfigurieren. Für die Zwecke der Demo ist das ATS vollständig deaktiviert.

**Version 1.4.12** (1.4.12.464) für iOS 6.0+

* (ZD #4521) CRS Testing Client Side und SSAI

Falsche Version MD5 in 3P-URL korrigiert.

**Version 1.4.12** (1.4.12.463) für iOS 6.0+

* (ZD #2751) CSAI und CRS| Verbesserung: Verarbeiten Sie dynamische Elemente in bestimmten Mediendatei-URLs.

Der Dienst für kreative Umverpackungen wurde aktualisiert, um Anzeigen mit dynamischen kreativen URLs korrekt zu bearbeiten.

* (ZD #3654) Speicherverlust in PSDK-Version nach dem 1.3.4.166

Speicherleck in drmFramework mit regelmäßiger Wiedergabe auf iOS 8.2-Geräten behoben

* (ZD #3988) Die Preroll-Funktion wird übersprungen, wenn nach der ersten Wiedergabe wieder danach gesucht wird

Es wurde ein Fehler behoben, durch den Anzeigenrichtlinien ordnungsgemäß deaktiviert werden konnten.

* (ZD #4017) Anfordern der iOS-API, um die Anzeigenwiedergabe bei der Rückwärtssuche zu erzwingen

Behoben mit Korrektur für ZD #4279

* (ZD #4279) HLS TVSDK-Anzeigeneinfügung -302 Umleitungsproblem unter iOS und Desktop

Fehler behoben, der auftrat, wenn ein Anzeigenasset eine relative Umleitungs-URL verwendete

**Version 1.4.9** (1.4.9.427) für iOS 6.0+

* (ZD #3075) Problem mit der Interneterreichbarkeit - iOS

Es wurde eine Benachrichtigung hinzugefügt, die erkennt, wann die Wiedergabe angehalten wurde.

* (ZD #3193) Anforderung einer API zum Ändern von Profilen in TVSDK

PTPlaybackInformation wurde aktualisiert, um die aktualisierte displayedBitrate verfügbar zu machen. Die BITRATE_CHANGE-Benachrichtigung wurde dahingehend aktualisiert, dass sie zeitzuverlässiger und genauer auf die vom M3U8 gemeldeten Bitraten reagiert.

* (ZD #3324) Problem mit dem Berichte von Primetime-Anzeigen, wenn keine Anzeigenmedien in VMAP vorhanden sind

Unterstützung für das Ping von URLs zur Verfolgung von Werbeunterbrechungen, überprüft TVSDK jetzt den Beginn von Werbeunterbrechungen und vollständige Pings für leere Werbeunterbrechungen

**Version 1.4.8** (1.4.8.402)

* (ZD #3158) Bei Abstürzen von IOS 7 in &quot;Replay im vollständigen Ereignis&quot;

**Version 1.4.7** (1.4.7.382)

* (ZD #2197) Verfolgung von Anzeigenfehlern. Es wurde eine Benachrichtigung hinzugefügt, dass das Manifest für Assets nicht geladen werden konnte.
* (ZD #2894) Player erstellt 4 Manifestanforderungen der obersten Ebene während der Wiedergabe.
* (ZD #2992) Eigene Dauer und Bezeichner des Auditude Berichte.

**Version 1.4.6**(1.4.6.325)

* (ZD #2197) Verfolgung von Anzeigenfehlern. Benachrichtigung hinzugefügt, dass das Manifest für Assets nicht geladen wurde

**Version 1.4.5** (1.4.5.283)

* (ZD #2141) Bei der Analytics-Implementierung der TreeHouse-App wurde AdobeAnalyticsPlugin.a eine Bibliothek zum Erstellen des Pakets hinzugefügt.
* Video Heartbeats Library Update auf 1.4.1.2
* [PTPALY-4226] [in Zusammenhang mit ZD #2423) Das Ausführen des DRM-Resets kann zum Löschen der Daten des Application Dokument führen.

**Version 1.4.4** (1.4.4.242)

* Video Heartbeats Library (VHL) wird auf Version 1.4.1 aktualisiert.

* (ZD #2435) Dokumentation zum TV-SDK zu Aktualisierungen des Analysebedarfs

**Version 1.4.2** (1.4.2.210: iOS 6.0+)

* (ZD #1129) _player.currentItem.audioOptions, die leer zurückgeben
* (ZD #2109) Primetime PSDK 1.4.1.125 funktioniert nicht mit Xcode 5.1.1
* (ZD #2137) Absturz im PSDK unter iOS, wenn DRM-Metadaten nicht geladen werden können

**Version 1.4.1** (1.4.1.125)

* (ZD #1107) CocoaLumberjack-Duplikat-Symbole
* (ZD #1644) Ändern Sie den iOS-Benutzeragent für Targeting und Berichte
* (ZD #1850) In iOS SDK enthaltene Cocoa-Lumberjack-Dateien
* (ZD#1908) Benutzerspezifische Tags werden von PSDK ignoriert, wenn mehr als 1 vorhanden ist

**Version 1.4.0** (1.4.0.32)

* Zendesk #1024 - Funktion zum Entfernen von Anzeigen aus dem Stream über Manifest

## Bekannte Probleme in 1.4 {#known-issues-in}

* In iOS TVSDK werden alle Anzeigen in das Inhaltsmanifest eingefügt. Anzeigenverhalten werden durch Suchen implementiert, die auf der Dauer des Inhalts und der Anzeigensegmente basieren. Wenn die Segmentdauer also nicht genau ist, endet die Suche möglicherweise nicht immer im exakten Rahmen am Anfang oder Ende der Werbeunterbrechung. Auch wenn die Dauer bis zum Rahmen reicht, gibt es eine Toleranz, die die Plattform selbst der Suche auferlegt, und es können einige Frames oder Anzeigen oder Inhalte angezeigt werden. Dies ist eine Einschränkung der Plattform und der Funktionsweise von Anzeigeneinfügungen mit TVSDK unter iOS.
* Die Entscheidung zum Überspringen erfolgt in diesem Fall beim Ereignis Suchen. Da die Anzeigensegmentdauer im Manifest jedoch nicht genau die tatsächliche Dauer der Anzeige widerspiegelt, ist die Suche nicht Bildgenauigkeit. Daher sehen Sie einige Frames der Anzeige, wenn die Anzeigenrichtlinien angewendet werden.
* RECORDING_ERROR: Beim Aufzeichnen des Bildschirms ist ein Fehler aufgetreten.
* Es kann vorkommen, dass das Video zur Lizenzrotation unter iOS 11 nicht abgespielt wird und unter iOS 9.x und iOS 10.x korrekt wiedergegeben wird.
* Bei der VPAID 2.0-Unterstützung werden VPAID-Anzeigen übersprungen, wenn die Wiedergabe über AirPlay aktiv ist.
* Die Verknüpfung von &quot;drmNativeInterface.framework&quot;ist nicht korrekt, wenn die Zielgruppe auf &quot;iOS7 (oder höher)&quot;festgelegt ist.\
   Problemumgehung: Geben Sie explizit die `libstdc++6`Variable an.  Dylib-Bibliothek wie folgt: Gehen Sie zu Zielgruppe->Build-Phasen->Link Binary with Libraries und fügen Sie `libstdc++.6.dylib`hinzu.

* Post-Roll-Anzeige wird nicht zum Ersetzen der API eingefügt.
* Bei der Suche nach einer Werbeunterbrechung (ohne sie zu verlassen) werden dem Duplikat-Beginn und dem Werbeunterbrechungsbenachrichtigungen angezeigt
* Das Festlegen von currentTimeUpdateInterval hat keine Auswirkungen.\
   Hinweis: In bestimmten iOS-Versionen lädt das Betriebssystem die Ressourcen nicht automatisch in PSDKLilibrary.framework. Es ist wichtig, PSDKResources.bundle manuell in die Bundle-Ressourcen der Anwendung zu kopieren: Gehen Sie zu &quot;Build Phases&quot;und kopieren Sie Bundle-Ressourcen.
* Die Referenz-App kann nicht mit Xcode 8 oder niedrigeren Versionen erstellt werden. iOS TVSDK Version 1.4.41, verwenden Sie Xcode 9 zum Kompilieren.

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite &quot; [Adobe Primetime - Training und Support](https://helpx.adobe.com/support/primetime.html) &quot;.