---
title: TVSDK 1.4 für Android-Versionshinweise
description: TVSDK 1.4 für Android-Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 1.4.
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '7802'
ht-degree: 0%

---


# TVSDK 1.4 für Android-Versionshinweise {#tvsdk-for-android-release-notes}

TVSDK 1.4 für Android-Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 1.4.

## Neue Funktionen {#new-features}

**Version 1.4.43**

**Sicheres Laden der Anzeige über HTTPS**

Adobe Primetime bietet eine Option zum Anfordern des ersten Aufrufs an den Primetime-Anzeigenserver und CRS über HTTPS.

**alwaysUseAudioOutputLatency(boolean val) in der MediaPlayer-Klasse**

Wenn dieser Parameter festgelegt ist, verwenden Sie die Latenz der Audioausgabe in der Berechnung des Audio-Zeitstempels.

Es akzeptiert einen booleschen Parameterwert. Wenn der Wert `True` ist, verwendet der Client in der Berechnung des Audio-Zeitstempels die Latenz der Audioausgabe.

**Version 1.4.42**

**Teil-Anzeigenumbruch:**
TV-ähnliches Erlebnis, in der Mitte einer Anzeige zu erscheinen, ohne die Verfolgung für die teilweise überwachte Anzeige auszulösen.
Beispiel: Der Benutzer schließt sich in der Mitte (40 Sekunden) einer 90-Sekunden-Werbeunterbrechung an, die aus drei 30-Sekunden-Anzeigen besteht. Dies ist 10 Sekunden nach der zweiten Anzeige in der Pause.
* Die zweite Anzeige wird während der verbleibenden Dauer (20 Sekunden) und die dritte Anzeige abgespielt.
* Anzeigentracker für die teilweise wiedergegebene Anzeige (zweite Anzeige) werden nicht ausgelöst. Die Tracker für nur die dritte Anzeige werden ausgelöst.

**Version 1.4.41**

Keine neuen Funktionen.

**Version 1.4.40**

Keine neuen Funktionen.

>[!NOTE]
>
>Sie benötigen keine API-Änderungen, wenn Sie eine Version vor 1.4.39 verwenden.

**Version 1.4.39**

* TVSDK ist zertifiziert mit VHL 2.0.1 und mit VHL 2.0.1 mit Nielsen.
* Android TVSDK wird aktualisiert, um CRS-Anforderungen des neuen Akamai-Hosts `primetime-a.akamaihd.net` zu erstellen.
* Die neue Hostnamenkonfiguration bietet CRS-Asset-Versand sowohl über HTTP als auch über HTTPS (SSL) in größerem Umfang.
* TVSDK unterstützt die Android Oreo-Version.
* Der `AdClientFactory`-Klasse wird eine neue Funktion hinzugefügt, um die Registrierung mehrerer Opportunity Detector zu unterstützen:

   ```
   public List<PlacementOpportunityDetector> createOpportunityDetectors(MediaPlayerItem item);
   ```

   Dies sollte ein Array von PlacementOpportunityDetector zurückgeben. Jetzt können Sie mehrere Opportunity Detector. Für die Funktion zum Beenden früherer Anzeigen waren beispielsweise zwei Opportunity-Detektoren erforderlich - eine für Anzeigeneinfügung und eine andere für den frühen Ausstieg aus der Anzeige. Sie müssen diese neue Funktion nur dann implementieren, wenn Sie Ihre eigene AdvertisingFactory (und nicht DefaultAdvertisingFactory) implementiert haben. Um das vorhandene Verhalten abzurufen, müssen Sie einen einzelnen Opportunity Detector erstellen, wie in der Funktion createOpportunityDetector(), in ein Array setzen und zurückgeben:

   ```
   public class MyAdvertisingFactory extends AdvertisingFactory {  
   …  
   @Override  
   public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {  
   List&lt;PlacementOpportunityDetector&gt; opportunityDetectors = new ArrayList&lt;PlacementOpportunityDetector&gt;();  
   opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));  
   return opportunityDetectors;  
   } }
   ```

>[!NOTE]
>
>Sie benötigen keine API-Änderungen, wenn Sie eine Version vor 1.4.39 verwenden.

**Version 1.4.36**

Fehlerkorrektur für Content Skip unter Android.

**Version 1.4.35**

* **Netzwerkanzeigeninformationen**

   TVSDK-APIs bieten jetzt zusätzliche Informationen zu VAST-Antworten von Drittanbietern. Anzeigen-ID, Anzeigensystem und VAST-Anzeigenerweiterungen werden in der NetworkAdInfo-Klasse bereitgestellt, auf die über die Eigenschaft networkAdInfo für ein Ad-Asset zugegriffen werden kann. Diese Informationen können für die Integration mit anderen Ad-Analytics-Plattformen wie **Moat Analytics** verwendet werden.

**Version 1.4.31**

**Multi-CDN-Unterstützung für CRS-Anzeigen**
* Standardmäßig werden alle transkodierten Assets auf einer CDN in Adobe auf Akamai gehostet. Mit der neuesten Version bietet Adobe Creative Repackage Service (CRS) die Möglichkeit, die transkodierten Kreativelemente wie vom Kunden angegeben in mehrere CDNs hochzuladen.
* TVSDK werden neue APIs hinzugefügt, um die Angabe der endgültigen kreativen CRS-URL zu ermöglichen, wenn die Standard-URL nicht verwendet wird. Informationen zur Verwendung dieser neuen APIs finden Sie in der Dokumentation.

**Version 1.4.18**
Primetime Android TVSDK unterstützt jetzt JavaScript-kreative VPAID 2.0-Funktionen, um eine umfassende interaktive In-Stream-Anzeigenerfahrung zu ermöglichen. Weitere Informationen zu VPAID 2.0 finden Sie unter [VPAID-Anzeigenunterstützung](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/vpaid-ads/android-3x-vpaid-ads.md).

**Version 1.4.17**

AC-3 5.1 wird nur auf Amazon FireTV unterstützt.

**Version 1.4.11**

* **Ad Fallback, Dissy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103** Für VAST-Anzeigen (kreative Elemente) mit aktivierter Ausweichregel, TVSDK behandelt eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht, Ersatzanzeigen an ihrer Stelle zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Weitere Informationen finden Sie unter [Ad Fallback for VAST and VMAP ads](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-fallback/android-3x-ad-fallback.md).

* **Video Heartbeats Library (VHL) aktualisiert auf Version 1.5**
   * Möglichkeit zum Senden von Metadaten mit Video-Beginn und/oder Video/Anzeige/Beginn als Kontextdaten
   * Weniger Netzwerkverkehr - Heartbeats sind im Durchschnitt weniger und kleiner

**Version 1.4.7**

* **On-Premise-Individualisierung-** UnterstützungUnterstützung für lokale Installationen des Adobe-Individualisierungsservers, um die Individualisierungsanforderung des Kunden an einen anderen Endpunkt anzupassen.

**Version 1.4.6**

* **AES-Beispielverschlüsselung (Flash Player Version 17.0.0.134 erforderlich)**Beispielbasierte AES-Verschlüsselung wird jetzt unterstützt.

**Version 1.4.2**

* **Video Heartbeats Library (VHL) aktualisieren auf Version 1.4.0.1**

   * Es wurde die Möglichkeit hinzugefügt, verschiedene Anwendungsfälle für Analysen - von anderen SDKs oder Playern - mit den Adobe Analytics Video Essentials zu bündeln.
   * Die Anzeigenverfolgung wurde optimiert, indem die Methoden trackAdBreakStart und trackAdBreakComplete entfernt wurden. Die Werbeunterbrechung wird aus den trackAdStart- und trackAdComplete-Methodenaufrufen abgeleitet.
   * Die Eigenschaft playhead ist bei der Verfolgung von Anzeigen nicht mehr erforderlich.

* **Nielsen SDK-** IntegrationTVSDK unterstützt jetzt das Senden von Benutzerverfolgungsinformationen an das Nielsen-SDK ohne benutzerdefinierte Integration.

**Version 1.4.0**

* **Blackout-Signalisierung mit Alternate Content** ReplacementIm Rahmen des 1.4 TVSDK-Updates unterstützt das TVSDK jetzt auch das Wechseln in regionale Blackouts und die Rückgabe von linearen Inhalten. Das TVSDK kann nun zwei Manifestdateien parallel, main und alternative verarbeiten, um die Blackout-Signale auch dann zu überwachen, wenn anstelle der ursprünglichen Programmierung eine alternative Programmierung angezeigt wird.

* **Entfernen/Ersetzen von C3-** AdsJetzt ist keine zusätzliche Vorarbeit erforderlich, um neue Anzeigen dynamisch in Video-on-Demand-Assets (VOD) einzufügen, die aus dem C3-Fenster herauskommen. Das TVSDK bietet jetzt eine API zum Entfernen benutzerdefinierter Inhaltsbereiche und zum dynamischen Einfügen neuer Anzeigen. Diese leistungsstarke neue Funktion ist auch in Fällen nützlich, in denen während der Übertragung Live-/Lineare Inhalte erscheinen und sofort zur Verwendung als On-Demand-Inhalte heruntergezogen werden, ohne dass genügend Zeit zum &quot;Bereinigen&quot;des Assets erforderlich ist.

* Die Schnittstelle PlaybackEventListener verfügt über eine neue Methode namens onReplaceMediaPlayerItem, mit der Sie auf ein neues Ereignis (`ITEM_REPLACED`) warten können. Dieses Ereignis wird immer dann ausgelöst, wenn eine MediaPlayerItem-Instanz in MediaPlayer ersetzt wird. Die Clientanwendung, die diese PlaybackEventListener implementiert, muss diese neue Methode implementieren oder überschreiben.
* AdClientFactory verfügt über eine neue Funktion zur Klasse hinzugefügt, um sich für mehrere Opportunity-Detektoren zu registrieren:

   ```
   public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem item);
   
   For example for early ad exit feature, you need two Opportunity Detectors - one for ad insertion and another for  early  exit from  `ad`.
   
   To override this new function create a single Opportunity Detector, and put into an array and return:
   
   @Override
   
   public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {
   
   List&lt;PlacementOpportunityDetector&gt; opportunityDetectors = new ArrayList&lt;PlacementOpportunityDetector&gt;();
   
   opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));
   
   return opportunityDetectors;
   }
   
   }
   ```

