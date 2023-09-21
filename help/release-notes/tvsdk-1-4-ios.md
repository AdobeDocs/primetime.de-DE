---
title: TVSDK 1.4 für iOS - Versionshinweise
description: TVSDK 1.4 für iOS - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK iOS 1.4.
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '6549'
ht-degree: 0%

---

# TVSDK 1.4 für iOS - Versionshinweise {#tvsdk-for-ios-release-notes}

TVSDK 1.4 für iOS - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK iOS 1.4.

## Neue Funktionen {#new-features}

**Version 1.4.45**

* Zur Einhaltung von Xcode10 hat TVSDK von &quot;`libstdc++`&quot; zu &quot;`libc++`&quot;, und daher ist die Mindestversion, die unterstützt wird, iOS 7. Zuvor war es iOS 6.

**Version 1.4.44**

* Keine neue Funktion oder Verbesserungen in dieser Version.

**Version 1.4.43**

* TV-ähnliche Erlebnisse, wenn man mitten in einer Anzeige Mitglied werden kann, ohne das Tracking einer partiellen Anzeige auszulösen.\
  Beispiel: Der Benutzer schließt sich in der Mitte (40 Sekunden) einer 90-Sekunden-Werbeunterbrechung an, die aus drei 30-Sekunden-Anzeigen besteht. Dies ist 10 Sekunden nach der zweiten Anzeige in der Pause.

   * Die zweite Anzeige wird für die verbleibende Dauer (20 Sek.) gefolgt von der dritten Anzeige wiedergegeben.
   * Anzeigentracker für die abgespielte partielle Anzeige (zweite Anzeige) werden nicht ausgelöst. Die Tracker nur für die dritte Anzeige werden ausgelöst.

* Die Eigenschaft enableVodPreroll des booleschen Typs wurde in der PTAdMetadata-Benutzeroberfläche hinzugefügt. Mit der -Eigenschaft kann die Pre-Roll-Funktion für einen VoD-Stream aktiviert werden. Wenn enableVodPreroll auf &quot;NO&quot;gesetzt ist, wird PSDK keine Pre-roll-Wiedergabe durchführen. Dies hat jedoch keine Auswirkungen auf die Zwischenrollen. Der Standardwert von enableVodPreroll ist JA.
* Die API &quot;closedCaptionDisplayEnabled&quot;der PTMediaPlayer-Oberfläche wird ab iOS v1.4.43 als veraltet markiert. Um festzustellen, ob für ein bestimmtes PTMediaPlayerItem geschlossene Untertitel verfügbar sind, überprüfen Sie die Eigenschaft subtitlesOptions von PTMediaPlayerMediaItem.

**Version 1.4.42**

In dieser Version werden keine neuen Funktionen hinzugefügt. Eine Liste der behobenen Probleme finden Sie unter Gelöste Probleme.

**Version 1.4.41**

API-Änderungen:

* **isSecure**: Eine neue API wird eingeführt, isSecure, um den Player vor der Aufzeichnung und Ausgabe eines Fehlers zu schützen. Der Standardwert ist &quot;true&quot;.
* **allowExternalRecording**: Eine neue API wurde eingeführt, um die Spiegelung von Flugspielen für sichere Inhalte zu ermöglichen. Airplay-Spiegelung wird als Aufzeichnung behandelt. Daher muss der Wert allowExternalRecording auf &quot;True&quot;gesetzt werden, um das Spiegeln von Flugwiedergaben zu ermöglichen, oder auf &quot;False&quot;gesetzt werden, um das Spiegeln von Flugwiedergaben zu stoppen, damit sichere Inhalte gewährleistet sind. Der Standardwert ist &quot;true&quot;.

**Version 1.4.40**

Keine neuen Funktionen.

**Version 1.4.39**

* iOS TVSDK ist mit VHL 2.0.1 und VHL 2.0.1 mit Nielsen zertifiziert.
* iOS TVSDK wurde aktualisiert, um CRS-Anforderungen vom neuen Akamai-Host zu stellen `primetime-a.akamaihd.net`.
* Die neue Hostnamenkonfiguration ermöglicht eine skalierbarere Bereitstellung von CRS-Assets über HTTP und HTTPS (SSL).

**Version 1.4.36**

VHL 2.0 in iOS TVSDK integrieren und zertifizieren : Reduzieren Sie die Barriere in der VideoHeartbeatsLibrary-Implementierung, indem Sie die Komplexität der APIs verringern.

**Version 1.4.34**

* Netzwerkanzeigen-Informationen

  TVSDK-APIs bieten jetzt zusätzliche Informationen zu VAST-Antworten von Drittanbietern. Anzeigen-ID, Anzeigensystem und VAST-Anzeigenerweiterungen werden im Abschnitt `PTNetworkAdInfo` -Klasse, die über  `networkAdInfo`  -Eigenschaft für ein Anzeigen-Asset. Diese Informationen können für die Integration mit anderen Ad Analytics-Plattformen wie **Moat Analytics**.

**Version 1.4.31**

* **Abrechnungsmetriken** Um Kunden aufzunehmen, die nur für das bezahlen möchten, was sie verwenden, anstatt für einen festen Satz, unabhängig von der tatsächlichen Verwendung, erfasst Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel Kunden abrechnen müssen.

Jedes Mal, wenn TVSDK ein Stream-Startereignis generiert, beginnt der Player regelmäßig mit dem Senden von HTTP-Nachrichten an das Adobe-Abrechnungssystem. Der Zeitraum, der als abrechnungsfähige Dauer bezeichnet wird, kann sich für standardmäßige VOD, Pro VOD (Mid-Roll-Anzeigen aktiviert) und Live-Inhalte unterscheiden. Die Standarddauer für jeden Inhaltstyp beträgt 30 Minuten, Ihr Vertrag mit Adobe bestimmt jedoch die tatsächlichen Werte.

* **Multi-CDN-Unterstützung für CRS-Anzeigen** TVSDK unterstützt jetzt Multi-CDN für CRS-Anzeigen. Durch Bereitstellung von FTP-Details für CRS-Anzeigen können Sie andere CDN-Speicherorte als das standardmäßige Adobe-eigene CDN wie Akamai angeben.

**Version 1.4.29**

In der Klasse PTSDKConfig wurde die forceHTTPS-API hinzugefügt.

Die PTSDKConfig-Klasse stellt Methoden zum Durchsetzen von SSL für Anfragen bereit, die an Adobe Primetime-Anzeigenentscheidungen-, DRM- und Video Analytics-Server gesendet werden. Weitere Informationen finden Sie unter `forceHTTPS` und `isForcingHTTPS` -Methoden für diese Klasse. Wenn ein Manifest über HTTPS geladen wird, behält TVSDK die Inhaltsverwendung von HTTPS bei und berücksichtigt diese Verwendung beim Laden relativer URLs aus diesem Manifest.

**Hinweis**: Anforderungen an Drittanbieter-Domänen wie Anzeigenverfolgungspixel, Inhalts- und Anzeigen-URLs und ähnliche Anforderungen werden nicht geändert. Inhaltsanbieter und Anzeigen-Server sind dafür verantwortlich, URLs bereitzustellen, die über HTTPS unterstützt werden.

**Version 1.4.18**

Das Primetime iOS TVSDK unterstützt jetzt JavaScript-Kreativelemente mit VPAID 2.0, um eine umfassende interaktive Anzeige im Stream zu ermöglichen.

Weitere Informationen zu VPAID 2.0 finden Sie unter [VPAID-Anzeigenunterstützung](../programming/tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-vpaid-2.0-ads.md).

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

**Hinweis**: Das Nielsen-Modul wurde aus dem TVSDK-Build entfernt. TVSDK wird demnächst mit einem neuen Nielsen-Integrationsmodul aktualisiert.

* **Ad Fallback, Daisy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103)**

Bei VAST-Anzeigen (Kreativen) mit aktivierter Ausweichregel behandelt das TVSDK eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht, stattdessen Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Weitere Informationen finden Sie unter [Anzeigen-Fallback für VAST- und VMAP-Anzeigen](../programming/tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-ad-fallback.md).

**Version 1.4.9**