## TVSDK-Änderungen für 1.4 {#tvsdk-changes}

* Die Schnittstelle PlaybackEventListener verfügt über eine neue Methode namens onReplaceMediaPlayerItem, mit der Sie auf ein neues Ereignis, ITEM_REPLACED, warten können. Dieses Ereignis wird immer dann ausgelöst, wenn eine MediaPlayerItem-Instanz in MediaPlayer ersetzt wird. Die Clientanwendung, die diese PlaybackEventListener implementiert, muss diese neue Methode implementieren oder überschreiben.

* AdClientFactory verfügt über eine neue Funktion zur Klasse hinzugefügt, um sich für mehrere Opportunity-Detektoren zu registrieren:

```
public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem item);
```

Beispielsweise benötigen Sie für die Funktion zum Beenden der Anzeige zwei Opportunity-Detektoren - eine für das Einfügen von Anzeigen und eine andere für den frühen Ausstieg aus der Anzeige.

Um diese neue Funktion außer Kraft zu setzen, erstellen Sie einen einzelnen Opportunity Detector, setzen Sie in ein Array und geben Sie Folgendes zurück:

```
@Override

public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {

List`<PlacementOpportunityDetector>` opportunityDetectors = new ArrayList`<PlacementOpportunityDetector>`();

opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));

return opportunityDetectors;

}

}
```

## Gerätezertifizierung und Unterstützung in 1.4 {#device-certification-and-support-in}

>[!NOTE]
>
>Die folgenden Funktionen werden von TVSDK nicht unterstützt:****
>
>* Langsames Bewegen auf jeder Plattform oder Version.
>* Live-Trick-Spiel.


**Version 1.4.43**

TVSDK 1.4.43 wurde mit Android-Geräten mit Android 6.0.1/ 7.0 und 8.1 (Oreo) zertifiziert.

* **Version 1.4.23:**

   * TVSDK 1.4.23 wurde für Android-Geräte mit Android N zertifiziert.

* **Version 1.4.18:**

   * Primetime wurde für Amazon Fire TV zertifiziert.
   * VPAID 2.0 wird nur auf Geräten mit Android 4.0 und höher unterstützt.

## Behobene Probleme in 1.4 {#resolved-issues-in}

>[!NOTE]
>
>Alle TVSDK-Kunden, die CRS verwenden, werden dringend aufgefordert, ein Upgrade auf TVSDK 1.4.39 oder höher unter iOS und Android durchzuführen. Diese Aktualisierung ist eine Ablösung der vorhandenen App-Implementierung. Überprüfen Sie nach der Aktualisierung in einem Proxy-Tool (z. B. Charles), ob die CRS-Anforderungen für kreative URLs erfüllt sind, um sicherzustellen, dass die Version im Pfad der Version 3.1 entspricht. Beispiel:
>
>`https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8`

**Version 1.4.43**

* Ticket #27143 - 5.1-Audiospur auf FireTV-Geräten kann nicht wiedergegeben werden

   * TVSDK kann jetzt AC3-Audio auf FireTV-Geräten abspielen. Die Wiedergabe erfolgt immer in Stereo.

* Ticket #33902 - Versand für sichere Anzeige über HTTPS

   * Adobe Primetime bietet eine Option zum Anfordern des ersten Aufrufs an den Primetime-Anzeigenserver und CRS über HTTPS.

* Ticket #34493 - Bluetooth-Audio-Verzögerung

   * `alwaysUseAudioOutputLatency` in der MediaPlayer-Klasse hinzugefügt. Wird eingestellt, führt dies zur Verwendung der Audio-Ausgabedatenzeit bei der Berechnung des Audio-Zeitstempels.

* Ticket #34949 - Neue Version der Video Heartbeat Library (VHL) integriert.

**Version 1.4.42 (1791)**

* Zendesk #33719: FireTV 4k Adaptive Bitrate skaliert langsam. Unterstützung für ABR für FireTV 4K-Geräte hinzugefügt.
* Zendesk #33338:  resetDRM löscht alle Daten der Anwendung.  Es wurde ein zusätzlicher Fall behandelt, bei dem Ausnahmen in Nicht-TVSDK-Threads dazu führten, dass TVSDK-Operationswarteschlangen gefüllt wurden.

**Version 1.4.41 (1776)**

* Zendesk #33002 - Companion Asset Data from TVSDK on Fire TV. Eine neue AdBannerAsset-Klasse wurde implementiert, die die Companion-Daten als Liste &lt;AdBannerAsset> zurückgibt, und AdAsset::id ist jetzt eine Zeichenfolge anstelle einer langen.
* Zendesk #32821 - Der Android Primetime-Player friert ein, wenn er auf Presentation Timestamp (PTS) für WWE trifft. Dieses Problem wurde in dieser Version behoben.
* Zendesk #33572 - VideoAnalyticsProvider Ad Beginn Crash. Dieses Problem wurde behoben, indem die richtige Kombination aus VHL+Nielsen Joint SDK Version von VideoHeartbeat.jar verwendet wurde.
* Zendesk #33355 - Fire TV: 15-Sekunden-Ausgabe Keine Fehlerbehebung von TVSDK Seite und Kunden überprüfen dies bei ihrem End- und Drittanbieter.

**Version 1.4.40 (1764)**

* Zendesk #33068 - Amazon-Lippensynchronisierungsproblem auf einem neuen Gerät. In diesen Versionen wurde ein Problem mit der Lip-Synchronisierung behoben.
* Zendesk #32215 - Android TVSDK 1.4.38 Sicherheitsprobleme `[Hotlist]`. Aktualisiert auf die neuesten OpenSSL-1.1.0 und curl-7.5.1.
* Zendesk #32920 - Leerer Bildschirm innerhalb einer Werbeunterbrechung und ohne Abschluss der Werbeunterbrechung. Es wurde ein Problem behoben, bei dem ein VPAID-Container in einen Status &quot;hängen&quot;versetzt und ein Problem behoben wurde, bei dem Facebook VPAID-Anzeigen häufig mehrere CDATA-Blöcke in einem einzigen \&amp;lt;AdParameters\&amp;gt zurückgaben; VAST-Knoten.

**Version 1.4.39 (1744)**

* Zendesk #28976 - Die Lizenzanforderung dauert mehr als eine Sekunde. Während DRM-Lizenzanforderungsaufrufe, die POST verwenden, ausgeführt werden, fügt Curl zusätzliche &quot;Erwarten: 100-continue&quot;-Header. Die Kopfzeile &quot;Expect:&quot;in TVSDK wurde entfernt.
* Zendesk #27707 - CSAI-Umgebung, die CUE IN-Markierungen nicht berücksichtigen, um Inhalte frühzeitig zurückzugeben oder wiederherzustellen. Unterstützung für mehrere Opportunitätsgeneratoren.

**Version 1.4.38 (1722)**

* Zendesk #21590 - Videoleistung und Videoverfolgung in den neuesten Herkünfte

Integration und Zertifizierung von VHL 2.0 in TVSDK, um die Barrierefreiheit in der VideoHeartbeatsLibrary-Implementierung zu verringern, indem die Komplexität der APIs verringert wird.

* Zendesk #29688 - Support für Android O Beta-Kunden.

TVSDK-Unterstützung für die neue Android Beta-Version.

**Version 1.4.36 (1713)**

* Zendesk #27392 - Inhaltsüberspringen unter Android

Um die Entschlüsselung zu ermöglichen, erweiterte das Android TVSDK fälschlicherweise den Bytebereich von Nicht-iFrame-Inhalten um 16 Byte. Die Erweiterung ist für Iframe-Streams erforderlich, nicht aber für Nicht-iFrame-Streams.

**Version 1.4.34 (1702)**

* Zendesk #27638 - Leak in cURL INet-Objekt

Das Posix cURL INet-Objekt leckte beim Halten auf dem Share Manager und dem DNS-Cache, der in den cURL-Verbindungen verwendet wurde.

Dieses Problem wurde behoben, indem das Objekt Posix cURL INet aus dem Inet-Dekonstructor gelöscht wurde.

**Version 1.4.33 (1694)**

* **OpenSSL-Bibliothek**

Die OpenSSL-Bibliothek wurde mit der OpenSSL-Version 1.0.2j aktualisiert.

* Zendesk #21701 - Senden Sie die ursprüngliche kreative URL für 1401 CRS-Anforderung anstelle der normalisierten URL.
Dieses Problem wird durch Senden der ursprünglichen kreativen URLs behoben.

* Zendesk #25023 - Videowiedergabe mit langer Dauer: Videosperre, Bildschirmflimmern
Dieses Problem wurde behoben, indem die maximalen Abmessungen des Videoformats für die Set-Top-Box-Geräte von CenturyLink festgelegt wurden.

* Zendesk #27460 - Das neue Akamai-Konto kann eine POST-CDN-Anforderung nicht bearbeiten.
Der Code wurde aktualisiert, damit die `cdn.auditude.com`-Anzeigenanforderung anstelle der POST GET ist.

* Zendesk #28245 - Der Wiedergabestatus wird nicht korrekt gemeldet, wenn die App von Hintergrund zu Vordergrund wechselt
Dieses Problem wurde behoben, indem der Wiedergabestatus, der wiedergegeben oder angehalten werden soll, korrekt wiederhergestellt wurde, wenn die Anwendung wieder im Vordergrund angezeigt wird.

**Version 1.4.32 (1682)**

* Zendesk #25779 - Sicherheitslücke in TVSDK
Für Android 4.2 und niedriger besteht eine Sicherheitslücke, wenn JavaScript in einem WebView aktiviert ist. WebView von TVSDK wurde für Geräte mit OS 4.2 oder niedriger deaktiviert. Dadurch wird die Verwendung von VPAID-Anzeigen in TVSDK auf diesen Geräten deaktiviert.

* Zendesk #26890 - Problem im SCREEN-Status (EIN/AUS) Bearbeitung Ref. Player
Wenn die Adobe Video Engine (AVE) von einem AUSGESETZTEN Status fortgesetzt wird, aktualisiert der DefaultMediaPlayer seinen Status nicht. Daher bleibt der DefaultMediaPlayer im Status &quot;AUSGESETZT&quot;, auch wenn sich die AVE in einem PLAYING-Status befindet. Dieses Problem wurde behoben, indem der Status DefaultMediaPlayer auf PLAYING gesetzt wurde, wenn ein PLAY-Status von AVE empfangen wurde, selbst wenn der aktuelle Status des DefaultMediaPlayer AUSGESETZT wurde.

**Version 1.4.31 (1675)**

* Zendesk #21974 - Ausnahmen aufgrund von Null-Objekten
   * AdIndex wird selten inkrementiert, wenn null. Dies kann auf falsche API-Aufrufe zurückzuführen sein, die für Pre-Roll adBreak empfangen wurden. Datentypen wurden korrigiert, um solche Ausnahmen zu vermeiden

* Zendesk #24714 - Deaktivierung der Fremdprotokollierung
   * TVSDK aktualisiert, um die externe Protokollierung zu deaktivieren

* Zendesk #24488 - Probleme bei der AV-Synchronisierung auf dem Fire TV
   * Korrektur durch Verbesserung der Handhabung der AV-Decoder-Threads. Insbesondere wird bei jeder Änderung der Eingabe- oder Ausgaberahmenwarteschlangen der für den Inhaltstyp des Rahmens spezifische Dekodierer-Thread ausgeführt.

* Zendesk #26551 - Beheben von CRS-Fehlern
   * Wenn die Anforderung HEAD (HTTP-Kopfzeile) lautet, müssen wir den Inhalt nicht lesen, da er leer ist. Es ist zwar ok, es zu lesen, aber alte Android (4.0.x) hängt, während wir read() aufrufen, und neuere Android geben den korrekten Wert (-1) zurück, wenn wir read() aufrufen. Auf dieser Grundlage änderte der Code, sodass er keinen Inhalt für &quot;head&quot;liest

* Zendesk #26696 Null-Zeiger-Ausnahme beim Zugriff auf TrickPlayManager
   * Korrektur, indem überprüft wird, ob das TrickPlayManager-Objekt vor der Verwendung nicht null ist.

**Version 1.4.30 (1659)**

* Zendesk #22675 Die Asset-Dauer wird für Live-/Lineare Streams nicht aktualisiert.
Dieses Problem wurde behoben, indem eine neue API, assetDuration, in PTVideoAnalyticsTrackingMetadata bereitgestellt wurde, die die Asset-Dauer für Live- und lineare Streams bereitstellt.

* Zendesk #25853 Speicherleck in TVSDK beim Wechseln von Kanälen
Das Problem, bei dem ein Dateilesepufferleck beim Zurücksetzen oder Loslassen des MediaPlayer beim Herunterladen einer Datei aufgelöst wurde.

**Version 1.4.29 (1653)**

* Zendesk #21200 - Player wird nicht vom Status &quot;Beendet&quot;zurückgesetzt, wenn die App im Hintergrund war
Wenn der Player nach dem Signieren des Stream-Switches ausgesetzt wurde, ermöglicht die Auflösung dem Player, den Stream-Schalter auszuführen, wenn der Player aus dem Standby-Status zurückgesetzt wird, anstatt zur vorherigen Position zurückzukehren.

* Zendesk #23412 - Der Player ist mit einem schwarzen Kasten fixiert, wenn Sie durch Anzeigen innerhalb der letzten 3 Sekunden der Werbeunterbrechung klicken
Dieses Problem ist dasselbe wie Zendesk #21200.

* Zendesk #23616 - Übersprungene Werbeunterbrechungen - Suchvorgänge in Zukunft zu weit
Je nach Anzeigeneinfügetyp (Einfügen/Ersetzen) bestimmt TVSDK, ob die Anzeigendauer zur Bestimmung des Endpunkts der Werbeunterbrechung verwendet wird.

* Zendesk #25078 - TVSDK DRM Memory Leak auf Android TV STB
Das Speicherleck für das DRM-Adapterobjekt wurde gefunden und behoben.

* Zendesk #25067 - Absturz in VideoEngineTimeline
Dies geschieht, weil Objekte nicht richtig gereinigt wurden und Ereignisse aufgerufen wurden, nachdem die Objekte zerstört wurden. Das Problem wurde behoben, indem Prüfungen hinzugefügt wurden, um Null-Ausnahmen zu verhindern.

* Zendesk #25352 - Festlegen eines benutzerdefinierten HTTP-Headers
Dieses Problem wurde behoben, indem der Zulassungsliste unter TVSDK ein neuer benutzerdefinierter Header hinzugefügt wurde.

* Zendesk #25617 - Live-Stream-PTS-Rollover, der zu Diskontinuität und Speicherabstürzen führt
Dieses Problem wurde behoben, indem eine PTS-Rollover-Verarbeitung in FragmentedHTTPStreamer hinzugefügt wurde, wenn ein Rollover mitten in einem Segment stattfindet.

**Version 1.4.28 (1637)**

* Zendesk #23618 - Werbeunterbrechungen - Ereignis werden ausgelöst, bevor die Anzeigenrichtlinie konsultiert wird
Dieses Problem wurde behoben, indem die Ereignis AD_BREAK_BEGINN und AD_BEGINN nicht ausgelöst wurden, wenn die Anzeige aufgrund von adForgiity übersprungen wurde. Stattdessen wird das Ereignis AD_BREAK_SKIPPED gesendet.

**Version 1.4.27 (1631)**

* Zendesk #23174 - Leistungsproblem bei der Größenanpassung des Videos
Dieses Problem wurde behoben, indem eine neue API, MediaPlayerView.setSurfaceFixedSize, nachgewiesen wurde, die TVSDK den Zugriff auf SurfaceHolder.setFixedSize() aus MediaPlayerView erlaubt.

* Zendesk #24450 - TVSDK stellt Duplikat-Anzeigenanforderungen her
Dieses Problem trat auf, wenn die abgelaufene Zeit in eine lange und nicht in eine Dublette konvertiert wurde und dieses Problem behoben wurde.

**Version 1.4.26 (1627)**

* Zendesk #21436 - Update der OpenSSL-Bibliothek auf Version 1.0.2h Aktualisierung der OpenSSL-Bibliothek auf OpenSSL-Version 1.0.2h
* Zendesk #23825 - Cookies werden nicht in den Rückrufen enthalten, die durch die Unterstützung von Android-Cookies behoben wurden.

**Version 1.4.25 (1620)**

* Zendesk #22900 - Live-Adobe Primetime DRM-Stream wird nicht auf dem Android-Referenzplayer wiedergegeben
Das Speicherzuordnungsproblem wurde behoben.
* Zendesk #23176 - Anwendung stürzt ab, wenn versucht wird, VPAID-Anzeigen wiederzugeben
Der Absturz trat auf, weil die Anwendung keine benutzerdefinierte Ansicht zur Wiedergabe einer VPAID-Anzeige erstellt. Dieses Problem wurde behoben, indem die VPAID-Anzeigen in der Anzeigenserverantwort ignoriert wurden, wenn keine benutzerdefinierte Ansicht vorhanden ist.

* Zendesk #23153 - SampleAES DRM Stream - Wiedergabe angehalten im TVSDK Reference Player
Dieses Problem ist mit Zendesk #22900 identisch.

**Version 1.4.24 (1612)**

* Zendesk #20784 - Analytics: Auslösen von Inhaltsbeendigungen für Live-Video-Transitionen
Dieses Problem wurde behoben, indem eine API (trackVideoComplete) hinzugefügt wurde, mit der der Abschluss von Inhalten während einer Live-/linearen Videoverfolgungssitzung manuell Trigger werden kann.

* Zendesk #21977 VideoEngineZeitleiste Absturz während des AdBreak/acceptAd-Vorgangs
   * In diesem Problem wurden die folgenden Bibliotheken aktualisiert:
      * AdobeMobile-Bibliothek auf Version 4.10.0
      * VHL-Bibliothek zu Version 1.5.6
      * VHL-Nielsen-Bibliothek zu Version 1.6.7

Dieses Problem wurde behoben, indem eine Null-Prüfung hinzugefügt wurde, bevor der zulässigen Anzeigenwerbung Anzeigen hinzugefügt wurden.

* Zendesk #22313 Die Bitrate für die STBs mit Amilogic Chipsatz überschreitet nicht 1,2M
Dieses Problem wurde behoben, indem die Funktionen des Mediencodecs vorgeladen und der nahtlose Switch für Amilogic-Chipsatzgeräte deaktiviert wurden.

* Zendesk #19520 Beispiel-AES-HLS-Asset nicht in TVSDK-Playern wiedergegeben
Dieses Problem wurde behoben, indem mehrere PMT-Deskriptoren für AES-verschlüsselte HLS-Streams verarbeitet wurden.

**Version 1.4.23 (1602)**

* Zendesk #18852 - Aktualisieren der Logik der kreativen Auswahl basierend auf CRS-Regeln
Dieses Problem wurde behoben, indem eine JSON-Konfigurationsdatei hinzugefügt wurde, um die Priorität für die kreative Auswahl anzugeben.

* Zendesk #20861 - Android N
Diese Version bietet Unterstützung für Android N, da keine direkten nativen Bibliotheken der Android-Plattform mehr verwendet werden können, die für Anwendungen, die unter Android N ausgeführt werden, nicht mehr verfügbar sind.

* Zendesk #21018 - Absturz von Android N
Gleiche Auflösung wie ZD# 20861.

* Zendesk #21266 - VideoEngineAdapter stürzt bei einem Fehler &quot;Invalid_Key&quot;ab
Der Fehler &quot;Invalid_Key&quot;enthält keine Beschreibung von AVE. Daher wurde der Text beim Analysieren in NPE umgewandelt. Das Problem wurde behoben, indem vor dem Analysieren der Beschreibung eine Null-Prüfung für die Beschreibung bei onError hinzugefügt wurde.