* **Blackout-Signalisierung mit Ersatz für alternativen Inhalt**

Als Teil des 1.4 TVSDK-Updates unterstützen wir jetzt auch das Eingehen in und Zurückkehren von regionalen Blackouts zu linearen Inhalten. Das TVSDK kann jetzt zwei Manifestdateien parallel, Hauptdatei und alternative verarbeiten, um Blackout-Signale zu überwachen, selbst wenn anstelle der ursprünglichen Programmierung alternative Programmierung angezeigt wird.

**Version 1.4.8**

* **Video Heartbeats Library (VHL) aktualisiert auf Version 1.5**

   * Möglichkeit zum Senden von Metadaten mit Videostart und/oder Video/Anzeige/Kapitelstart als Kontextdaten
   * Weniger Netzwerk-Traffic - Heartbeats sind im Durchschnitt weniger und kleiner

**Version 1.4.7**

* **On-Premise-Individualisierungsunterstützung**

Unterstützung für On-Premise-Installationen des Adobe Individualization Servers, um die Individualisierungsanforderung des Clients so anzupassen, dass sie an einen anderen Endpunkt gesendet wird.

* **Auflösungsbasierter Ausgabeschutz**

DRM-Richtlinien können jetzt die höchstzulässige Auflösung festlegen, je nach den Funktionen des Geräts zum Ausgabeschutz. Beispiel: &quot;Wenn HDCP verfügbar ist, können Inhalte mit einer Auflösung von bis zu 1080p abgespielt werden, und wenn HDCP nicht verfügbar ist, können Inhalte mit einer Auflösung von bis zu 480p abgespielt werden.&quot;

**Version 1.4.4**

* **Aktualisierung der Video Heartbeats Library (VHL) auf Version 1.4.1.1**

   * Es wurde die Möglichkeit hinzugefügt, verschiedene Analytics-Anwendungsfälle von anderen SDKs oder Playern mit den Adobe Analytics-Video-Grundlagen zu bündeln.
   * Das Anzeigen-Tracking wurde optimiert, indem die Methoden trackAdBreakStart und trackAdBreakComplete entfernt wurden. Die Werbeunterbrechung wird aus den trackAdStart - und trackAdComplete -Methodenaufrufen abgeleitet.
   * Die Eigenschaft &quot;playhead&quot;ist beim Tracking von Anzeigen nicht mehr erforderlich.
   * Unterstützung für die Marketing Cloud-Besucher-ID hinzugefügt.

* **Nielsen-SDK-Integration**

   * Das TVSDK unterstützt jetzt das Senden von mTVR- und MDPR ID3-Beacons an das Nielsen-SDK ohne benutzerdefinierte Integration. Laden Sie zunächst das Nielsen iOS App SDK 3.1.2.19 herunter.

**Version 1.4.0**

* **Blackout-Signalisierung mit Ersatz für alternativen Inhalt**

   * Als Teil des TVSDK-Updates für 1.4 unterstützt das TVSDK jetzt auch das Wechseln in regionale Blackouts und das Zurückkehren aus linearen Inhalten. Das TVSDK kann jetzt zwei Manifestdateien parallel, Hauptdatei und alternative verarbeiten, um Blackout-Signale zu überwachen, selbst wenn anstelle der ursprünglichen Programmierung alternative Programmierung angezeigt wird.

* **C3-Anzeigen entfernen/ersetzen**

   * Jetzt ist keine zusätzliche Vorbereitung erforderlich, um neue Anzeigen dynamisch in Video-On-Demand-Assets (VOD) einzufügen, die aus dem C3-Fenster herauskommen. Das TVSDK bietet jetzt eine API zum Entfernen benutzerdefinierter Inhaltsbereiche und zum dynamischen Einfügen neuer Anzeigen. Diese leistungsstarke neue Funktion ist auch in Fällen nützlich, in denen Live-/lineare Inhalte während der Übertragung bereitgestellt werden und sofort zur Verwendung als On-Demand-Inhalt abgerufen werden, ohne dass genügend Zeit bleibt, das Asset zu &quot;bereinigen&quot;.

## Gerätezertifizierung und -unterstützung in 1.4 {#device-certification-and-support-in}

>[!NOTE]
>
>Die folgenden Funktionen sind **not** unterstützt im TVSDK:
>
>* Langsames Bewegen auf allen Plattformen oder Versionen.
>* Live Trick Play.

**Version 1.4.43**

* TVSDK 1.4.43 ist für iOS 11 zertifiziert.

**Version 1.4.29**

* TVSDK 1.4.29 wurde für iOS 10 zertifiziert.

**Version 1.4.28**

* TVSDK 1.4.28 wurde für iOS 10 Beta 7 zertifiziert.
* DRM-Unterstützung zum Erzwingen von HTTPS durch Hinzufügen von forceHTTPS- und isForcingHTTPS-APIs.
* Aktualisierung von VHL-Bibliotheken auf Version 1.5.8, Adobe von Mobile-Bibliotheken auf Version 4.8.4 und der Bibliothek des Logger-Dienstprogramms auf das Bereitstellungsziel der Version 7.0.

**Version 1.4.19**

Diese Version des TVSDK wurde mit dem FairPlay-Support für iOS und tvOS zertifiziert.

**Version 1.4.17**

* tvOS

  Diese Version des TVSDK enthält Unterstützung für tvOS und wurde für unverschlüsselte HLS-Streams zertifiziert.

  **Hinweis**: Beachten Sie die folgenden Kompilierungsrichtlinien:

   * Die TVSDK tvOs-Unterstützung ist auf nicht-Adobe DRM-verschlüsselte Streams beschränkt. Sie müssen den Verweis auf drmNativeInterface.framework in Ihren tvOS-Build-Einstellungen entfernen. AES-verschlüsselte Streams werden weiterhin unterstützt.
   * Apple erfordert, dass alle Apple TV-Anwendungen für Bitcode aktiviert sind. Daher müssen Sie dieses Flag in Ihren Projekteinstellungen aktivieren.

## Behobene Probleme in Version 1.4 {#resolved-issues-in}

<!-- 

Comment Type: draft

 <p>All TVSDK customers who use CRS are strongly encouraged to upgrade to TVSDK 1.4.39 or latest on iOS and Android. This upgrade is a drop-in replacement to the existing app implementation. After the upgrade, check for the CRS creative URL requests in a proxy tool (for example, Charles) to verify that the version in the path reflects version 3.1. For example:</p> 
 <p><span class="code">https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8</span></p> 
-->

<!-- 

Comment Type: draft

 <p>TVSDK versions earlier than version 1.4.28 sometimes exhibit a long delay in the startup time when ad-enabled content is played on devices that are running on iOS 10. To resolve this issue, upgrade to version 1.4.28 or later. Version 1.4.28 was released on August 31, 2016, and iOS 10 was released on September 13, 2016.</p> 

-->