* Zendesk #22286 - Die native Bibliothek weist Speicherleseschlüssel/-fragment zu und verursacht Absturz
Dieser Absturz, der bei Android beim Versuch auftrat, ein Manifest mit mehreren Schlüsseln gleichzeitig zu laden, wurde behoben.

**Version 1.4.22 (1581)**

* Zendesk #17236 - Unzuverlässige Abspielzeit für HLS-Videos mit DRM
Der Zeitsprung mit den LBA-Streams, bei dem die Beginn-Zeit des Audiosegments nicht mit der Beginn-Zeit des Videosegments übereinstimmt, wurde korrigiert.

* Zendesk #17680 - Die Videowiedergabe friert im Feld Selevision Andredo ein
Der Video-Decoder auf diesem Gerät gibt manchmal einen signifikanten Ausgabedauer-Sprung zurück, wenn der Videoframe aus dem Ausgabepuffer in die Warteschlange gestellt wird, und dieser Zeitstempel bleibt hoch. Dieses Problem wurde behoben, indem ein *Profil zurückgegeben wurde, das nicht unterstützt wird*, der den Player nicht zwingt, das gleiche Profil erneut auszuführen oder ein anderes Profil auszuwählen.

* Zendesk #19074 - Videosperre während der FFWD- und REW-Trickwiedergabe
Dieses Problem wurde behoben, indem eine neue Warnung TRICKPLAY_ENDED_DUE_TO_ERROR hinzugefügt wurde, um die Anwendung darauf hinzuweisen, dass das Trickplay beendet wurde und dass das Video aufgrund eines nicht behebbaren Fehlers angehalten wurde.

* Zendesk #19574 - TVSDK gibt keine M3U8-Antwortdaten für DRM- oder Nicht-DRM-Inhalte zurück
Dieses Problem wurde wie folgt behoben:

* Zendesk #19986 - OP-Verhalten bei bestimmten Geräten wie Android TV unterbrochen
* Fehler FILE_NOT_FOUND zur Bedingung hinzufügen.
* Wenn der Fehler von einem *Fehler* stammt, der nicht gefunden wird, trennen Sie die URL und die Antwort von der Fehlerbeschreibung, wenn die Antwort verfügbar ist.
Der Logikfehler, der durch die Unterstützung von NVidia Shield OP eingeführt wurde, wurde behoben. Vertrauen Sie auf Nicht-NVidia-Schutzschildern auf sichere Display-Flags, auch wenn der Anzeigetyp unbekannt ist.

* Zendesk #20549 - Umgang mit StallPlaylists. Dieses Problem wurde behoben, indem das Intervall zwischen dem Live-Manifest-Update auf die Hälfte der erwarteten Segmentdauer reduziert wurde, wenn der vorherige Abruf keine neuen Segmente erhält.

* Zendesk #20742 - Die Speicherbelegung scheint bei der Wiedergabe von Live-Inhalten auf FireTV weiter zu steigen. Der Absturz wird durch die JNI-Objektverweistabelle verursacht, die die Grenze erreicht hat. Dieses Problem wurde behoben, indem der Verweis auf das MediaFormat-Objekt gelöscht wurde, das beim Neustart des Decoders erstellt wurde.

* Zendesk #21125 - Rendite aus einer Live-/linearen Werbeunterbrechung früh (CSAI). Es wurde eine Funktion hinzugefügt, die es dem Player ermöglicht, während einer Werbeunterbrechung zum Hauptinhalt zurückzukehren, wenn der Player die Spaltung in Anzeigenzetteln registriert, indem er den Splice im Opportunitätsdetektor verwendet.

* Zendesk #21334 - TVSDK-Anzeigenanforderungszeitlimit für Anzeigen-Anfragen von Drittanbietern. AdvertisingMetadata wurde eine adRequestTimeout-Einstellung hinzugefügt, die einen globalen Timeout für den Anzeigenaufruf ermöglicht.

**Version 1.4.21 (1566)**

* Zendesk #17781 - ADB-Screenshot funktioniert nicht mehr
Dieses Problem wurde behoben, indem die API DefaultMediaPlayer.create(Context context, boolean secureSurface) hinzugefügt wurde, die die Bildschirmerfassung ermöglicht.
Übergeben Sie false für secureSurface, um Screenshots zuzulassen.
Wichtig: Es wird dringend empfohlen, diese Bildschirmaufzeichnungsfunktion in einer Produktionseinstellung nicht zu aktivieren.

* Zendesk #19074 - Videosperre während der FFWD- und REW-Trickwiedergabe
Die folgenden Probleme, die auftraten, wenn die trickPlay-Funktion in der Play-back-Funktion eingefroren werden konnte, wurden behoben:

* Zendesk #19532 - &quot;Beschriftung schließen&quot;wird nicht in der richtigen Reihenfolge angezeigt
   * FHS-Beginn trickplay, aber das erste iframe-Segment enthielt keinen Rahmen.
   * Wenn FHS beim Herunterladen eines iframe-Segments eine Fehlerbedingung trifft, wird das trickplay beendet und die Wiedergabe angehalten.
   * Die Andorid MediaCodec-Implementierung wartet ewig auf die Verfügbarkeit der Eingabeschlange, während sie aufgefordert wurde, alle Eingabe-/Ausgabepuffer zu leeren.
Dieses Problem wurde behoben, indem die Reihenfolge der WebVTT-Hinweise umgekehrt wurde, sodass mehrere sich überschneidende Hinweise als &quot;Bildlauf nach oben&quot;angezeigt werden.

* Zendesk #19574 - Das TVSDK gibt keine M3U8-Antwortdaten für DRM- oder Nicht-DRM-Inhalte zurück
Beim anfänglichen Laden der Manifestdatei in PTMediaPlayerItem.prepareToPlay meldet das TVSDK nicht den Hauptteil der Fehlerantwort auf die Anwendung, wenn der Ladevorgang fehlschlägt.
Dieses Problem wurde behoben, indem TVSDK die Fehlerantwort als Fehler an die Anwendung melden konnte.

* Zendesk #19701 - Einfrieren der Wiedergabe mit SAP/Diskontinuität
Der Player friert ein, wenn Audio und Video bei Diskontinuität nicht ausgerichtet sind.

* Fehler #PTPLAY-11162 - Das Update der OpenSSL-Bibliothek auf Version 1.0.2f wurde behoben.

**Version 1.4.20 (1546)**

* Zendesk #17384 - Funktionsanforderung: Unterstützung von ID3-Metadaten für AAC-Wiedergabe
Unterstützung für ID3-Tags in AAC-Medien wurde ab Version 1.4.20 im TVSDK für Android bereitgestellt.

* Zendesk #18358 - Player stürzt beim Bitratenwechsel ein, ohne dass die Synchronisierung unterbrochen wird
Dieses Problem wurde behoben, indem die ABR-Stickereifälle ordnungsgemäß behandelt wurden.

* Zendesk #19232 - App, die TVSDK 1.4.18 verwendet, verhält sich merkwürdig mit älteren Amazon OS-Versionen 4
Dieses Problem wurde behoben, indem die Erstellung verborgener Web-Ansichten im TVSDK-Player-Initialisierungsprozess entfernt wurde, um Konflikte mit Geräten zu vermeiden, die Android WebView nicht unterstützen.

* Zendesk #19585 - Wiedergabe mit langsamer Bewegung, wenn eine Transition der adaptiven Bitrate erfolgt.
Wenn das neue Profil während des ABR-Switches eine andere Audio-Samplerate hat als das aktuelle Profil, wird die Wiedergabe schnell oder langsam. Der Grund dafür ist, dass der Videopräsentator nicht darüber informiert wird, dass sich das Audioformat geändert hat.
Dieses Problem wurde behoben, indem sichergestellt wurde, dass das Benachrichtigen-Flag an der richtigen Stelle gesetzt wurde.

* Zendesk #19683 - SAP DAI-Wiedergabe - Kein Audio für wenige Sekunden.
In mehreren Fällen in der Logik des TVSDK wurde RENDITION_TIMEOUT_THRESHOLD beim Vergleich des Zeitstempels zweier Darstellungssegmente als akzeptabler Wertebereich verwendet, da der Zeitstempel nicht immer mit einem Unterschied von 0 ms abgeglichen werden kann. Wenn die Lücke im Bereich von RENDITION_TIMEOUT_THRESHOLD liegt, wird davon ausgegangen, dass es sich um eine Übereinstimmung handelt.

Die RENDITION_TIMEOUT_THRESHOLD wurde auf 100 ms eingestellt, stellte aber fest, dass sie für bestimmte Streams nicht ausreicht. Dieses Problem wurde behoben, indem die Variable RENDITION_TIMEOUT_THRESHOLD auf 200 ms erhöht wurde.

* Zendesk #19699 - Das TVSDK kann nicht zwischen VTT-Untertitelspuren wechseln
Dieses Problem wurde behoben, indem der Player beim Ändern einer Verfolgung abgeblättert und das Manifest neu geladen wurde und das UTF8-Zeichenfolgenkonvertierungsproblem korrigiert wurde, das die Verfolgungsnamen der Dublette-Byte-WebVTT-Beschriftung beeinflusste.

* Zendesk #19717 - Problem mit der Anzeige der CC-Optionen
Dieses Problem wurde behoben, indem die Unicode-Zeichenfolge ordnungsgemäß verarbeitet wurde.

* Zendesk #19910 - TIT2 ID3-Tags werden nicht erkannt
Dieses Problem wurde behoben, indem umfassendere Unterstützung für ID3 v2.4-Zeichenfolgenkodierungen und Unterstützung für ID3 v2.3 bereitgestellt wurde.

* Zendesk #20135 - Das TVSDK löst mehrere onComplete-Vorgänge für VOD-Inhalte aus.
Dieses Problem wurde behoben, indem der Ereignis-Listener post_roll_compelete an der richtigen Stelle hinzugefügt wurde und nicht im vollständigen Ereignis der Statusänderung.

**Version 1.4.19 (1521)**

* Zendesk #4180 - Das TVSDK erzwingt HDCP nicht.
   * Dies ist eine teilweise Korrektur für dieses Ticket und behandelt nur das Problem für NVidia-Schutzeinrichtungen.