**Version 1.4.45{#ios-tvsdk}**

* Ticket #36294 - iOS TVSDK funktioniert nicht mit Xcode 10

   * Korrektur der Kompilierungsprobleme mit TVSDK in XCode 10. Aufgrund der XCode 10-Anforderungen erfordern Apps, die auf TVSDK für iOS ab Version 1.4.45 basieren, ein minimales Bereitstellungsziel als iOS 7.0

* Ticket #36321 - Diskrepanz im suchbaren Bereich zwischen PTMediaPlayer- und AVPlayer-Instanz im Status &quot;Wiedergabe&quot;.
* Ticket #36493 - `libstdc++` Unterstützung für iOS 12

   * Korrektur der Kompilierungsprobleme mit TVSDK in iOS 12. Für Apps, die auf TVSDK für iOS ab Version 1.4.45 basieren, ist ein minimales Bereitstellungsziel als iOS 7.0 erforderlich.

**Version 1.4.44**

* Ticket #34683 - Die Zeit für die Anzeigenwiedergabe läuft negativ

   * Zusätzliche Prüfungen, die durchgeführt werden, um den Fall zu verarbeiten, wenn eine Abweichung zwischen der vom Anzeigen-Server gemeldeten Dauer und dem tatsächlichen Anzeigeninhalt besteht.

* Ticket #34801 - currentTime und localTime wurden beim Suchen nach einer neuen Position während des Status &quot;Angehalten&quot;nicht aktualisiert

   * Die aktuelle Zeit des Players kann jetzt auf null gesetzt werden, falls der Player angehalten wird. Zuvor wurde die aktuelle Zeit nur im Wiedergabestatus auf null gesetzt.

* Ticket Nr. 35037 - Wiedergabe wird beim Zurückkehren aus der signal-basierten Anzeigeneinfügung mit einer schlechten URL angehalten.

   * Verbesserte Fehlerbehebung für das geschlossene Problem #34385 in Version 1.4.42. Der Code für die Prüfung und Ausnahmebehandlung von isCancelled wurde hinzugefügt, um die Vorgangswarteschlange stabiler zu machen.

**Version 1.4.43**

* (ZD#32990) - iOS: Inhaltswiedergabe anstelle von Anzeigen auf einigen Cue-Punkten. Die API &quot;selectedMediaOptionInMediaSelectionGroup&quot;, die Teil der AVPlayerItem-Schnittstelle war, wurde jetzt in iOS 11 unter AVMediaSelection verschoben. Das Problem wurde mit dieser neuen API behoben.
* (ZD#33683) TVSDK entfernt == Suffix aus den Metadaten-Zeichenfolgen. Das Problem wurde in der Parsing-Logik behoben.
* (ZD#33905) - iOS TVSDK führt Aufrufe an die Manifestdateien mit zwei Benutzeragenten durch. Das Problem mit dem Benutzeragenten wurde im ersten m3u8-Aufruf behoben (Neuinstallationsfall). Die M3u8-Benutzer verfügen jetzt über die gleichen Benutzeragenten für alle Aufrufe.
* (ZD#34293) - In LINEAR-Streams eingefügte Vorrollen werden in iOS11 nicht korrekt wiedergegeben. Das Problem wurde für Pre-oll-Anzeigen behoben.
* (ZD#34684) - Wenn die Richtlinie zum Überspringen einer Anzeige angewendet wird, werden Pre-Roll-Anzeigenrahmen für einige Sekunden angezeigt. Eine neue API, enableVodPreroll, wurde eingeführt, um die Wiedergabe der Vorahmen in vod-Wiedergabe zu deaktivieren. Der Standardwert für diese API ist &quot;Ja&quot;. Die API stellt sicher, dass die Zuordnung von Anzeigeninhalten im Hauptinhalt übersprungen wird.
* (ZD#34765) - Nach dem Aufruf von stop() werden immer noch wenige Transport Streams-Segmente heruntergeladen. Die Stopp()-API wurde erweitert, um den Download der zusätzlichen Segmente zu vermeiden.
* (ZD#34865) - Pre-Roll-Anzeigen für Livestream werden auf iOS abgeschnitten. Im Zusammenhang mit iOS11 wird dieses Problem durch das Hinzufügen einer zusätzlichen Prüfung behoben, um zu überprüfen, ob es sich bei dem Stream um Pre-Roll- oder Hauptinhalte handelt.
* (ZD#35093) - Es wurde ein Failover-Szenario behoben, bei dem die Wiedergabe nicht zum Backup-Stream wechselt, wenn die Primäre Variante des Streams beim Start fehlschlägt (gibt 404 zurück).

**Version 1.4.42 (1.4.42.118)**

* (ZD#34385) - Die Wiedergabe wird beim Zurückkehren aus der signal-basierten Anzeigeneinfügung mit einer schlechten URL angehalten.

  Erhöhen Sie die maximale Anzahl gleichzeitiger Lesevorgänge für CustomAVAssetLoaderOperations, damit die Manifestlesungen weiterhin ausgeführt werden können.
* (ZD#34373) - Endbenutzer können nicht auf HDMI-verbundene Geräte streamen, wenn die Stream-Aufzeichnung verboten ist.
* (ZD#32678) - TVSDK erfasst nicht die richtigen Anzeigen-IDs in iOS.

  Die Anzeigen-ID des finalen Anzeigenmotivs wird jetzt in VHL-Pings im Fall von VAST-/VMAP-Umleitungen erfasst.
* (ZD#33904) - TVSDK wird nicht für AVFoundation-Benachrichtigungen AVAudioSessionMediaServicesWereLostNotification und AVAudioSessionMediaServicesWereResetNotification registriert.

  PTMediaServicesWereLostNotification und PTMediaServicesWereResetNotification können jetzt in der Player-App registriert werden, um die Benachrichtigungen abzurufen, wenn Media-Dienste zurückgesetzt oder verloren gehen.

* (ZD#33815) - Kunden können ihre Priorisierungs- und Normalisierungs-CRS-Regeln nicht aktualisieren, ohne eine App-Aktualisierung erforderlich zu machen.

  Die APIs getCRSRulesJsonURL und setCRSRulesJsonURL wurden zum iOS TVSDK hinzugefügt.

**Version 1.4.41 (1.4.41.76)**

* (ZD #34464) - Probleme beim Erstellen einer Referenz-App mit TVSDK Version 1.4.41

  Ab dieser Version ist Xcode 9 für die Kompilierung von TVSDK für iOS erforderlich.
* (ZD #29456) - Airplay startet im Status &quot;Angehalten&quot;

  Fehlerkorrektur - Das Pausenproblem wurde behoben, das auftrat, wenn das Video bei der Eingabe von Airplay angehalten wurde.
* (ZD #30371) - AdBreak-Startzeitänderungen, wenn mehr als 2 Anzeigen in einen linearen Stream eingefügt werden

  Behebung des Fehlers, durch den beim Versuch, Inhalte auf Apple TV wiederzugeben, die Wiedergabe vollständig verhindert wurden
* (ZD #32146) - Es wird kein PTMediaPlayerStatusError für HLS Live-Inhalt beim Blockieren der iOS 11 dev beta empfangen

  Für HLS Live- und VOD-Inhalt wird kein PTMediaPlayerStatusError empfangen, wenn Charles blockiert wird (Drop-Verbindung und 403)
* (ZD #29242) - Airplay-Videowiedergabe schlägt mit aktivierten Anzeigen fehl

  Wenn Anzeigen aktiviert sind und AirPlay die Wiedergabe eines Videos startet, wird die Videowiedergabe nie gestartet und es wird kein Fehler angezeigt
* (ZD#33341) - DRMInterface.h Trigger Build-Warnungen in Xcode 9

  Fehlerkorrektur - Bei zwei Blockprototypen in DRMInterface.h fehlt in den Parameterlisten das Wort &quot;void&quot;.
* (ZD#31979) - Wird nicht kompiliert/ausgeführt, wenn es für iPhone 7/iPhone7+ iOS 10 oder höher ist.

  Das Kompilieren von IB-Dokumenten für eine Version vor iOS 7 wird nicht mehr unterstützt
* (ZD#32920) - Leerer Bildschirm innerhalb einer Werbeunterbrechung und Abschluss von Werbeunterbrechungen

  Wenn eine Werbeunterbrechung Anzeigeninstanzen präsentiert und nach Abschluss einer Anzeigeninstanz ein leerer Bildschirm angezeigt wird
* (ZD#32509) - iOS 11-Bildschirmaufzeichnung deaktivieren Bildschirmaufzeichnung in iOS 11 deaktivieren

* (ZD#33179) - Intermittierender Ereignisfehler auf iOS11

  Behebung des Ereignisfehlers in iOS 11

**Version 1.4.40** (1.4.40.72)

* (ZD #32465) - Player kann keine zusammengeführten Wiedergabelisten verarbeiten.

  Rufen Sie finishLoadingWithError(with: Error) für AV-Stiftung auf, um alternative Streams/Trigger-Failover zu testen.

* (ZD #31951) - TVSDK-Fehler während Lizenzrotationen.

  Fehlerkorrektur - Die Lizenzrotation funktioniert jetzt einwandfrei.
* (ZD #31951) - Leerer Bildschirm innerhalb einer Werbeunterbrechung und ohne Abschluss einer Werbeunterbrechung.

  Es wurde ein Problem behoben, bei dem Facebook VPAID-Anzeigen häufig mehrere CDATA-Blöcke in einem einzelnen \&amp;lt;AdParameters\&amp;gt; VAST-Knoten zurückgaben.
* (ZD #33336) - [iOS] TVSDK - Anzeigen-Pods werden nicht ausgefüllt, obwohl von Freewheel genügend Anzeigen zurückgegeben werden.

  Eine über- und untergeordnete Beziehung zwischen Sequenzanzeige und Fallback-Anzeige und Sortierung basierend auf der übergeordneten Sequenz und dem Index wurde erstellt.

**Version 1.4.39** (1.4.39.43)

* (ZD #32178) - iOS TVSDK-Version ist nicht korrekt.

  Die TVSDK-Versionsausgabe in den Protokolldateien war 1.0.211. Es ist behoben, um die richtige Version auszugeben.

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

* (ZD #29281) - iOS: Hinzufügen von AdSystem und Creative Id zu CRS-Anforderungen

Nutzung der kreativen ID und des AdSystem in CRS-Anforderungen basierend auf CRS-Normalisierungsregeln

* (ZD #29176) - Absturz auf PTAdPolicyDeligate satAdBreakAsWatched:position

Absturz aufgrund leerer AdBreak wird jetzt verarbeitet.

* (ZD #30125) - Programmatische Anzeigen funktionieren nicht auf der iOS-Plattform

Unterstützung für programmatische Anzeigen in iOS hinzugefügt.

* (ZD #30782) - #EXT-X-PROGRAM-DATE-TIME Notification

Das zeitgesteuerte Metadatenereignis wird nicht für das Tag # EXT-X-PROGRAM-DATE-TIME mit LIVE DRM-Streams ausgelöst.

**Version 1.4.37 (1.4.37.842)**

* (ZD #28950 ) - Problem mit der VOD-Wiedergabe

Problem bei der Wiedergabe, wenn das Tag # EXT-X-PLAYLIST-TYPE im Stream auf &quot;Event&quot;anstatt auf &quot;VOD&quot;gesetzt ist

* (ZD #29281) - iOS: Hinzufügen von AdSystem und Creative Id zu CRS-Anforderungen

Nutzung von Creative Id und AdSystem in CRS-Anforderungen basierend auf CRS-Normalisierungsregeln.

* (ZD #29462) - TremorHub-Anzeige in A&amp;E VOD, die zu einem Absturz in iOS-Apps führt

**Version 1.4.36 (1.4.36.835)**

* (ZD #29418) - Fälle mit einer Dauer von 0 (#EXT-X-CUE-OUT:0.000) führen dazu, dass iOS TVSDK die Wiedergabe stoppt oder abstürzt.

Das Problem wurde behoben und die Wiedergabe wird ordnungsgemäß gestartet.

* (ZD #29462) - Ad in VOD verursacht einen Absturz auf iOS TVSDK .

Das Problem wurde behoben. iOS TVSDK löst eine Ausnahme (AUDNetworkAdInfo::initWithAdId) aus und verarbeitet sie nicht. Die Ausnahme ist auf eine leere Anzeigen-ID zurückzuführen.

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

* (ZD# 28481) - FER-Ausfall aufgrund des falschen Schlüssels, der am Ende einer Werbeunterbrechung für diese FER-Streams angehängt wird

Bei einem FER-Stream wird der Schlüssel vor der Werbeunterbrechung nach dem Ende der Werbeunterbrechung eingefügt. Dieses Problem wurde behoben, indem die *last seen key* am Ende der Werbeunterbrechung.

**Version 1.4.33** (1.4.33.803 für iOS 6.0+)

* (ZD# 21701) CRS für Unterkonten aktivieren

Aktiviert durch Senden der ursprünglichen kreativen URL für die CRS-Anforderung 1401 anstelle der normalisierten URL gemäß der Anforderung für das CRS-Backend.

* (ZD# 26218) - Ladeproblem PSDKResources.bundle

Dieses Problem wurde behoben, indem das Laden der Ressource so aktualisiert wurde, dass es von allen verfügbaren Bundles aussieht.

* (ZD# 27460) Midroll First Ad-Aufruf - POST zu cdn.auditude<span></span>.com gibt 403 zurück.

Das neue CDN-Konto kann eine POST-CDN-Anfrage nicht verarbeiten. Dieses Problem wurde behoben, indem der Code aktualisiert wurde, um die `cdn.auditude.com` -Anzeigenanforderung GET anstelle von POST sein.

**Version 1.4.32** (1.4.32.792 für iOS 6.0+)

* (ZD# 27132) Unterstützung von Dezimalwerten für VMAP-Anzeigenunterbrechungen.

Wenn Inhalte nicht entlang der definierten Werbeunterbrechungen segmentiert wurden, führten Ganzzahlen zu unerwarteten Anzeigenplatzierungen. Das Problem wurde behoben, indem die Dezimalwerte nicht in Ganzzahlen konvertiert wurden.

* (ZD# 27189) AES-Inhalte mit dem Tag EXT-X-DISCONTINUITY-SEQUENCE werden nicht korrekt wiedergegeben.

Das Problem wurde behoben, indem das -Tag am Anfang der Wiedergabeliste platziert wurde.

**Version 1.4.31** (1.4.31.785 für iOS 6.0+)

* (ZD# 24528) Implementieren von TVSDK-Nutzungsmetriken für die Rechnungsstellung

Weitere Informationen finden Sie unter [Abrechnungsmetriken](../programming/tvsdk-1.4-for-ios/c-psdk-ios-1.4-billing/c-psdk-ios-1.4-billing.md).

* (ZD# 24642) Bild-in-Bild-Unterstützung für TVSDK

Die Bildfunktion, die in einigen Fällen nicht richtig funktionierte, wurde behoben.

* (ZD# 25246) Falsche Anzeigenunterbrechungssignale

Dieses Problem wurde behoben, indem Diskontinuitäts-Tags über Variantenmanifeste hinweg ausgerichtet wurden.

* (ZD# 26218) Der Prozess zum Erstellen von Anwendungen wird kompliziert, wenn versucht wird, PSDKLibrary.framework in das Anwendungs-Framework des Clients einzubinden

Dieses Problem wurde behoben, indem das PSDKLibrary.framework wie angefordert verpackt wurde.

* (ZD# 26364) Multi-CDN-Unterstützung für CRS-Anzeigen
<!-- 
Comment Type: draft
For more information, see [Multiple CDN support for CRS Ad Delivery](http://help.adobe.com/en_US/primetime/psdk/ios/1.4/index.html#PSDKs-concept-Multiple_CDN_support_for_CRS_ad_delivery).
-->
* (ZD# 27028) Verzögerung bei der Wiedergabe einiger Streams in iOS 10.

Dieses Problem wurde behoben, indem eine Problemumgehung für Streams ohne M3U8-Erweiterung bereitgestellt wurde.

**Version 1.4.30** (1.4.30.754 für iOS 6.0+)

In dieser Version wurden die folgenden Probleme für TVSDK behoben:

* (ZD# 24180) Fügen Sie der Zulassungsliste eine benutzerdefinierte Kopfzeile hinzu.

Der TVSDK-Zulassungsliste wurde eine neue benutzerdefinierte Kopfzeile hinzugefügt.

* (ZD# 25016) Failover-Stream wird zufällig ausgewählt, wenn ABR-Steuerungsparameter festgelegt werden

Dieses Problem wurde behoben, indem die ABR-Streams in der richtigen Reihenfolge verwaltet wurden, wenn die ABR-Einstellungen mit der Einstellung initialBitrate für einen Stream bereitgestellt wurden, der Failover-URLs enthält. Dadurch wird verhindert, dass die Failover-Streams anstelle von &quot;primary&quot;wiedergegeben werden.

* (ZD# 25076) Absturz auf PTAuditudeAdResolver loadComplete

Das Problem, bei dem während des schnellen Starts/Stopps mehrerer PTMediaPlayer-Instanzen mit Anzeigen ein Absturz auftrat, wurde behoben.

* (ZD# 25960) Es werden keine zusätzlichen abonnierten Tags ausgelöst, die Benachrichtigungen zu Änderungen an Metadaten auslösen

Das Problem, dass ein abonniertes Tag nicht benachrichtigt wird, wenn es angezeigt wird, bevor das erste Segment im Manifest angezeigt wird, wurde behoben.

* (ZD# 26084) PSDK mit 106000.101000.-11833 Decoder konnte beim Übergang von der letzten Werbeunterbrechung zurück zu Unterhaltungsinhalten keinen Fehler finden

Wenn die letzte Startzeit der Werbeunterbrechung vom VMAP vor Abschluss der Gesamtdauer fällt, wird der Schlüssel unter bestimmten Bedingungen erst nach dem Ende der letzten Werbeunterbrechung eingefügt. Dieses Problem wurde behoben.

* Die Video Heartbeat Library (VHL) wurde auf Version 1.5.9 aktualisiert, um die folgenden Probleme zu beheben:

   * (ZD #22351) VHL - Analytics: Live-Video-Asset-Dauer

Dieses Problem wurde behoben, indem die assetDuration-API zu `PTVideoAnalyticsTrackingMetadata` , um die Asset-Dauer für Live-/Linear-Streams zu aktualisieren und eine Logik zur Überprüfung des Live-Streams bereitzustellen.

* (ZD# 22675) VHL - Analytics: Aktualisieren der Dauer von Live-Video-Assets

Dieses Problem ist mit ZD #22351 identisch.

* (ZD #25908) VHL - Analytics: Adobe Heartbeat Event Crash

Dieses Problem wurde behoben, indem die Implementierung so aktualisiert wurde, dass die neueste Version von VHL für iOS Version 1.5.9 verwendet wird, um Stabilität und Leistung zu verbessern.

* (ZD #25956) VHL - Analytics: Absturz bei wiederholter Wiedergabe von Videos

Dieses Problem ist mit ZD #25908 identisch.

**Version 1.4.29** (1.4.29.743)

* (ZD# 23901) Anzeigen von Drittanbietern werden nicht wiedergegeben

Dieses Problem wurde behoben, indem zur URL-Struktur von CRS v3 gewechselt wurde, um die Zonen-ID in die neu gepackte URL aufzunehmen.

* (ZD #25183) Probleme mit der DRM-Wiedergabe auf tvOS und iOS

Dieses Problem wurde behoben, indem Unterstützung für mehrere Schlüssel-Tags bereitgestellt wurde, die für die Unterstützung mehrerer DRM benötigt werden.

* (ZD# 25334) TVSDK kann freigegebene cDVR-Inhalte nicht wiedergeben

Dieses Problem wurde behoben, indem TVSDK daran gehindert wurde, leere Zeichenfolgen in absolute URLs zu konvertieren.

* (ZD# 25347) Festlegen eines benutzerdefinierten HTTP-Headers auf AVURLAsset

Unterstützung für benutzerdefinierte Header für Segmentanforderungen über die Klasse PTNetworkConfiguration wurde hinzugefügt.

**Version 1.4.28** (1.4.28.722)

* (ZD #24549) Mehrere Anzeigen-Tracking-Aufrufe

Dieses Problem wurde behoben, indem der Timeline-Manager aktualisiert wurde, um auf Benachrichtigungen zu einem bestimmten Objekt zu warten, wenn mehrere Player erstellt werden.

* (ZD #24758) PTManifestLogger unterstützt iOS 8 nicht

Dieses Problem wurde behoben, indem die Bibliothek des Logger-Dienstprogramms auf das Bereitstellungsziel der Version 7.0 aktualisiert wurde.

* (ZD #24775) Verzögerter Stream aufgrund von Anzeigen

Dieses Problem wurde behoben, indem die Dauer der Verschiebung auf Ereignisspiellisten korrekt berechnet wurde.

* (ZD #24799) Einige der Episoden werden nicht in der iOS APP wiedergegeben

Dieses Problem wurde durch die Verwendung des lokalen Webservers für Untertitel behoben, wenn die WebVTT-Dateien geografisch eingeschränkt sind.

**Version 1.4.27** (1.4.27.711) für iOS 6.0+

* (ZD #24089) - Optimierungen für die Anzeigenauflösung in langen DVR-Streams

Dieses Problem wurde behoben, indem mehrere Optimierungen hinzugefügt wurden, um die für die Verarbeitung des DVR-Fensters in Live-/linearen Streams erforderliche Zeit zu verkürzen.

* (ZD #21554) - TVSDK-Fehlerbeacons werden nicht für application-type = video/mp4 ausgelöst

Dieses Problem wurde behoben, indem der Player die richtigen Fehler-Tracking-URLs für ungültige Asset-Formate pingen konnte.

* (ZD #24424) - Absturz des Typs EXC_BAD_ACCESS KERN_INVALID_ADDRESS stammt von PSDKLib für iOS auf neueren Hardwaregeräten.

Der Absturz, der aufgrund einer nicht zugewiesenen Medienplayer-Instanz aufgetreten ist, wenn die Wiedergabe zwischen verschiedenen Streams schnell umgeschaltet wird, wurde behoben.

* (ZD #24575) - Absturz in TVSDK auf 32-Bit-Geräten bei enableDebugLog=true

Das Problem im Protokollformat, das den Absturz auf 32-Bit-Geräten verursachte, wenn die Protokollierung aktiviert ist, wurde behoben.

**Version 1.4.26** (1.4.26.702) für iOS 6.0+

* (ZD# 20213) - TVSDK FW muss dynamisch/modularisiert für XCode7 sein

   * Korrigiert durch Aktualisierung der Bibliotheken mit Modulunterstützung

**Version 1.4.25** (1.4.25.684) für iOS 6.0+

* (ZD #19629) - Live-Video wird angehalten, wenn Airplay zu ATV 4 aufgerufen wird

Dieses Problem wurde behoben, indem eine Wartezeit hinzugefügt wurde, nachdem alte Elemente entfernt wurden, aber bevor neue Elemente zum AVQueuePlayer hinzugefügt wurden. Ohne Wartezeit werden Benachrichtigungen an das falsche Element gesendet.

* (ZD #19856) - Standardmäßig werden keine Untertitel angezeigt, wenn sie aktiviert sind

Die Probleme in der Webvtt-Wiedergabeliste, die dazu führten, dass die Untertitel nicht korrekt angezeigt wurden, wurden behoben.

* (ZD #21590) - Videoleistung und -verfolgung in den neuesten Origin Builds

Das Problem mit der fehlenden Videolänge in VideoAnalytics wurde behoben.

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

Dieses Problem wurde behoben, indem VideoAnalyticsTracker aktualisiert wurde, um beim Übergang zwischen Kapitel- und Nicht-Kapitelgrenzen Kapitelstart/-abschluss ordnungsgemäß zu erkennen.

* (ZD #20784) - Analytics: Auslösen von Inhaltsbeendigungen für Live-Videoübergänge

Dieses Problem wurde behoben, indem eine Logik hinzugefügt wurde, um den Abschluss von Inhalten während einer Videoverfolgungssitzung manuell Trigger.

Die folgenden Bibliotheken wurden aktualisiert:

* AdobeMobile-Bibliothek auf 4.10.0
* VHL-Bibliothek zu 1.5.6
* VHL-Nielsen-Bibliothek zu 1.6.7
* (ZD #21855) - Untertitel werden nach dem Mid-Roll nicht abgespielt

In diesem Problem führten doppelte Diskontinuitäts-Tags dazu, dass nach der Mid-Roll keine Untertitel angezeigt wurden. Dieses Problem wurde behoben, indem die Diskontinuitäts-Tags nebeneinander entfernt wurden.

* (ZD #21994) - String out-of-bounds in PTHLSUtils

Die wahrscheinlichste Ursache des Absturzes ist, wenn ein EXT-X-KEY über eine URL verfügt, die von Anführungszeichen umgeben ist.

* ZD #22074) - AUDVAST-Absturz tritt einmal pro Minute auf iOS auf

In Version 1.4.23 wurde der Absturz behoben, der durch das Vorhandensein unsicherer Zeichen in einer VAST-Umleitungs-URL verursacht wurde. TVSDK hat diese Anzeigen jedoch weiterhin übersprungen.

Dieses Problem wurde behoben, indem die unsicheren Zeichen verarbeitet und die Anzeigen wiedergegeben wurden.

* (ZD #22694) - PTMediaPlayer.  Ansicht nach Player ausgeblendet

Dieses Problem wurde behoben, indem die Logik so aktualisiert wurde, dass die Player-Ansicht eingeblendet wird, wenn eine VPAID-Anzeige nicht wiedergegeben werden kann.

**Version 1.4.23** (1.4.23.641) für iOS 6.0+

* (ZD #18016) - Keine Antwort vom Primetime SDK mit schlechter Netzwerkbedingung

Dieses Problem wurde behoben, indem die Fehlerbenachrichtigung verbessert wurde, wenn ein schwerwiegender Fehler von AVFoundation auftritt, und indem der App ermöglicht wurde, den Neustart nach dem Fehler zu handhaben.

* (ZD #20580) - Absturz in PTSplicerManager

Dieses Problem wurde behoben, indem ein zusätzlicher Schutz vor gleichzeitigen Problemen bereitgestellt wurde, die den Absturz verursachen.

* (ZD #21782) - iOS-Fehlercode 10100

Das Problem, dass das TVSDK beim Starten der Wiedergabe auf Adobe Access DRM Streams einen Fehler vom Typ 101000 zurückgab, wurde behoben.

* (ZD #21889) - Die Wiedergabe von Online-Anzeigen und Offline-Inhalten schlägt fehl

Das Problem, bei dem die Wiedergabe fehlschlug, nachdem eine Anzeige auf AES-verschlüsselten Offline-Inhalten fehlschlug, wurde behoben.

* (ZD #22074) - AUDVAST-Absturz tritt einmal pro Minute auf iOS auf

Dieses Problem wurde behoben, indem die Handhabung von VAST-Anzeigen-Tags von Drittanbietern verbessert wurde, die ungültige Zeichen in der URL enthalten.

* (ZD #2257) - TVSDK kann DRM-Stream nicht wiedergeben

Das Problem, bei dem das TVSDK, das beim Starten der Wiedergabe auf Adobe Access DRM Streams einen Fehler vom Typ 101000 zurückgab, wurde behoben.

**Version 1.4.22** (1.4.22.627) für iOS 6.0+

* (ZD #18709) - Absturz im TVSDK für iOS

Das Problem eines Absturzes bei einigen Adobe Access DRM-geschützten Streams wurde behoben.

* (ZD #18850) - Aktualisieren der kreativen Auswahllogik basierend auf CRS-Regeln

Dieses Problem wurde behoben, indem eine .json -Konfigurationsdatei hinzugefügt wurde, um die Priorität der kreativen Auswahl anzugeben.

* (ZD #19770) - Protected AES Video Feed wird nicht mehr wiedergegeben

Das Problem, dass 302 umgeleitete Streams nicht abgespielt wurden, wurde behoben.

* (ZD #19629) - Live-Video wird angehalten, wenn Airplay zu ATV 4 aufgerufen wird

Dieses Problem wurde behoben, indem eine Behelfslösung für die Live-Videopause hinzugefügt wurde, wenn die Wiedergabe für Apple TV 4-Geräte aktiviert ist. Das Problem scheint ein Apple TV 4-Problem zu sein.

* (ZD #21119) - Das TVSDK wird nach der Anzeigenwiedergabe angehalten

Unterstützung für AES-verschlüsselte Streams mit einer Sequenz IV während der Verwendung von Anzeigeneinfügungen hinzugefügt.

* (ZD #21125) - Rückgabe von Live-/linearen Werbeunterbrechungen früh

Es wurde Unterstützung für die Rückkehr von einer Werbeunterbrechung frühzeitig vor der Wiedergabe der Werbeunterbrechung bis zum Abschluss hinzugefügt. Die frühe Rückgabe wird durch ein benutzerdefiniertes Manifest-Tag angezeigt.

* (ZD #21224) - Airplay-Unterstützung für tokenisierte Streams von Akamai

Zur Klasse PTNetworkConfiguration wurden APIs hinzugefügt, um Cookies als URL-Parameter an Segmente für bestimmte Akamai-tokenisierte Streams anzuhängen.

* (ZD #21287) - Fremdprotokoll

Ein Problem mit einigen Protokollanweisungen, die standardmäßig in der xcode-Konsole angezeigt werden, selbst wenn die Protokollierung deaktiviert ist, wurde behoben.

* (ZD #21446) - Ad Break-Ereignisse werden manchmal nicht vom TVSDK ausgelöst

In Ereignis-Streams werden Werbeunterbrechungen im vorherigen Release-Build nicht korrekt ausgelöst. Dieser Build behebt dieses Problem.

**1,4,21** (1.4.21.605) für iOS 6.0+

* (ZD #20749) - Fallback überspringt nicht leere VAST-Antworten; zusätzliche Anzeigen-Tracking-URLs werden ausgelöst

Ein Problem mit doppelten Pings für Fallback-Anzeigen wurde behoben.

**1.4.20** (1.4.20.590) für iOS 6.0+

* (ZD #18639) - Das TVSDK verwendet übermäßige CPU/Ressourcen für ein langes Hot-Recording-Asset.

Die übermäßige CPU-/Ressourcenbelegung wurde auf beiden Ebenen behoben. Zunächst muss die Funktion für die Zeitaktualisierung auf einer globalen Warteschlange anstatt des Haupt-Threads ausgeführt werden und die CPU-Auslastung für die Analyse des Manifests mit dem zuvor verarbeiteten und zwischengespeicherten m3u8 optimiert werden.

* (ZD #19349) - Pre-Roll-Anzeigen werden beim Einschränken der Netzwerkverbindung übersprungen.

Dieses Problem wurde behoben, indem ein Timeout-Ereignis (requestTimeout) für die Anwendung und die adMetadata bereitgestellt wurde.  adRequestTimeout-API zum Überschreiben des standardmäßigen 10-Sekunden-Timeouts.

* (ZD #19446) - Fehlende Benachrichtigung bei Live-Streams

Dieses Problem wurde behoben, indem die Anwendung das Abonnement des EXT-X-PROGRAM-DATE-TIME für Live-Streams ermöglichte.

* (ZD #19459) - Absturz beim Vorbereiten von alternativem Audio mit PTMediaPlayerItem prepareAudioOptionsWithAVMediaSelectionOptions
* (ZD #19460) - Absturz - [PTMediaPlayerItem prepareSubtitlesOptionsWithAVMediaSelectionOptions:nonForcedOptions:]

Dieses Problem ist mit dem Zendesk #19459 identisch.

* (ZD #19574) - Das TVSDK gibt keine M3U8-Antwortdaten für DRM- oder Nicht-DRM-Inhalte zurück

Beim ersten Laden der Manifestdatei in PTMediaPlayerItem.prepareToPlay meldet das TVSDK bei fehlgeschlagenem Laden des Manifests nicht den Hauptteil der Fehlerantwort an die Anwendung.

Dieses Problem wurde behoben, indem TVSDK die Fehlerantwort als Fehler an die Anwendung melden konnte.

* (ZD #19615) - Die Fallback-Logik funktioniert nicht

In der aktuellen Implementierung wurden Fallback-Anzeigen übersprungen und nicht neu verpackt, es sei denn, diese Anzeigen weisen das Format m3u8 auf. Dieses Problem wurde behoben, indem auch die Unterstützung für Neuverpackung von Fallback-Anzeigen hinzugefügt wurde.

* (ZD #19770) - Das TVSDK kann keine geschützten AES-Inhalte mit 302-Umleitung wiedergeben

Das Umleitungsproblem wurde behoben, da die Umleitungs-URL von cleanConnectionData gelöscht wurde, bevor sie zum Analysieren des Manifests verwendet werden konnte.

* (ZD #19856) - Untertitel werden für einige Bitraten nicht angezeigt, wenn sie standardmäßig aktiviert sind

Dieses Problem wurde behoben, indem der Fehler von iOS für die Streams behoben wurde, in denen die Untertitel nicht angezeigt wurden.

* (ZD #19868) - Das TVSDK stürzt ab, wenn ein ungültiger kreativer Benutzer zum Tracken gebracht wird

Der Absturz im TVSDK, bei dem eine Instanz des riesigen Parsers fälschlicherweise verzögert wurde, wurde behoben.

* (ZD #20180) - VPAID-Anzeigen werden gelegentlich übersprungen

Der JavaScript-MIME-Typ wurde nicht immer einbezogen oder wurde als gültiger MIME-Typ betrachtet. Dieses Problem wurde behoben, indem JavaScript als gültiger MIME-Typ eingefügt wurde.

* (ZD #20749) - Fallback überspringt nicht leere VAST-Antworten; zusätzliche Anzeigen-Tracking-URLs werden ausgelöst

Das Problem, dass einige Kreative nicht neu verpackt werden, wurde behoben.

**Version 1.4.19** (1.4.19.563) für iOS 6.0+

* ZD #18639) - Das TVSDK verwendet übermäßige CPU/Ressourcen auf einem langwierigen Hot-Recording-Asset.

Dieses Problem wurde behoben, indem das Umschreiben der DRM m3u8-Wiedergabeliste in Cache-Bit der Wiedergabeliste optimiert wurde, die zuvor umgeschrieben wurden. Dies ist am relevantesten, wenn Sie Live-m3u8-Streams wiedergeben, für die m3u8 nach jedem Segmentdownload heruntergeladen wird.

* (ZD#18956) - player.drmManager ist nil, wenn der Haltepunkt im iOS Demo Player festgelegt ist

Dieses Problem wurde behoben, indem die API-Implementierung PTMediaPlayer.drmManager aktualisiert wurde, um DRMManager aus dem DRM-Framework abzurufen.

**Version 1.4.18** ( 1.4.18.557) für iOS 6.0+

* (ZD #18844) Tracking-Abspielleiste für Live-Inhalte im iOS-Player.

Dieses Problem wurde behoben, indem die Anwendungen einen eigenen Abspielleistenwert festlegen konnten.

* Zendesk #18518 - Wenn der Videoname nicht angegeben ist, lautet der Name des TVSDK standardmäßig *PSDK-basierter Player.*

Dieses Problem wurde behoben, indem der Standardwert für den Player-Namen entfernt wurde.

**Version 1.4.17** (1.4.17.545) für iOS 6.0+

* Zendesk #2228 - Enhance the TVSDK to return JSON response of the fetching of a manifest

Anstatt einen Fehler zu senden, wenn der Inhalt nicht M3U8 ist, gibt das DRM-Framework eine Null-DRMMetadata zurück. Das Problem wurde behoben, indem Metadaten hinzugefügt wurden, um Inhalte verfügbar zu machen, wenn die Benachrichtigung M3U8_PARSER_ERROR auftritt.

* Zendesk #2231 - Fehler beim Abrufen des Manifests, das in MediaPlayerNotification nicht verfügbar ist

Gleiche Auflösung wie Zendesk #2228

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` Nicht befülltes Makro

Das Problem, dass das Auditude SDK einen Ping nicht sendet, wenn die Tracking-URL zu Beginn Leerzeichen aufweist, wurde behoben.

* Zendesk #17294 - Crash SecKeyRawSign

Ein möglicher Absturz, bei dem der Code des Kunden die Schlüsselkette verwendet, wurde behoben.

* Zendesk #18008 - Unterstützung von Cookies für iOS8+ zur Unterstützung von tokenisierten Streams

Akamai-tokenisierte Streams erfordern, dass Cookies bei Segmentanfragen gesendet werden. Dies war in iOS 7 und früher nicht möglich. Ab iOS 8 hat Apple eine API hinzugefügt, mit der für Segmentanfragen Cookies übergeben werden können. Diese Unterstützung ist jetzt im TVSDK verfügbar. Es wurde auch Unterstützung für das Senden eines Benutzeragenten hinzugefügt, sofern verfügbar.

* Zendesk #18166 - TVSDK 1.4.15 gibt Hunderte von Warnungen beim Kompilieren mit DWARF mit dSYM-Dateioptionen

Alle Warnungen wurden behoben.

**Hinweis**: Für TVSDK wurden tvOS-kompatible Bibliotheken hinzugefügt.

**Version 1.4.16** (1.4.16.1454)

* Zendesk #3875 - Tab S stürzt während der Wiedergabe ab

Zurücksetzen der Abhängigkeit von OKHTTP für die Auditude für CRS, da TVSDK jetzt direkt die HTTPS-Verbindung anstelle von curl verwendet. Das Problem wurde durch das Löschen von Ausnahmen behoben, bevor ein weiterer JNI-Aufruf durchgeführt wurde.

* Zendesk #4487 - Tracking Linear Channel of Content

Das Problem wurde behoben, indem der Video Heartbeat-Tracker während einer linearen Stream-Wiedergabesitzung neu initialisiert wurde.

* Zendesk #17919 - Android - Content Suchen verursacht Heartbeat-Fehler

Das Problem bestand darin, den Heartbeat in einem Fehlerstatus zu beheben, wenn in einem Kapitel eine Suche vorhanden war

* Zendesk #18053 - Anwendung mit TVSDK stürzt auf Marshmallow ab

Das TVSDK stürzte unter Android M OS ab, wenn die TVSDK-Bibliothek einen Neon-Code verwendet, der eine YUV -> RGB-Farbkonvertierung bewirkt. Dieses Problem wurde behoben, indem die Funktionen aktualisiert wurden, die dieses Problem verursachen, indem eine Nicht-Neon-Version des Codes verwendet wurde.

* Zendesk #18072 - Android M - Application Crash

Dieser Absturz tritt beim Aufruf der MediaCodecList- und MediaCodecInfo-APIs auf, wenn geprüft wird, ob das Profil und die Ebene unterstützt werden. Adobe sucht nach Google-Unterstützung für weitere Einblicke. Dieses Problem wurde behoben, indem eine temporäre Bearbeitung bereitgestellt wurde, indem alle Codec-Informationen vorzeitig geladen wurden, um zu vermeiden, dass diese APIs nur dann aufgerufen werden, wenn Codec-Informationen benötigt werden.

* Zendesk #18074 - Arabische Untertitel, die nicht auf Nexus mit Android 6.0 funktionieren

Dieses Problem wurde behoben, indem Unterstützung für die Android CTS-Schriftzuordnung bereitgestellt wurde.

**Version 1.4.15** (1.4.15.512) für iOS 6.0+

**Hinweis**: Das Nielsen-Modul wurde aus dem TVSDK-Build entfernt, aber das TVSDK wird in naher Zukunft mit einem neuen Nielsen-Integrationsmodul aktualisiert.

* (ZD #2228) - Fehler beim Abrufen des Manifests, der in MediaPlayerNotification nicht verfügbar ist

Metadaten wurden hinzugefügt, um Inhalte anzuzeigen, wenn die Benachrichtigung M3U8_PARSER_ERROR auftritt.

* (ZD #4437) - Abstürze innerhalb des Adobe Primetime SDK

Fehlerkorrektur - Es wurde ein gemeldeter Absturz bei der Vorbereitung von Untertiteln/alternativen Audioinhalten behoben.

* (ZD #4487) - Tracking Linear Channel of Content

Zulässige Neuinitialisierung des Video Heartbeat Tracker während einer linearen Stream-Wiedergabesitzung.

**Version 1.4.14** (1.4.14.498) für iOS 6.0+

* (ZD #17260) - Absturz auf playlistManagerForURL

Es wurde ein zeitweiliger Absturz aufgrund von Gleichzeitigkeitsproblemen behoben.

**Version 1.4.13** (iOS 6.0+)

* (ZD #3304) - VAST 3.0 `[ERRORCODE]` Nicht befülltes Makro

   * Der Fehler-Code 400 wird angezeigt, wenn Inline-Werbung schlechte Kreativinhalte aufweist.
   * `[ERRORCODE]` -Makro wird URL-kodiert.

* (ZD #3865) Heartbeat-Integration mit IMA-Anzeigen

Es wurde ein Fehler behoben, durch den die Videolänge falsch gemeldet wurde.

* TVSDK-Demo-Player für iOS 9 aktualisiert

Um iOS 9 ordnungsgemäß zu unterstützen, müssen Sie die Ausnahmen von Application Transportation Security konfigurieren. Für die Demo ist das ATS vollständig deaktiviert.

**Version 1.4.12** (1.4.12.464) für iOS 6.0+

* (ZD #4521) Client-seitiges CRS-Testen und SSAI

Fehlerhaftes Reverse MD5 in 3P-URL behoben.

**Version 1.4.12** (1.4.12.463) für iOS 6.0+

* (ZD #2751) CSAI und CRS | Verbesserung: Behandeln Sie dynamische Elemente in bestimmten Mediendatei-URLs.

Der Creative Repackaging Service wurde aktualisiert, um Anzeigen mit dynamischen kreativen URLs ordnungsgemäß zu verarbeiten.

* (ZD #3654) Memory Leak in PSDK-Version nach 1.3.4.166

Speicherleck in drmFramework mit regulärer Wiedergabe auf iOS 8.2-Geräten behoben

* (ZD #3988) Die Vorbereitung wird bei der Suche nach der ersten Wiedergabe übersprungen.

Es wurde ein Fehler behoben, sodass Anzeigenrichtlinien ordnungsgemäß deaktiviert werden konnten.

* (ZD #4017) iOS-API anfordern, die Anzeigenwiedergabe bei der Rückwärtssuche zu erzwingen

Behoben mit Korrektur für ZD #4279

* (ZD #4279) HLS TVSDK-Anzeigeneinfügung -302 Umleitungsproblem auf iOS und Desktop

Es wurde ein Fehler behoben, durch den ein Anzeigen-Asset eine relative Umleitungs-URL verwendet hat

**Version 1.4.9** (1.4.9.427) für iOS 6.0+

* (ZD #3075) Problem mit der Interneterreichbarkeit - iOS

Es wurde eine Benachrichtigung hinzugefügt, die erkennt, wann die Wiedergabe angehalten wurde.

* (ZD #3193) Anfrage für eine Profiländerungs-API in TVSDK

PTPlaybackInformation wurde aktualisiert und zeigt jetzt die aktualisierte displayedBitrate an. Die BITRATE_CHANGE-Benachrichtigung wurde aktualisiert, um die zeitliche Zuverlässigkeit und Genauigkeit der gemeldeten Bitraten des M3U8 zu verbessern.

* (ZD #3324) Problem mit der Meldung von Primetime-Anzeigen, wenn keine Anzeigenmedien in VMAP vorhanden sind

Unterstützung für Ping von leeren Tracking-URLs für Werbeunterbrechungen. TVSDK überprüft jetzt den Start von Werbeunterbrechungen und vollständige Pings für leere Werbeunterbrechungen

**Version 1.4.8** (1.4.8.402)

* (ZD #3158) IOS 7 stürzt bei vollständiger Ereigniswiedergabe ab

**Version 1.4.7** (1.4.7.382)

* (ZD #2197) Tracking von Anzeigenfehlern. Es wurde eine Benachrichtigung hinzugefügt, dass das Asset Manifest nicht geladen werden konnte.
* (ZD #2894) Der Player führt 4 Manifestanforderungen auf oberster Ebene während der Wiedergabe durch.
* (ZD #2992) Auditude Berichterstellung über seltsame Zeiträume und Kennungen.

**Version 1.4.6**(1.4.6.325)

* (ZD #2197) Tracking von Anzeigenfehlern. Benachrichtigung hinzugefügt, dass Asset-Manifest nicht geladen werden konnte

**Version 1.4.5** (1.4.5.283)

* (ZD #2141) Analytics-Implementierung für die TreeHouse-App, Hinzufügung der Bibliothek AdobeAnalyticsPlugin.a zum Erstellen von Paketen .
* Aktualisierung der Video Heartbeats-Bibliothek auf 1.4.1.2
* (PTPALY-4226) (im Zusammenhang mit ZD #2423) Das Ausführen von DRM Reset kann zum Löschen der Daten des Anwendungsdokuments führen.

**Version 1.4.4** (1.4.4.242)

* Video Heartbeats Library (VHL) aktualisiert auf Version 1.4.1.

* (ZD #2435) TV SDK-Dokumentation zu Aktualisierungen der Analyseanforderungen

**Version 1.4.2** (1.4.2.210: iOS 6.0+)

* (ZD #1129) _player.currentItem.audioOptions gibt leer zurück
* (ZD #2109) Primetime PSDK 1.4.1.125 funktioniert nicht mit Xcode 5.1.1
* (ZD #2137) Absturz im PSDK in iOS, wenn DRM-Metadaten nicht geladen werden können

**Version 1.4.1** (1.4.1.125)

* (ZD #1107) CocoaLumberjack doppelte Symbole
* (ZD #1644) Ändern des iOS-Benutzeragenten für Targeting und Reporting
* (ZD #1850) Im iOS SDK enthaltene Cocoa Lumberjack-Dateien
* (ZD#1908) Benutzerdefinierte Tags werden von PSDK ignoriert, wenn mehr als 1 vorhanden ist

**Version 1.4.0** (1.4.0.32)

* Zendesk #1024 - Funktion zum Entfernen von Anzeigen aus dem Stream über Manifest

## Bekannte Probleme in Version 1.4 {#known-issues-in}

* In iOS TVSDK werden alle Anzeigen dem Inhaltsmanifest zugeordnet. Anzeigenverhalten werden durch Suche basierend auf der Dauer des Inhalts und der Anzeigensegmente implementiert. Wenn die Segmentdauer also nicht genau ist, endet die Suche möglicherweise nicht immer im exakten Rahmen am Anfang oder Ende der Werbeunterbrechung. Selbst wenn die Dauer des Frames beträgt, gibt es eine Toleranz, die die Plattform selbst der Suche auferlegt, und es können einige Frames oder Anzeigen oder Inhalte angezeigt werden. Dies ist eine Einschränkung der Plattform und der Funktionsweise von Anzeigen-Insertion mit TVSDK in iOS.
* Die Entscheidung zum Überspringen erfolgt in diesem Fall beim Suchereignis. Da die Anzeigensegmentdauer im Manifest jedoch nicht genau die tatsächliche Dauer der Anzeige darstellt, ist die Suche nicht frame-genau. Daher sehen Sie einige Frames der Anzeige, wenn die Anzeigenrichtlinien angewendet werden.
* RECORDING_ERROR: Beim Aufzeichnen des Bildschirms ist ein Fehler aufgetreten.
* Es kann vorkommen, dass die Lizenzrotation nicht auf iOS 11 abgespielt wird und auf iOS 9.x und iOS 10.x gut wiedergegeben wird.
* Wenn die Wiedergabe über AirPlay aktiv ist, werden VPAID-Anzeigen in VPAID 2.0-Unterstützung übersprungen.
* Das drmNativeInterface.framework wird nicht korrekt verknüpft, wenn das Mindestziel auf iOS7 (oder höher) festgelegt ist.\
  Problemumgehung: Geben Sie explizit die `libstdc++6`.  dylib-Bibliothek wie folgt: Gehen Sie zu Target->Build-Phasen->Binärdatei mit Bibliotheken verknüpfen und fügen Sie hinzu `libstdc++.6.dylib`.

* Eine Post-Roll-Anzeige wird nicht zum Ersetzen der API eingefügt.
* Bei der Suche in einer Werbeunterbrechung (ohne daraus zu werden) wird eine doppelte Anzeigenunterbrechungsbenachrichtigung ausgegeben.
* Das Festlegen von currentTimeUpdateInterval hat keine Auswirkungen.\
  Hinweis: In bestimmten iOS-Versionen lädt das Betriebssystem die Ressourcen nicht automatisch in das PSDKLibrary.framework. Es ist wichtig, das PSDKResources.bundle manuell in die Bundle-Ressourcen der Anwendung zu kopieren: Gehen Sie zu &quot;Build-Phasen&quot;und kopieren Sie Bundle-Ressourcen.
* Die Referenz-App kann nicht mit Xcode 8 oder niedrigeren Versionen erstellt werden. Ab iOS TVSDK-Version 1.4.41 verwenden Sie zum Kompilieren Xcode 9.

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