Sie müssen die korrekt implementierte HDCP-Erkennungs-API im Nvidia Shield verwenden, um den HDCP-Status dynamisch zu verfolgen.

* Zendesk #18358 - Das TVSDK friert beim Bitratenwechsel ein, ohne dass die Synchronisierung beendet wird.
   * Dieses Problem wurde behoben, indem eine neue Warnung hinzugefügt wurde, um die PTS-Diskontinuität zu erkennen, und die PTS-Prüfung gezwungen wurde, das richtige Segment für jeden ABR-Switch erneut zu suchen.
Um das Einfrieren zu beheben, sollte der Aufruf der Methode mediaPlayer.setCustomConfiguration forcePTSCheckForABR als Argument enthalten.

* Zendesk #19038 - Kein Live-Stream auf Asus Zenpad 10.

   Dieses Problem wurde behoben, indem die Informationen zum Mediencodec im Voraus geladen wurden, sodass Sie die Funktion zur Laufzeit nicht Abfrage haben.

* Die folgenden Probleme sind mit Zendesk #19038 identisch:
   * Zendesk #19483 - Das TVSDK stürzt auf der Intel Plattform ab.
   * Zendesk #19171 - Absturz auf Asus Memo Pad 7 mit Android 5.0.

**Version 1.4.18 (1503)**

* Zendesk #3324 - Der Berichte Primetime-Anzeigen verfolgt keine Werbeunterbrechungen, wenn in einem VMAP keine Anzeigenmedien vorhanden sind.
Wenn eine Werbeunterbrechung leer ist, wurden der Beginn der Werbeunterbrechung und die Ereignis der vollständigen Verfolgung nicht gepingt. Dieses Problem wurde behoben, indem Werbeunterbrechungen für Beginn-Pings für leere Werbeunterbrechungen, wie z. B. VMAP AdBreak, mit einem gültigen AdSource-Knoten gesendet wurden.

* Zendesk #18229 - SetCCVisiblity(VISIBLE) wird nach dem MediaPlayer.reset()-Aufruf ignoriert
Dieses Problem wurde durch Hinzufügen von setCCVisibility(Visibility.INVISIBLE) behoben. zur Funktion reset() in der MediaPlayer-Klasse.

* Zendesk #18328 - Problem mit Dropped Frames auf Amazon Fire TV 2nd Generation-Geräten für Inhalte mit 60FPS
Dieses Problem wurde behoben, indem die kodierten FPS für die Entscheidungsfindung über die Ruhezeit und eine besser kodierte FPS-Prognoselogik angewendet wurden.

**Version 1.4.17 (1472)**

* Zendesk #2231 - Fehler beim Abrufen des in MediaPlayerNotification nicht verfügbaren Manifests zurückgegeben
Dieses Problem wurde behoben, indem der Antworttext des Manifests einbezogen wurde, wenn ein Parse-Fehler auftrat.

* Zendesk #17703 - VideoEngineView verhindert keine Screenshots während der Videowiedergabe
Die Methode setSecure ist seit API 17 verfügbar. Da jedoch API 17 4.2, 4.2.1 und 4.2.2 umfasst, ist nicht bekannt, welcher eine Ausnahme auslöst oder ob es gerätespezifisch ist. Dieses Problem wurde behoben, indem VideoEngineView.setSecure in die try catch-Klausel aufgenommen wurde.

* Zendesk #17919 - Inhaltssuche verursacht Heartbeat-Fehler
Als Ergebnis des Heartbeat-Aufrufs, der beim Starten der Suche nach dem Pre-Roll generiert wurde, ist ein Fehler bezüglich der Position der Eingabedaten aufgetreten. Dieses Problem wurde behoben.

**1.4.16a** (1454a)

* Zendesk #18215 - Einige AES-Streams können nicht geladen werden.
Dieses Problem wurde behoben, indem die Größe der DRM-Metadaten des Profils überprüft wurde, bevor der AES-Schlüssel geladen wurde.

**Version 1.4.16 (1454)**

* Zendesk #3875 - Tabulator-S stürzt während der Wiedergabe ab
Rückgängigmachen der Abhängigkeit von OKHTTP auf Auditude für CRS, da TVSDK jetzt direkt HTTPLILLconnection statt curl verwendet. Das Problem wurde behoben, indem Ausnahmen gelöscht wurden, bevor ein anderer JNI-Aufruf erfolgte.

* Zendesk #4487 - Tracking Linear Kanal of Content
Das Problem wurde behoben, indem die erneute Initialisierung des Video Heartbeat-Trackers während einer linearen Stream-Wiedergabesitzung ermöglicht wurde.

* Zendesk #17919 - Android - Inhaltssuche verursacht Heartbeat-Fehler
Das Problem, bei dem der Heartbeat-Status in einem Fehlerzustand ist, wenn ein Kapitel eine Suche enthält, wurde behoben.

* Zendesk #18053 - Adobe Primetime stürzt auf Marshmallow ab
Das TVSDK stürzte unter Android M OS ab, wenn die TVSDK-Bibliothek Neoncode verwendet, der die YUV -> RGB-Farbkonvertierung durchführt. Das Problem wurde behoben, indem die Funktionen aktualisiert wurden, die dieses Problem verursachen, indem die Nicht-Neon-Version des Codes verwendet wurde.

* Zendesk #18072 - Android M - Anwendungsabsturz
Beim Prüfen, ob Profil und Ebene unterstützt werden, kommt es zu einem Absturz, wenn MediaCodecList- und MediaCodecInfo-APIs aufgerufen werden. Das Problem wurde behoben, indem eine temporäre Bearbeitung bereitgestellt wurde, indem alle Codec-Informationen frühzeitig geladen wurden, um zu vermeiden, dass diese APIs nur dann aufgerufen werden, wenn Codec-Informationen benötigt werden.

* Zendesk #18074 - Arabische Untertitel, die nicht auf Nexus mit Android 6.0 funktionieren
Das Problem wurde behoben, indem CTS-Schriftartzuordnung für Android unterstützt wurde.

**Aktualisierung auf Version 1.4.15 (1438)**

* Zendesk #17437 - Lange Verzögerung beim Start von VOD-Inhalten mit einigen AES-Streams.
Um dieses Problem zu beheben, laden Sie bei mehreren im Manifest aufgeführten Schlüsseln alle AES-Schlüssel parallel herunter.

**Version 1.4.15 (1435)**

* Zendesk #4278 - Glitches auf Android legen die oberen Boxen fest, wenn sich die adaptive Bitrate ändert (ABR).
Die Korrektur wurde vorgenommen, um Unterstützung für nahtlose ABR-Switches mit dem neuesten Android-Mediencodec hinzuzufügen.

* Zendesk #17063 - Der Aufruf von mediaPlayer.reset() verursacht einen Fehler beim Zurücksetzen der Videomaschine.
Die Korrektur sollte den ursprünglichen MediaErrorCode aus VideoEngineExceptions beim Auslösen von ErrorEvents enthalten.

* Zendesk #17130 - Eine kurze, aber bemerkenswerte Pause beim Ändern der Bitrate auf FireTV.
(Wie unter #4278 oben) Das Problem bestand darin, Unterstützung für nahtlose ABR-Switches mit dem neuesten Android-Mediencodec hinzuzufügen.

* Zendesk #17666 - Zusätzliche Anzeigenmarken, Unerwartete oder Keine Anzeigen beim Fortsetzen von Inhalten.
Die Korrektur war ein Problem, bei dem prepareToPlay bei VOD-Inhalten (Video-on-Demand) ausgeführt wurde. Die erste Suche wird statt der virtuellen Zeit für die lokale Zeit ausgeführt.

* Zendesk #17437 - Lange Verzögerung beim Start von VOD-Inhalten mit einigen AES-Streams.
Die Korrektur bestand darin, alle AES-Schlüssel parallel herunterzuladen, wenn mehrere Schlüssel im Manifest aufgelistet sind.

* Zendesk #17851 - Android TV - Schwarzer Rahmen während ABR
Die Korrektur bestand darin, KEY_MAX_WIDTH und KEY_MAX_HEIGHT anzugeben, um die adaptive Wiedergabe zu aktivieren.

**Version 1.4.14 (1415)**

* Zendesk #3875 - Tabulator-S stürzt während der Wiedergabe ab.
Um den Absturz zu verhindern, war eine zusätzliche Fehlerbehebung erforderlich.

* Zendesk #17245 - Fallback auf Android TV funktioniert nicht.
Es wurde ein zusätzlicher Fehler behoben, bei dem die Wiedergabe hängt, wenn die Ausweichmöglichkeit aktiviert ist, und die VMAP-Antwort einen leeren Werbeunterbrechung aufweist.

**Version 1.4.14 (1412)**

* Zendesk #17245 - Fallback auf Android TV funktioniert nicht.
Eine Beschränkung für die Deaktivierung der kreativen Neuverpackung von Fallback-Anzeigen wurde entfernt.

**Version 1.4.13 (1388)**

* Zendesk #3502 - HLS Client-basierte Failover-Unterstützung während einer Werbeunterbrechung
Lassen Sie Failover auf das Hauptmanifest zu, wenn das Aktualisieren des Live-Profils während der Werbeunterbrechungszeit auftritt.

* Zendesk #3875 - Tabulator-S stürzt während der Wiedergabe ab
Um den Konflikt zwischen HttpUrlConnection und cURLm zu lösen, verwenden Sie eine Bibliothek eines Drittanbieters.

* Zendesk #4450 - Problem beim Festlegen benutzerdefinierter Metadaten für eine einzelne Platzierung in einem Inhaltsauflöser
hinzufügen Sie einen Setter zu den Opportunity-Einstellungen.

**Version 1.4.12 (1388)**

* Zendesk #2751 - CSAI und CRS | Verbesserung: Verarbeiten Sie dynamische Elemente in bestimmten Mediendatei-URLs.
Der Dienst für kreative Umverpackungen wurde aktualisiert, um Anzeigen mit dynamischen kreativen URLs korrekt zu bearbeiten.

* Zendesk #3965 - Beim Zurückschalten von der Trickplay-Wiedergabe auf die normale Wiedergabe erfolgt ein Sprung nach vorne, bevor die Wiedergabe gestartet wird.
   * Die Fehlerbehebung beinhaltet, dass TVSDK die Zeit zurückgibt, bevor die Rate geändert wird, bis alle Variablen aktualisiert wurden, anstatt die GetStreamTime zu berechnen.
   * Es wurde ein Absturz behoben, der beim Ändern der Abspielgeschwindigkeit des Tricks am Ende des Streams auftrat.
   * Korrektur der Berechnung der aktuellen Zeit während der Trick-Wiedergabe.

* Zendesk #3978 - Trickplay bei 8x und 16x wird häufig gefriert.
   * Wählen Sie immer das Trick Play Profil mit der niedrigsten Bitrate, um eine konstante Pufferung zu vermeiden.
   * Erhöhen Sie das Intervall für das Überspringen des Rahmens für eine hohe Trick-Abspielrate.
   * Behebung eines Fehlers, bei dem der Puffer nach Erreichen der Zielgruppe während der Trick-Wiedergabe weiter wächst.

* Zendesk #3992 - Zusätzliche Trickplay-Geschwindigkeiten.
TrickPlay wurde aktualisiert, um Raten über 16x zu akzeptieren. +/- 32, +/-64 und +/-128 sind jetzt auch zulässig.

* Zendesk #4007 - Interpretieren des GEOB-Objekts als Teil der Zeitschienenmetadaten (Android &amp; Web).
setByteArray- und getByteArray-API hinzugefügt.

* PTPLAY-7301 - Sofort auf Beginn am Zufälligen Zugriffspunkt.
&quot;Sofort ein&quot;wurde aktualisiert, um einen Startpunkt ungleich null zuzulassen.

**Version 1.4.11 (1363)**

* Zendesk #2076 - Häufiger Stotter beim Abspielen von Videos auf Motorola Xoom mit Android 4.0.3
Es wurden Geräte zur Zulassungsliste hinzugefügt, um zu verhindern, dass sie versuchen, Inhalte mit hohem Profil wiederzugeben.

* Zendesk #2197 - `[Ads]` Trackinganzeigefehler
Dispatch OperationFailedEvent mit Warnmeldung.

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` Makro nicht gefüllt
   * Fehlercode 400 wird angezeigt, wenn Inline-Anzeige ein falsches kreatives Element enthält.
   * `[ERRORCODE]` Makro wird URL-kodiert

**Version 1.4.10 (1354)**

* Zendesk #2941 - Live-Assets haben nicht &quot;0&quot;im suchbaren Bereich
Zuvor gab es bei der Suche nach dem Anfang eines Live-Streams einen 3-Segmentpuffer, jetzt ist es möglich, bis zum Anfang eines Live-Streams zu suchen (d. h. den Beginn des ersten Segments).

* Zendesk #3169 - Update Reference Player with Adobe Analytics integration Der Referenz-Player wurde mit der Adobe Analytics-Bibliothek als Beispiel für Implantation aktualisiert.
* Zendesk #3299 - Unerklärliches Verhalten bei Tricks
   * Es wurde ein Fehler behoben, durch den die Rückkehr zum Wiedergabestatus nach dem Beenden der Trick-Wiedergabe mehrere Sekunden dauern konnte (manchmal 25+ Sekunden).
   * Es wurde ein Fehler behoben, durch den beim Aufrufen von trick play ein zweites Mal auf demselben Medium der Stream zum aktuellen Zeitpunkt eingefroren werden konnte.
* Zendesk #3433 - Android und Flash - Probleme mit Untertiteln

GetLine für WebVTT hielt eine &lt;CR>&lt;LF> angepasste Länge für ein Paket nicht ein; Die letzte Beschriftung könnte Zeichen aus vorherigen Beschriftungen enthalten.

* PTPLAY-6243 - Erweiterter Referenz-Player zum Erfassen von Debugging-Informationen

Die Android-Beispiel-Referenzplayer wurden um eine Option erweitert, um Debug-Protokolle zu aktivieren und die Ergebnisse per E-Mail zu versenden. Diese Option befindet sich im Referenzplayer im Menü Protokoll.

**Version 1.4.9 (1332)**

* Zendesk #2649 - Puffer Complete wird ausgeführt, bevor der ursprüngliche Puffer voll ist

Nach einer Suche ist dies der Fall, bei dem die Video-Engine den Status &quot;PLAYING&quot;festlegt, bevor der Video-Moderator zur Wiedergabe bereit ist. Tritt auf, wenn der Pufferstatus vor der Suche hoch ist. Korrektur durch Benachrichtigung der Video-Engine über niedrigen Pufferstatus. Bei einem niedrigen Pufferstatus der Video-Engine bewirkt der Aufruf von &quot;Abspielen&quot;eine Statusänderung zu &quot;BUFFERING&quot;anstelle von &quot;PLAYING&quot;. Die Wiedergabe wird fortgesetzt, wenn der Status auf PLAYING geändert wird.

* Zendesk #2846 - Erweiterungsanfrage: Bieten Sie die Möglichkeit, für Aufrufe der Auditude-Bibliothek eine andere Benutzeragenten-Zeichenfolge festzulegen.

Es wurde eine neue API hinzugefügt, mit der der Benutzeragent für werbebezogene Aufrufe, auditudeSettings.setUserAgent(&quot;user/agent&quot;), festgelegt wird. Wenn kein Benutzeragent festgelegt ist, wird die Standardeinstellung verwendet. Dies betrifft nur den Benutzeragenten für werbebezogene Aufrufe. Der Benutzeragent für Medienaufrufe bleibt unverändert und lautet &quot;Adobe Primetime&quot;+.

**Version 1.4.8 (1324)**

* Zendesk #1218 - 106000.33 Fehler mit lokalem ... Wenn das Laden des Manifests in FragmentedHTTPStreamer::ThreadParseManifest() fehlschlägt, überprüfen Sie, ob die URL-Domäne localhost ist. Ändern Sie in diesem Fall die Domäne auf 127.0.0.1 und rufen Sie ThreadParseManifest auf.
* Zendesk #3072 - Automatischer Wechsel zu niedrigeren Bitraten. Die Berechnung der Pufferlänge wurde geändert, um die PTS-Nutzlast auf Null zu überspringen.
* Zendesk #3168 - WebVTT-Untertitel werden nur für die ersten 10 Sekunden angezeigt.
* Zendesk #3193 - Request for a Profil change API in TVSDK, PlaybackEventListener.onProfileChanged() wurde hinzugefügt.

**Version 1.4.7 (1311)**

* Zendesk #2197 - Verfolgung von Anzeigenfehlern. Benachrichtigung hinzugefügt, dass das Manifest für Assets nicht geladen wurde
* Zendesk #2575 - PSDK ignoriert benutzerdefinierte MARK-In-Stream-Anzeige vor dem Video
* Zendesk #2719 - Win Death mit Auditude-Anzeigen, feste Beacon-Verfolgung bei Umleitung zu relativer URL im auditude-Plugin
* Zendesk #2760 - DISCONTINUITY-Tag während des TrickPlay-Modus ignoriert
* Zendesk #2805 - Absturz des Players zu Beginn der Wiedergabe, dieselbe Fehlerbehebung wie Zendesk #2719
* Zendesk #2817 - Android-Player - Der Player hängt manchmal und stoppt die Wiedergabe, korrigiert durch Verlängerung der Dekodierungspuffer von 2,0 auf 3,0 Sekunden
* Zendesk #2839 - Unterstützt Adobe Primetime PSDK ARMv8 Chipsätze?, wurde eine Fehlerbehebung für Abstürze auf Galaxy S6 hinzugefügt.
* Zendesk #2885 - Wiedergabe von Auditude-Abstürzen, dieselbe Fehlerbehebung wie Zendesk #2719
* Zendesk #2895 - Live-HLS-Fehler nach 10 Minuten Wiedergabe
* Zendesk #2925 - Feedback zum Android-Dev-Build (1.4.5), auf bestimmten Geräten, wenn wir das Paket in die Eingangskwarteschlange stellen, wenn das PTS negativ ist, wird der Decoder in einen seltsamen Zustand versetzt, dass wir immer eine negative Ausgabe PTS für zukünftige Pakete erhalten. Die Korrektur setzt die Eingabe PTS auf null, wenn es negativ ist, um dieses Problem zu vermeiden.
* PTPLAY-4645 - Deaktivieren Sie die RC4-Unterstützung in openssl. Es gibt bekannte Exploits für RC4. Wenn also versucht wird, eine Verbindung mit einem Server herzustellen, der nur RC4 unterstützt, schlägt dies fehl.

**Version 1.4.6 (1282)**

* Zendesk #2192 - Bitrate senkt nicht immer unter schlechten Netzwerkbedingungen, korrigiert durch Entfernen der schnellen Switch-Implementierung.
* Zendesk #2631 - Arabische Untertitel unter Android: Text in mehreren Zeilen wird abgeschnitten angezeigt, wobei die Schriftgröße für arabische Schriften angepasst wird.
* Zendesk #2844 - Pufferung auf Hinweis 4 und Downloadzeit für Fragmente ist nicht korrekt.

Dieses Problem wurde behoben, indem Latenzzeiten zwischen Videosegmentdownloads zur Bandbreitenberechnung hinzugefügt wurden und die Logik zur Berechnung der Downloadzeit die volle Anforderungszykluszeit verwendet.

* Zendesk #2908 - Arabische Untertitel, die nicht auf Nexust 5, 6 und 7 funktionieren, wurden korrigiert, indem 2 weitere Fallback-Schriftarten für arabische Skripten hinzugefügt wurden.
* PTPLAY-4627 - Nielson-Apps auf Version 1.2.3.7 aktualisieren
* PTPLAY-5084 - Unterstützung für Live Übergeordnet Manifest-Update-Failover

**Version 1.4.5 (1248)**

* Zendesk #1757 - Nur abgespielter oder Player stürzt bei einigen Video-Bitrate-Profilen ab, Nexus 4 und Nexus 7 stürzten ab
* Zendesk #2072 - TimedMetadata for AdEvent enthält nicht die vollständige URL nur &quot;http&quot;
* Zendesk #2192 - Bitrate ist unter schlechten Netzwerkbedingungen nicht immer niedriger
* Zendesk #2256 - Zugriff auf Übergeordnet Playlist, aktualisiertes PSDK zum Versenden von timedMetadata-Ereignissen für abonnierte Tags in der Übergeordnet Playlist.
* Zendesk #2269 - Zwei verschiedene Untertitelsprachen werden gleichzeitig mit WebVTT auf dem Bildschirm angezeigt
* Zendesk #2417 - Player, der versucht, Untertitel vor dem Beginn der Wiedergabe herunterzuladen, verwendete WebVTT die falsche Segmentnummernvariable für die Segmentnummerübereinstimmung. Fehler werden nur für Medien angezeigt, deren Segmentindizes bei Null beginnen.
* Zendesk #2470 - PSDK kehrt nicht aus dem Status AUSGESETZT zurück, wenn eine Bitratenänderung nach der Aussetzung erfolgt. In einer besonderen Situation, in der die intelligente Suche von RestoreGPUResource (Wiederherstellung des Players vom Aussetzzustand) aufgerufen und der Stream-Switch erkannt wird, bevor dies erfolgt, kann die intelligente Suche nicht abgeschlossen werden und führt zu einer konstanten Pufferung.
* Zendesk #2451 - Untertitel &quot;bottom inset&quot;, Parameter &quot;bottomInset&quot;zum Untertitelcode hinzugefügt
* Zendesk #2480 - Deaktivieren der HTTP 302-Umleitungsoptimierung, Unterstützung für Einstellung der useRedirectUrl-Eigenschaft hinzugefügt
* Zendesk #2486 - Beacons von Drittanbietern
* Zendesk #2547 - Arabische Untertitel: Text sollte rechtsbündig ausgerichtet werden

**Version 1.4.4 (1195)**

* Zendesk #1158 - Wiedergabe bei Huawei Valiant fehlgeschlagen (Y301A1)
* Zendesk #1709 - Falsche Mediengröße und gestrecktes Video
* Zendesk #1757 - Nur Audio, das nach dem Wechsel zwischen Streams mit identischen SPA/pps-Daten wiedergegeben wird
* Zendesk #2095 - HTTP-307-Status (Umleitung) bewirkt, dass der Adobe-Player die Wiedergabe stoppt
* Zendesk #2126 - Fehlendes TimedMetaData-Ereignis für letzten ADEVENT, abonnierte Tags, die nach dem letzten Segment existierten, wurden nicht von AVE an PSDK gemeldet
* Zendesk #2227 - Lockups in VideoEngine nativeReset und nativePause
* Fehler #3921755 - OpenSSL-Bibliotheksaktualisierung auf Version 1.0.1L

**Version 1.4.3 (1173)**

* Zendesk #1591 - RENDITION_M3U8_ERROR
* Zendesk #1870 - Geschlossene Beschriftung aktivieren und deaktivieren
* PTPLAY-1818 - Die Wiedergabe der Rückspur-Trick-Wiedergabe wird an der Anzeige beendet, anstatt über sie zurückzukehren
* PTPLAY-2736 - Eine zuvor angezeigte WebVTT-Beschriftung wird auf dem Bildschirm angezeigt, wenn die Wiedergabe eines Streams mit WebVTT-Beschriftung abgeschlossen ist
* PTPLAY-3773 - Eine Mid-Roll-Anzeige wird nicht wiedergegeben, wenn die Stream-Wiedergabe nach der Anzeigenposition gestartet wird

**Version 1.4.2**

* Zendesk #1561 - clientbasierte Failover-Unterstützung in der Zeit. Verwendet die Programm-Datumseingangszeit, um Failover zu beheben
* Zendesk #1590 - LoadInfo.MediaDuration is always 0 (not fixed for audio-only)
* Zendesk #1626 - Potenzieller Speicherleck im Player. Kein aktueller Speicherleck, Problem mit NotificationHistory, das die letzten 1000 Benachrichtigungen speichert, wurde auf 100 reduziert.
* Zendesk #2192 - Bitrate ist unter schlechten Netzwerkbedingungen nicht immer niedriger

**Version 1.4.1 (1121)**

* Zendesk #1951 - Lockup in VideoEngine.nativeReset() auf 4.0.x-Geräten
* Zendesk #2064 - Nativer Absturz SIGSEGV auf bestimmten intel-basierten Android-Geräten
* Zendesk #2075 - Lockup in VideoEngine.nativeReleaseGPUResource auf 4.0.x-Geräten
Hinweis: Dieser Build ist ***erforderlich*** für die Unterstützung von Android 5.0 (Lollipop)
* Zendesk #1513 - Unterstützung für Android Lollipop
* Zendesk #1709 - Falsche Mediengröße und gestrecktes Video
* Zendesk #1871 - WebVTT-Untertitel verschwinden gelegentlich und werden dann bei der Anzeige eines Lebenszyklus mit WebVTT-Untertiteln wieder angezeigt
* Zendesk #1996 - In PSDK 1.4.0 werden keine Zeitschienen angezeigt
* Zendesk #2046 - Absturz mit PSDK 1.4.1.1113, Absturz bei Live-Streams behoben, wenn keine Anzeigen von auditude zurückgegeben werden
* Fehler #3769657 - Aktualisierung der Version von curl auf 7.38.0
* PTPLAY-1575 - Wenn ABR-Wiedergabe-Beginn mit nur Audio-Stream und dann zu Audio-/Videostream wechseln, wird das Video nie gerendert, solange die Audiowiedergabe fortgesetzt wird
* PTPLAY-2499 - Aktualisierung auf OpenSSL auf Version 1.0.1j, um aktuelle Sicherheitslücken zu beheben
* PTPLAY-2632 - Video wird nach Abschluss der Midroll-Anzeige unter Android Lollipop nicht wiederhergestellt
* PTPLAY-2678 - Anhalten von Videos während Live-Tests auf Android Lollipop

**Version 1.4.0**

* Zendesk #1024 - Funktion zum Entfernen von Anzeigen aus dem Stream über Manifest
* Zendesk #1293 - Problem mit der Auswahl des Untertitelspuren.
* Zendesk #1590 - LoadInfo.MediaDuration ist immer 0, mediaDuration zeigt jetzt den richtigen Wert an.
* Zendesk #1629 - Player/App stürzt am Ende der Anzeigenwiedergabe auf Galaxy S4 ab
* Zendesk #1674 - ClosedCaption Nicht angezeigt, korrekte 708-Beschriftungsanzeige, wenn 0 x 03 ETX-Codes fehlen.
* PTPLAY-2157 - Standard-Untertitelstile wurden von Gettern zurückgegeben, selbst wenn nach dem Festlegen und visuellen Überprüfen eines anderen Stils im Stream. Die Stileigenschaften für Untertitel zeigen jetzt den Wert an, auf den sie eingestellt wurden.

## Bekannte Probleme in 1.4 {#known-issues-in}

**Version 1.4.31**

* PTPLAY-16803 - Geschlossene Beschriftung funktioniert nicht mit reinem Audioinhalt, da das Beschriftungssystem Video benötigt, um zu funktionieren. Ohne Video gibt es keine Viewport-Dimension und ohne Viewport-Dimension können keine Grafiken für Beschriftungen angezeigt werden.
* PTPLAY-1634 - Das gleiche abonnierte Tag hat in verschiedenen Live-Fenstern unterschiedliche Zeitstempel. Wenn ein Live-Fenster verschoben wird, sollte dasselbe Tag in ihnen dieselben Zeitstempel haben. Manchmal haben jedoch auch dieselben Tags unterschiedliche Zeitstempel.
* PTPLAY-3197 - Absturz mit Signal-11-SIGSEGV-Fehler auf Acer Iconia-Gerät nach ~ 1 Stunde kontinuierlicher Wiedergabe
* PTPLAY-3310 - Bei geringerer Bitrate wird das Audio bei Acer Iconia choppy/stuttery
* PTPLAY-3355 - WIN-TOD-Absturz auf Motorola Xoom mit 4.0.x nach ~ 1 Stunde kontinuierlicher Wiedergabe.
* PTPLAY-3557 - Das Zurückspulen bei einer Werbeunterbrechung führt zur Fertigstellung des Streams
* PTPLAY-7079 - Das Wiedergabefenster auf dem Android-Client funktioniert nicht mit Secure Stopp/Hard Stopp
* Fehler #3760144 - Die Auflösung kann sich verschieben oder zu pulsieren scheinen, wenn der Stream auf einigen Geräten wie Kindle Fire 7 und Samsung Galaxy Nexus angehalten wird. Nur bei sorgfältiger Prüfung sichtbar
* Fehler #3761170 - searchToLocal in Live with Ads cannot search into ad content, its best to use the currentTime APIs for Live streams
* Fehler #3763370 - Live-Streams mit Anzeigen zeigen gelegentlich zwei Anzeigenmarken nahe beieinander, wenn nur eine vorhanden sein sollte. Diese Anzeigenmarkierungen stellen dieselbe Anzeige dar und nur eine wird wiedergegeben
* Fehler 3763373 - Die Anzeigenmarke wird möglicherweise kurz ausgeblendet, wenn eine Anzeige in VOD-Streams gefunden wird. Die Anzeigenmarke wird wiederhergestellt und es gibt keine anderen negativen Auswirkungen auf die Zeitschiene
* Bei einigen Geräten treten bekannte Wiedergabeprobleme auf. Siehe [Bekannte Geräteprobleme in 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Referenzimplementierung - Trick play wird in der Beispielanwendung nicht implementiert
* Auf einigen Android-TV-Geräten wird ein schwarzer Frame angezeigt, da der Decoder an folgenden Transitionen zurückgesetzt wird:
   * In- und Out-Trickplay-Modus
   * Wechseln zwischen spät bindenden Audiospuren
   * von einer Anzeige zum Hauptinhalt.

**Version 1.4.23**

* &quot;Untertitel&quot;funktioniert nicht mit reinen Audioinhalten, da das Untertitelsystem nur mit Videos arbeiten kann. Ohne Video gibt es keine Viewport-Dimension und ohne Viewport-Dimension können keine Grafiken für Beschriftungen angezeigt werden.
* Ab Version 1.4.23 wird das TVSDK Gingerbread OS 2.3 nicht mehr unterstützen. Dies liegt daran, dass das TVSDK die folgenden privaten Android-Bibliotheken verwendet hat, um Hardwareinformationen über Geräte mit Gingerbread OS zu erfassen:

   * `libstagefright.so`
   * `libcutils.so`

In der Android N-Version hat Google den Zugriff auf diese privaten Bibliotheken entfernt. Das Gingerbread OS macht derzeit weltweit weniger als 1 % des Android OS-Marktanteils aus, sodass nach Version 1.4.23 das Gingerbread OS nicht mehr vom TVSDK unterstützt wird.
Wenn Sie Version 1.4.23 (einschließlich Unterstützung für Android N) oder höher verwenden:
* Aktualisieren Sie Ihre Apps, um die Version 11 von minSdk zu verwenden.
* Wenn Ihr Endbenutzer OS 2.3 ausführt, ist die SDK-Version niedriger als die minSdkVersion der Anwendung. Das System bricht die Installation oder Aktualisierung der Anwendung ab.
* Wenn der Endbenutzer eine Version ausführt, die höher als OS 2.3 ist, wird die Anwendung korrekt installiert.

Wenn Sie die minSdkVersion aktualisieren:

* Wenn Ihr Endbenutzer OS 2.3 ausführt, wird die Anwendung installiert, die Wiedergabe funktioniert jedoch nicht.
Dies gilt sowohl für Updates als auch für Neuinstallationen.
* Wenn der Endbenutzer ein System über OS 2.3 ausführt, wird die App korrekt installiert und der Inhalt wird korrekt wiedergegeben.

**Version 1.4.22**

* Der frühe Ausstieg aus Anzeigen funktioniert bei einigen der Mid-Roll-Anzeigen nicht, wenn Splice-out- und Splice-in-Tag zu nahe beieinander liegen.

**Version 1.4.2**

* Die Rückspaltung bei einer Werbeunterbrechung führt zum Abschluss des Streams.

Der Media Player sendet MediaPlayerState.Complete fälschlicherweise während des Rückspulens von Trick Play ab, wenn eine Anzeigengrenze erreicht wird. Der Player sollte dieses Ereignis im Trick Play-Modus ignorieren, andernfalls verarbeitet das SDK den Status korrekt.

**Version 1.4.0 (1086)**

* PTPLAY-1634 - Das gleiche abonnierte Tag hat unterschiedliche Zeitstempel in verschiedenen Live-Fenstern. Wenn Live-Fenster verschoben werden, sollte dasselbe Tag in jedem von ihnen dieselben Zeitstempel haben. Manchmal haben aber auch dieselben Tags unterschiedliche Zeitstempel.
* PTPLAY-2541 - COMPONENT_CREATION_FAILURE wird manchmal nach mehreren Switches zum/vom alternativen Stream in Blackouts gesehen
* Fehler #3726865 - Wenn ein MultiBitrate-LBA-Stream Beginn aus einem reinen Audio-Stream enthält, wird das Video nicht angezeigt, wenn auf einen Audio-/Video-Stream gewechselt wird. Von einem Audio-/Video-Stream ausgehend wird dieses Problem nicht angezeigt und kann erfolgreich zwischen Audio- und Audio-/Video-Streams wechseln
* Fehler #3760144 - Die Auflösung kann sich verschieben oder zu pulsieren scheinen, wenn ein Stream auf einigen Geräten wie Kindle Fire 7 und Samsung Galaxy Nexus angehalten wird. Nur bei sorgfältiger Prüfung sichtbar
* Fehler #3761170 - searchToLocal in Live with Ads kann nicht wieder in Anzeigeninhalte suchen; es ist am besten, die currentTime-APIs für Live-Streams zu verwenden
* Fehler #3763370 - Live-Streams mit Anzeigen zeigen gelegentlich zwei Anzeigenmarken nahe beieinander, wenn nur eine vorhanden sein sollte. Diese Anzeigenmarkierungen stellen dieselbe Anzeige dar und nur eine wird wiedergegeben
* Fehler 3763373 - Die Anzeigenmarke wird möglicherweise kurz ausgeblendet, wenn eine Anzeige in VOD-Streams gefunden wird. Die Anzeigenmarke wird wiederhergestellt und es gibt keine anderen negativen Auswirkungen auf die Zeitschiene
* Bei einigen Geräten treten bekannte Wiedergabeprobleme auf. Weitere Informationen finden Sie unter [Bekannte Geräteprobleme in 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Referenzimplementierung - Trick play wird in der Beispielanwendung nicht implementiert.

## Bekannte Geräteprobleme in 1.4 {#known-device-issues-in}

| Gerät | Chipsatz | Problem | Ursache | Problemumgehung |
|--- |--- |--- |--- |--- |
| Droid X | TI OMAP3 | ABR-Verzögerung wird erwartet, da der Decoder neu gestartet wird. |  |  |
| HTC Desire (anders als HTC Desire HD) | QSD 8250 | Video kann nicht wiedergegeben werden. Gibt den Fehler VIDEO_PROFIL_NOT_SUPPORTED zurück. | Dessire stellt keinen richtigen HW-Decoder bereit. Es gibt Stagefright&#39;s SW Decoder. | Starten Sie das Gerät neu. |
| HTC EVO 4G | QSD 8650 | Kein HW-Decoder. | Qualcomm hat keinen HW-Decoder. | Aktualisieren Sie auf Android 4.x. |
| Kindle FireSystem Version 6.0 | TI OMAP4 | Es werden keine HLS-Streams wiedergegeben. Video unter AIR funktioniert nicht. |  | Aktualisieren Sie auf die Systemversion 6.3. |
| Kindle Fire HD | TI OMAP4 | Kann in einen Zustand gelangen, in dem Videos nicht abgespielt werden können. Gibt VIDEO_PROFIL_NOT_SUPPORTED- und UNRECOVERABLE_ERROR-Fehler zurück. | Der HW-Decoder befindet sich in einem nicht wiederherstellbaren Zustand, wenn die App den HW-Decoder nicht vollständig herunterfährt, z. B. nach einem Absturz. Gilt auch für native Apps auf dem Gerät. | Starten Sie das Gerät neu. |
| Kindle Fire HD 8.9 | Snapdragon 800 | AVE stürzt nach mehreren ABR-Switches ab. |  |  |
| Motorola Atrix | Tegra2 | Allgemeine Leistungsprobleme mit AVE im Gegensatz zu AIR. Audio/Video nach der Synchronisierung stürzt die Videowiedergabe nach der Wiedergabe zwischen 9 und 15 Minuten ab. Abstürze. | Möglicherweise in Zusammenhang mit openGLES, die wir auf AIR aktivieren. wird untersucht. |  |
| Nexus 7 (2. Generation) | S4Pro APQ8064 (Qualcomm) | Das Gerät hängt, wenn ein Film länger als 30 Minuten angehalten wird. | Geräteproblem, das Google gemeldet wurde. | App sollte einen Timeout-Wert aufweisen, damit kein langer Pausenstatus zulässig ist. |
| Nexus S (GB) | Hummer Vogel | Keine Videowiedergabe mit HW-Decoder möglich. | Es gibt keinen Stagefright-basierten HW-Decoder in Nexus S, daher verwenden wir für Android 2.3 einen SW-Decoder. | Aktualisieren Sie auf ICS. |
| Nexus S (ICS) | Hummer Vogel | Videos flackern gelegentlich. | Schlechte Daten können dazu führen, dass der Decoder in einen schlechten Zustand gerät. | Starten Sie das Gerät neu. |
| Nook-TabletAndroid-Betriebssystem: 2.3 | TI OMAP 4 | Video wird nicht abgespielt und App hängt. | Stagefright tritt nach einiger Ausführung der App in einen instabilen Zustand ein. Aufrufe an mediaPlayer::QueryCodecs hängen. | Starten Sie das Gerät neu, um den Status zurückzusetzen. |
| Samsung Galaxy ACE | Qualcomm MSM7227 | Die SampleMediaPlayer-App kann nicht installiert werden. | Verwendet ARM v6 anstelle des gebräuchlicheren ARM v7-Chipsatzes. FP/AIR unterstützt dieses Gerät nicht. |  |
| Samsung Galaxy ACE2Android OS: 2.3.6 | NovaThor U8500 | Video kann nicht wiedergegeben werden. | Dieser Chipsatz ist ein unbekannter Decoder für Android pre-ICS in AVE. |  |
| Samsung Galaxy S2 (GT-I9100) | Exynos | Die Videoleistung ist für dieses Gerät nicht annähernd gleich. | Der HW-Decoder gibt dekodierte Frames mit dem falschen PTS zurück. Sieht so aus, als ob der Decoder die Dekodierungszeit anstelle der Präsentationszeit verwendet. |  |
| Samsung Galaxy S2 GAndroid OS: 2.3.6 | TI OMAP4 | Abstürze beim Starten des Videos. |  | Aktualisieren Sie auf Android 2.3.7 oder 4.x. |
| Samsung Galaxy S3 (I747) | Qualcomm MSM8960 | Gelegentlich friert das Video ein, und es wird nur die Audiowiedergabe durchgeführt, sodass es nicht mehr reagiert. |  |  |
| Samsung Galaxy S3 I747M | SAMSUNG_M2ATT | Video friert ein. | Untersuchung. |  |
| Samsung Galaxy Tab 1 v10.1 | Tegra 2 | Die MBR-Transition kann bis zu drei Sekunden dauern. | Als Korrektur für MBR-Abstürze starten wir den Decoder für jeden Stream-Switch neu, was bis zu drei Sekunden dauern kann. |  |
| Samsung Galaxy |  | Die SampleMediaPlayer-App kann nicht installiert werden. | Verwendet ARM v6 anstelle des gebräuchlicheren ARM v7-Chipsatzes. FP/AIR unterstützt dieses Gerät nicht. |  |
| Xoom | Tegra | Einige Frames werden zum Wechseln entfernt. Der Decoder wird nicht neu gestartet. | Begrenzung von OMXAL. |  |

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).
