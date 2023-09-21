---
title: TVSDK 1.4 für Android - Versionshinweise
description: TVSDK 1.4 für Android - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 1.4.
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '7802'
ht-degree: 0%

---

# TVSDK 1.4 für Android - Versionshinweise {#tvsdk-for-android-release-notes}

TVSDK 1.4 für Android - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme sowie die Geräteprobleme in TVSDK Android 1.4.

## Neue Funktionen {#new-features}

**Version 1.4.43**

**Sicheres Laden von Anzeigen über HTTPS**

Adobe Primetime bietet die Möglichkeit, den ersten Aufruf an den Primetime-Anzeigenserver und CRS über HTTPS anzufordern.

**alwaysUseAudioOutputLatency(boolean val) in MediaPlayer-Klasse**

Wenn dieser Parameter festgelegt ist, verwenden Sie die Latenz der Audioausgabe in der Berechnung des Audio-Zeitstempels.

Es akzeptiert einen booleschen Parameterwert. Wenn der Wert `True`, verwendet der Client die Latenz der Audioausgabe in der Berechnung des Audio-Zeitstempels.

**Version 1.4.42**

**Einfügen einer partiellen Werbeunterbrechung:**
TV-ähnliche Erlebnisse beim Beitritt mitten in einer Anzeige, ohne dass das Tracking für die teilweise überwachte Anzeige ausgelöst wird.
Beispiel: Der Benutzer schließt sich in der Mitte (40 Sekunden) einer 90-Sekunden-Werbeunterbrechung an, die aus drei 30-Sekunden-Anzeigen besteht. Dies ist 10 Sekunden nach der zweiten Anzeige in der Pause.
* Die zweite Anzeige wird für die verbleibende Dauer (20 Sek.) gefolgt von der dritten Anzeige wiedergegeben.
* Anzeigentracker für die abgespielte partielle Anzeige (zweite Anzeige) werden nicht ausgelöst. Die Tracker für nur die dritte Anzeige werden ausgelöst.

**Version 1.4.41**

Keine neuen Funktionen.

**Version 1.4.40**

Keine neuen Funktionen.

>[!NOTE]
>
>Sie benötigen die API-Änderungen nicht, wenn Sie eine Version vor 1.4.39 verwenden.

**Version 1.4.39**

* TVSDK ist mit VHL 2.0.1 und VHL 2.0.1 mit Nielsen zertifiziert.
* Android TVSDK wird aktualisiert, um CRS-Anforderungen vom neuen Akamai-Host zu stellen `primetime-a.akamaihd.net`.
* Die neue Hostnamenkonfiguration ermöglicht eine skalierbarere Bereitstellung von CRS-Assets über HTTP und HTTPS (SSL).
* TVSDK unterstützt die Android Oreo-Version.
* Eine neue Funktion wird hinzugefügt zu `AdClientFactory` -Klasse zur Unterstützung der Registrierung mehrerer Opportunity-Detektoren:

  ```
  public List<PlacementOpportunityDetector> createOpportunityDetectors(MediaPlayerItem item);
  ```

  Dies sollte ein Array von PlacementOpportunityDetector zurückgeben. Jetzt können Sie mehrere Opportunity-Detektoren registrieren. Beispielsweise waren für die Funktion zum frühen Beenden von Anzeigen zwei Opportunity-Detektoren erforderlich - eine für das Einfügen von Anzeigen und eine andere für den frühen Beenden von Anzeigen. Sie müssen diese neue Funktion nur dann implementieren, wenn Sie Ihre eigene AdvertisingFactory implementiert haben (und nicht DefaultAdvertisingFactory verwenden). Um das vorhandene Verhalten abzurufen, müssen Sie einen einzelnen Opportunity-Detektor erstellen, wie in der Funktion createOpportunityDetector() , in ein Array einfügen und zurückgeben:

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
>Sie benötigen die API-Änderungen nicht, wenn Sie eine Version vor 1.4.39 verwenden.

**Version 1.4.36**

Fehlerbehebung für das Überspringen von Inhalten unter Android.

**Version 1.4.35**

* **Netzwerkanzeigen-Informationen**

  TVSDK-APIs bieten jetzt zusätzliche Informationen zu VAST-Antworten von Drittanbietern. Anzeigen-ID-, Anzeigen- und VAST-Anzeigenerweiterungen werden in der NetworkAdInfo-Klasse bereitgestellt, auf die über die Eigenschaft networkAdInfo für ein Anzeigen-Asset zugegriffen werden kann. Diese Informationen können für die Integration mit anderen Ad Analytics-Plattformen wie **Moat Analytics**.

**Version 1.4.31**

**Multi-CDN-Unterstützung für CRS-Anzeigen**
* Standardmäßig werden alle transkodierten Assets auf einem Adobe-eigenen CDN auf Akamai gehostet. Mit der neuesten Version bietet Adobe Creative Repackaging Service (CRS) die Möglichkeit, die transkodierten kreativen Inhalte wie vom Kunden angegeben in mehrere CDNs hochzuladen.
* TVSDK werden neue APIs hinzugefügt, um die Angabe der endgültigen kreativen CRS-URL zu ermöglichen, wenn die Standard-URL nicht verwendet wird. Informationen zur Verwendung dieser neuen APIs finden Sie in der Dokumentation .

**Version 1.4.18**
Das Primetime Android TVSDK unterstützt jetzt Javascript-Kreativelemente mit VPAID 2.0, um ein interaktives, umfangreiches Inhalts-Anzeigenerlebnis zu ermöglichen. Weitere Informationen zu VPAID 2.0 finden Sie unter [VPAID-Anzeigenunterstützung](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/vpaid-ads/android-3x-vpaid-ads.md).

**Version 1.4.17**

AC-3 5.1 wird nur auf Amazon FireTV unterstützt.

**Version 1.4.11**

* **Ad Fallback, Daisy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103)** Bei VAST-Anzeigen (Kreativen) mit aktivierter Ausweichregel behandelt TVSDK eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht, an ihrer Stelle Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Weitere Informationen finden Sie unter [Anzeigen-Fallback für VAST- und VMAP-Anzeigen](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-fallback/android-3x-ad-fallback.md).

* **Video Heartbeats Library (VHL) aktualisiert auf Version 1.5**
   * Möglichkeit zum Senden von Metadaten mit Videostart und/oder Video/Anzeige/Kapitelstart als Kontextdaten
   * Weniger Netzwerk-Traffic - Heartbeats sind im Durchschnitt weniger und kleiner

**Version 1.4.7**

* **On-Premise-Individualisierungsunterstützung** Unterstützung für On-Premise-Installationen des Adobe Individualization Servers, um die Individualisierungsanforderung des Clients so anzupassen, dass sie an einen anderen Endpunkt gesendet wird.

**Version 1.4.6**

* **AES-Beispielverschlüsselung (Flash Player Version 17.0.0.134 erforderlich)**Beispielbasierte AES-Verschlüsselung wird jetzt unterstützt.

**Version 1.4.2**

* **Aktualisierung der Video Heartbeats Library (VHL) auf Version 1.4.0.1**

   * Es wurde die Möglichkeit hinzugefügt, verschiedene Analytics-Anwendungsfälle von anderen SDKs oder Playern mit den Adobe Analytics-Video-Grundlagen zu bündeln.
   * Das Anzeigen-Tracking wurde optimiert, indem die Methoden trackAdBreakStart und trackAdBreakComplete entfernt wurden. Die Werbeunterbrechung wird aus den trackAdStart - und trackAdComplete -Methodenaufrufen abgeleitet.
   * Die Eigenschaft &quot;playhead&quot;ist beim Tracking von Anzeigen nicht mehr erforderlich.

* **Nielsen-SDK-Integration** Das TVSDK unterstützt jetzt das Senden von Benutzer-Tracking-Informationen an das Nielsen-SDK ohne benutzerdefinierte Integration.

**Version 1.4.0**

* **Blackout-Signalisierung mit Ersatz für alternativen Inhalt** Als Teil des TVSDK-Updates für 1.4 unterstützt das TVSDK jetzt auch das Wechseln in regionale Blackouts und das Zurückkehren aus linearen Inhalten. Das TVSDK kann jetzt zwei Manifestdateien parallel, Hauptdatei und alternative verarbeiten, um Blackout-Signale zu überwachen, selbst wenn anstelle der ursprünglichen Programmierung alternative Programmierung angezeigt wird.

* **C3-Anzeigen entfernen/ersetzen** Jetzt ist keine zusätzliche Vorbereitung erforderlich, um neue Anzeigen dynamisch in Video-On-Demand-Assets (VOD) einzufügen, die aus dem C3-Fenster herauskommen. Das TVSDK bietet jetzt eine API zum Entfernen benutzerdefinierter Inhaltsbereiche und zum dynamischen Einfügen neuer Anzeigen. Diese leistungsstarke neue Funktion ist auch in Fällen nützlich, in denen Live-/lineare Inhalte während der Übertragung bereitgestellt werden und sofort zur Verwendung als On-Demand-Inhalt abgerufen werden, ohne dass genügend Zeit bleibt, das Asset zu &quot;bereinigen&quot;.

* Die Schnittstelle PlaybackEventListener verfügt über eine neue Methode namens onReplaceMediaPlayerItem , mit der Sie auf ein neues Ereignis überwachen können. `ITEM_REPLACED`. Dieses Ereignis wird jedes Mal ausgelöst, wenn eine MediaPlayer-Elementinstanz in MediaPlayer ersetzt wird. Die Client-Anwendung, die diesen PlaybackEventListener implementiert, muss diese neue Methode implementieren oder überschreiben.
* AdClientFactory hat eine neue Funktion zur Klasse hinzugefügt, um sich für mehrere Opportunity-Detektoren zu registrieren:

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

* Die Schnittstelle PlaybackEventListener verfügt über eine neue Methode namens onReplaceMediaPlayerItem, mit der Sie auf ein neues Ereignis warten können, ITEM_REPLACED. Dieses Ereignis wird jedes Mal ausgelöst, wenn eine MediaPlayer-Elementinstanz in MediaPlayer ersetzt wird. Die Client-Anwendung, die diesen PlaybackEventListener implementiert, muss diese neue Methode implementieren oder überschreiben.

* AdClientFactory hat eine neue Funktion zur Klasse hinzugefügt, um sich für mehrere Opportunity-Detektoren zu registrieren:

```
public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem item);
```

Für die Funktion zum Beenden früherer Anzeigen benötigen Sie beispielsweise zwei Opportunity-Detektoren - eine für das Einfügen von Anzeigen und eine andere für den frühzeitigen Ausstieg aus Anzeigen.

Um diese neue Funktion außer Kraft zu setzen, erstellen Sie einen einzelnen Opportunity-Detektor, setzen Sie ihn in ein Array und geben Sie Folgendes zurück:

```
@Override

public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {

List`<PlacementOpportunityDetector>` opportunityDetectors = new ArrayList`<PlacementOpportunityDetector>`();

opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));

return opportunityDetectors;

}

}
```

## Gerätezertifizierung und -unterstützung in 1.4 {#device-certification-and-support-in}

>[!NOTE]
>
>Die folgenden Funktionen sind **not** unterstützt im TVSDK :
>
>* Langsames Bewegen auf allen Plattformen oder Versionen.
>* Live Trick Play.

**Version 1.4.43**

TVSDK 1.4.43 wurde mit Android-Geräten mit Android 6.0.1/ 7.0 und 8.1 (Oreo) zertifiziert.

* **Version 1.4.23:**

   * TVSDK 1.4.23 wurde für Android-Geräte mit Android N zertifiziert.

* **Version 1.4.18:**

   * Primetime wurde für Amazon Fire TV zertifiziert.
   * VPAID 2.0 wird nur auf Geräten mit Android 4.0 und höher unterstützt.

## Behobene Probleme in Version 1.4 {#resolved-issues-in}

>[!NOTE]
>
>Alle TVSDK-Kunden, die CRS verwenden, werden dringend aufgefordert, ein Upgrade auf TVSDK 1.4.39 oder neueste Version auf iOS und Android durchzuführen. Dieses Upgrade ersetzt die vorhandene App-Implementierung. Suchen Sie nach dem Upgrade nach den kreativen CRS-URL-Anforderungen in einem Proxy-Tool (z. B. Charles), um sicherzustellen, dass die Version im Pfad die Version 3.1 widerspiegelt. Beispiel:
>
>`https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8`

**Version 1.4.43**

* Ticket 27143 - 5.1-Audio-Track kann nicht auf FireTV-Geräten wiedergegeben werden

   * TVSDK kann jetzt AC3-Audio auf FireTV-Geräten abspielen. Die Wiedergabe erfolgt immer in Stereo.

* Ticket #33902 - Sichere Anzeigenbereitstellung über HTTPS

   * Adobe Primetime bietet die Möglichkeit, den ersten Aufruf an den Primetime-Anzeigenserver und CRS über HTTPS anzufordern.

* Ticket #34493 - Bluetooth-Audio-Verzögerung

   * hinzugefügt `alwaysUseAudioOutputLatency` in der MediaPlayer-Klasse, die bei Festlegung dazu führt, dass bei der Berechnung des Audiozeitstempels die Latenz der Audioausgabe verwendet wird.

* Ticket #34949 - Neue Version der Video Heartbeat Library (VHL) integriert.

**Version 1.4.42 (1791)**

* Zendesk #33719: FireTV 4k Adaptive Bitrate wird langsam skaliert. Unterstützung für ABR für FireTV 4K-Geräte hinzugefügt.
* Zendesk #33338: resetDRM löscht alle Daten der Anwendung.  Es wurde ein zusätzlicher Fall behandelt, bei dem Ausnahmen in Nicht-TVSDK-Threads dazu führten, dass TVSDK-Vorgangswarteschlangen gefüllt wurden.

**Version 1.4.41 (1776)**

* Zendesk #33002 - Companion Asset Data from TVSDK on Fire TV. Implementierung einer neuen Klasse AdBannerAsset , die die Companion-Daten als Liste zurückgibt &lt;adbannerasset> und AdAsset::id ist jetzt ein String anstelle von long.
* Zendesk #32821 - Der Android Primetime-Player friert ein, wenn er für WWE den Präsentations-Zeitstempel (PTS) erkennt. Dieses Problem wurde in dieser Version behoben.
* Zendesk #33572 - VideoAnalyticsProvider Ad Start Absturz. Dieses Problem wurde durch die Verwendung der richtigen Kombination aus VHL+Nielsen Joint SDK Version von VideoHeartbeat.jar behoben.
* Zendesk #3355 - Fire TV: Scrub zurück 15 Sekunden Ausgabe. Keine Korrektur von TVSDK-Seite und -Kunde bestätigt dies bei ihrem End- und Drittanbieter.

**Version 1.4.40 (1764)**

* Zendesk #33068 - Amazon lip sync issue on new device. Das Problem bei der Lip-Synchronisierung wurde in diesen Versionen behoben.
* Zendesk #32215 - Android TVSDK 1.4.38 Sicherheitsprobleme `[Hotlist]`. Aktualisiert auf die neuesten OpenSSL-1.1.0 und curl-7.5.1.
* Zendesk #32920 - Leerer Bildschirm innerhalb einer Werbeunterbrechung und ohne Abschluss einer Werbeunterbrechung. Es wurde ein Problem behoben, bei dem ein VPAID-Container in einen hängenden Zustand versetzt wurde und ein Problem behoben wurde, bei dem Facebook VPAID-Anzeigen häufig mehrere CDATA-Blöcke in einem einzelnen \&amp;lt;AdParameters\&amp;gt; VAST-Knoten zurückgaben.

**Version 1.4.39 (1744)**

* Zendesk #28976 - Die Lizenzanfrage dauert mehr als eine Sekunde. Während DRM-Lizenzanforderungsaufrufe, die POST verwenden, ausgeführt werden, fügt Curl eine zusätzliche Kopfzeile &quot;Expect: 100-continue&quot;hinzu. Die Kopfzeile &quot;Expect:&quot;in TVSDK wurde entfernt.
* Zendesk #27707 - CSAI-Umgebungen berücksichtigen CUE IN-Markierungen nicht für die frühe Rückkehr oder Rückkehr zu Inhalten. Unterstützung für mehrere Opportunity-Generatoren.

**Version 1.4.38 (1722)**

* Zendesk #21590 - Videoleistung und -verfolgung in den neuesten Origin Builds

Integration und Zertifizierung von VHL 2.0 in TVSDK, um die Barrierefreiheit in der VideoHeartbeatsLibrary-Implementierung zu reduzieren, indem die Komplexität der APIs verringert wird.

* Zendesk #29688 - Support für Android O Beta-Kunden.

TVSDK-Unterstützung für die neue Beta-Version von Android.

**Version 1.4.36 (1713)**

* Zendesk #27392 - Überspringen von Inhalten auf Android

Um die Entschlüsselung zu ermöglichen, weitete das Android TVSDK fälschlicherweise den Byte-Bereich von Nicht-iFrame-Inhalten um 16 Byte aus. Die Erweiterung ist für iFrame-Streams erforderlich, nicht aber für Nicht-iFrame-Streams.

**Version 1.4.34 (1702)**

* Zendesk #27638 - Leak in cURL INet-Objekt

Das Posix cURL INet -Objekt leckte, während es auf den Share Manager und DNS-Cache hielt, der in den cURL-Verbindungen verwendet wurde.

Dieses Problem wurde behoben, indem das Posix cURL INet -Objekt aus dem INet-Dekrekonstruktor gelöscht wurde.

**Version 1.4.33 (1694)**

* **OpenSSL-Bibliothek**

Die OpenSSL-Bibliothek wurde mit der OpenSSL-Version 1.0.2j aktualisiert.

* Zendesk #21701 - Senden Sie die ursprüngliche kreative URL für die CRS-Anforderung 1401 anstelle der normalisierten URL.
Dieses Problem wird durch Senden der ursprünglichen kreativen URLs behoben.

* Zendesk #25023 - Lange Videowiedergabe: Videoeinfrieren, Bildschirmflackern Dieses Problem wurde behoben, indem die maximalen Abmessungen für das Videoformat für Set-Top-Box-Geräte von CenturyLink festgelegt wurden.

* Zendesk #27460 - Das neue Akamai-Konto kann eine POST-CDN-Anfrage nicht verarbeiten.
Der Code wurde aktualisiert, um die `cdn.auditude.com` -Anzeigenanforderung GET anstelle von POST sein.

* Zendesk #28245 - Der Wiedergabestatus wird nicht korrekt benachrichtigt, wenn die App von Hintergrund zu Vordergrund wechselt. Dieses Problem wurde behoben, indem der Wiedergabestatus korrekt wiedergegeben oder angehalten wurde, wenn die Anwendung in den Vordergrund zurückkehrt.

**Version 1.4.32 (1682)**

* Zendesk #25779 - Sicherheitslücke, die mit TVSDK Android 4.2 und niedriger gefunden wurde, weist eine Sicherheitslücke auf, wenn JavaScript in einer WebView aktiviert ist. Die Verwendung von WebView durch TVSDK wurde für Geräte mit OS 4.2 oder niedriger deaktiviert. Dadurch wird die Verwendung von VPAID-Anzeigen in TVSDK auf diesen Geräten deaktiviert.

* Zendesk #26890 - Problem im SCREEN-Status (EIN/AUS) bei der Handhabung von Ref. Player Wenn die Adobe-Video-Engine (AVE) von einem AUSGESETZTEN Status fortgesetzt wird, aktualisiert der DefaultMediaPlayer seinen Status nicht. Daher bleibt der DefaultMediaPlayer im Status AUSGESETZT, auch wenn der AVE-Status WIEDERGEGEBEN ist. Dieses Problem wurde behoben, indem der Status DefaultMediaPlayer auf PLAYING gesetzt wurde, wenn ein PLAY-Status von AVE empfangen wurde, selbst wenn der aktuelle Status von DefaultMediaPlayer AUSGESETZT ist.

**Version 1.4.31 (1675)**

* Zendesk #21974 - Ausnahmen aufgrund von Null-Objekten
   * AdIndex wird bei null selten inkrementiert. Dies kann auf falsche API-Aufrufe zurückzuführen sein, die für Pre-roll adBreak empfangen wurden. Korrektur der Datentypen, um solche Ausnahmen zu vermeiden

* Zendesk #24714 - Deaktivieren der externen Protokollierung
   * TVSDK wurde aktualisiert, um die irrelevante Protokollierung zu deaktivieren

* Zendesk #24488 - Probleme bei der AV-Synchronisierung bei Fire TV
   * Fehlerkorrektur - die Verarbeitung der AV-Decoder-Threads wird verbessert. Insbesondere wird bei jeder Änderung der Eingabe- oder Ausgabeframe-Warteschlangen der für den Inhaltstyp des Frames spezifische Decoder-Thread ausgeführt.

* Zendesk #26551 - Beheben der CRS-Fehler
   * Wenn die Anfrage HEAD (HTTP-Kopfzeile) lautet, müssen wir den Inhalt nicht lesen, da er leer ist. Während es in Ordnung ist, zu versuchen, sie zu lesen, hängt die alte Android (4.0.x), während wir read() aufrufen, und die neuere Android gibt den richtigen Wert (-1) zurück, wenn wir read() aufrufen. Auf dieser Grundlage wurde der Code geändert, sodass kein Inhalt für &quot;head&quot;gelesen wird.

* Zendesk #26696 Null Pointer Ausnahme beim Zugriff auf TrickPlayManager
   * Fehlerkorrektur - vor der Verwendung wird geprüft, ob das Objekt &quot;TrickPlayManager&quot; nicht null ist.

**Version 1.4.30 (1659)**

* Zendesk #22675 Asset-Dauer wird für Live-/Linear-Streams nicht aktualisiert. Dieses Problem wurde behoben, indem eine neue API, assetDuration, in PTVideoAnalyticsTrackingMetadata bereitgestellt wurde, die die Asset-Dauer für Live- und lineare Streams bereitstellt.

* Zendesk #25853 Speicherleck in TVSDK beim Wechsel von Kanälen Das Problem, dass ein Pufferleck beim Zurücksetzen oder Verlassen des MediaPlayers beim Herunterladen einer Datei behoben wurde.

**Version 1.4.29 (1653)**

* Zendesk #21200 - Player erholt sich nicht von ausgesetzten Status, wenn die App im Hintergrund war. Wenn der Player nach der Anzeige des Stream-Switches ausgesetzt wurde, ermöglicht die Auflösung dem Player, den Stream-Schalter beim Wiederherstellen des Players aus dem Aussetzen-Status auszuführen, anstatt zur vorherigen Position zurückzukehren.

* Zendesk #23412 - Player ist mit einem schwarzen Kasten fixiert, wenn Sie innerhalb der letzten drei Sekunden der Werbeunterbrechung durch Anzeigen klicken. Dieses Problem ist dasselbe Problem wie Zendesk #21200.

* Zendesk #23616 - Übersprungene Werbeunterbrechungen Suchvorgänge in der Zukunft zu weit. Abhängig vom Anzeigeneinfügetyp (Einfügen/Ersetzen) bestimmt TVSDK, ob die Anzeigendauer in der Berechnung zur Bestimmung des Endpunkts der Werbeunterbrechung verwendet wird.

* Zendesk #25078 - TVSDK DRM Speicherleck auf Android TV STB Das Speicherleck für das DRM Adapterobjekt wurde gefunden und korrigiert.

* Zendesk #25067 - Absturz in VideoEngineTimeline Dies geschieht, weil Objekte nicht korrekt bereinigt wurden und Ereignisse aufgerufen wurden, nachdem die Objekte zerstört wurden. Das Problem wurde behoben, indem Prüfungen hinzugefügt wurden, um Null-Ausnahmen zu verhindern.

* Zendesk #25352 - Festlegen eines benutzerdefinierten HTTP-Headers Dieses Problem wurde behoben, indem ein neuer benutzerdefinierter Header zur Zulassungsliste auf TVSDK hinzugefügt wurde.

* Zendesk #25617 - Live-Stream-PTS-Rollover, der die Diskontinuität des Players und den Speicherabsturz verursachte Dieses Problem wurde behoben, indem eine PTS-Rollover-Handhabung in FragmentedHTTPStreamer hinzugefügt wurde, wenn mitten in einem Segment ein Rollover stattfindet.

**Version 1.4.28 (1637)**

* Zendesk #23618 - Werbeunterbrechungsereignisse werden ausgelöst, bevor die Anzeigenrichtlinie konsultiert wird. Dieses Problem wurde behoben, indem die AD_BREAK_START- und AD_START-Ereignisse nicht ausgelöst wurden, wenn die Anzeige aufgrund von adForgiability übersprungen wurde. Stattdessen wird das AD_BREAK_SKIPPED -Ereignis gesendet.

**Version 1.4.27 (1631)**

* Zendesk #23174 - Leistungsproblem beim Ändern der Größe des Videos Dieses Problem wurde behoben, indem eine neue API, MediaPlayerView.setSurfaceFixedSize, nachgewiesen wurde, die es TVSDK ermöglicht, über MediaPlayerView auf SurfaceHolder.setFixedSize() zuzugreifen.

* Zendesk #24450 - TVSDK stellt doppelte Anzeigenanfragen Dieses Problem trat auf, wenn die verstrichene Zeit in lange und nicht verdoppelt wurde. Dieses Problem wurde behoben.

**Version 1.4.26 (1627)**

* Zendesk #21436 - Aktualisierung der OpenSSL-Bibliothek auf Version 1.0.2h Aktualisierung der OpenSSL-Bibliothek auf OpenSSL-Version 1.0.2h
* Zendesk #23825 - Cookies werden nicht in die Rückrufe einbezogen, die durch die Unterstützung von Android-Cookies korrigiert wurden.

**Version 1.4.25 (1620)**

* Zendesk #22900 - Live Adobe Primetime DRM-Stream wird nicht auf dem Android-Referenz-Player wiedergegeben. Das Problem mit der Speicherzuordnung wurde behoben.
* Zendesk #23176 - Anwendung stürzt ab, wenn versucht wird, VPAID-Anzeigen abzuspielen Der Absturz trat auf, da die Anwendung keine benutzerdefinierte Anzeigenansicht erstellt, um eine VPAID-Anzeige zu rendern. Dieses Problem wurde behoben, indem die VPAID-Anzeigen in der Antwort des Werbeservers ignoriert wurden, wenn keine benutzerdefinierte Anzeigenansicht vorhanden ist.

* Zendesk #23153 - SampleAES DRM Stream - Wiedergabe im TVSDK Reference Player angehalten Dieses Problem ist mit dem Zendesk #22900 identisch.

**Version 1.4.24 (1612)**

* Zendesk #20784 - Analytics: Auslösen von Inhaltsbeendigungen für Live-Videoübergänge Dieses Problem wurde behoben, indem eine API (trackVideoComplete) hinzugefügt wurde, um den Inhaltsabschluss während einer Live-/linearen Videoverfolgungssitzung manuell Trigger.

* Zendesk #21977 VideoEngineTimeline Absturz während placeAdBreak/acceptAd-Vorgang
   * In diesem Problem wurden die folgenden Bibliotheken aktualisiert:
      * AdobeMobile-Bibliothek auf Version 4.10.0
      * VHL-Bibliothek in Version 1.5.6
      * VHL-Nielsen-Bibliothek in Version 1.6.7

Dieses Problem wurde behoben, indem eine Null-Prüfung hinzugefügt wurde, bevor Anzeigen zur akzeptierten Anzeigenliste hinzugefügt wurden.

* Zendesk #22313 Die Bitrate für die STBs mit Amilogic-Chipsatz liegt nicht über 1,2M. Dieses Problem wurde behoben, indem die Medien-Codec-Funktionen vorgeladen und der nahtlose Switch für Amilogic Chipsatz-Geräte deaktiviert wurde.

* Zendesk #19520 Beispiel-AES-HLS-Asset wird nicht in TVSDK-Playern wiedergegeben Dieses Problem wurde behoben, indem mehrere PMT-Deskriptoren für Beispiel-AES-verschlüsselte HLS-Streams verarbeitet wurden.

**Version 1.4.23 (1602)**

* Zendesk #18852 - Aktualisieren der kreativen Auswahllogik basierend auf CRS-Regeln Dieses Problem wurde behoben, indem eine JSON-Konfigurationsdatei hinzugefügt wurde, um die Priorität der kreativen Auswahl anzugeben.

* Zendesk #20861 - Android N Diese Version bietet Unterstützung für Android N, da es nicht mehr möglich ist, native Bibliotheken der Android-Plattform direkt zu verwenden, die für Anwendungen, die unter Android N ausgeführt werden, nicht mehr zugänglich sind.

* Zendesk #21018 - Android N absturz Gleiche Auflösung wie ZD# 20861.

* Zendesk #21266 - VideoEngineAdapter stürzt bei einem Invalid_Key-Fehler ab Der Invalid_Key-Fehler enthält keine Beschreibung von AVE. Daher führte das Parsen des Textes zu NPE. Das Problem wurde behoben, indem eine Null-Prüfung für die Beschreibung während onError hinzugefügt wurde, bevor die Beschreibung analysiert wurde.

* Zendesk #2286 - Native Bibliothek weist Speicherleseschlüssel/Fragment zu, was zu Abstürzen führt. Dieser Absturz, der unter Android auftrat, wenn versucht wurde, ein Manifest mit mehreren Schlüsseln gleichzeitig zu laden, wurde behoben.

**Version 1.4.22 (1581)**

* Zendesk #17236 - Unzuverlässige Abspielkopfzeit für HLS-Videos mit DRM Der Zeitsprung mit den LBA-Streams, bei dem die Startzeit des Audiosegments nicht mit der Startzeit des Videosegments übereinstimmt, wurde behoben.

* Zendesk #17680 - Die Videowiedergabe friert in der Selevision Andredo-Box ein. Der Video-Decoder auf diesem Gerät gibt manchmal einen signifikanten Zeitsprung zurück, wenn der Video-Frame aus dem Ausgabepuffer entfernt wird. Dieser Zeitstempel bleibt hoch. Dieses Problem wurde behoben, indem eine *Videoprofil nicht unterstützt* -Fehler, der den Player nicht zwingt, dasselbe Profil erneut auszuführen oder ein anderes Profil auszuwählen.

* Zendesk #19074 - Video-Freeze während FFWD- und REW-Trick-Wiedergabe Dieses Problem wurde behoben, indem eine neue Warnung TRICKPLAY_ENDED_DUE_TO_ERROR hinzugefügt wurde, um der Anwendung mitzuteilen, dass die Trickplay beendet wurde und das Video aufgrund eines nicht wiederherstellbaren Fehlers angehalten wurde.

* Zendesk #19574 - TVSDK gibt keine M3U8-Antwortdaten für DRM- oder Nicht-DRM-Inhalte zurück. Dieses Problem wurde wie folgt behoben:

* Zendesk #19986 - OP-Verhalten für bestimmte Geräte wie Android TV unterbrochen
* Hinzufügen eines Fehlers FILE_NOT_FOUND zur Bedingung.
* Wenn der Fehler von einer *Datei nicht gefunden* Fehler, wobei die URL und die Antwort von der Fehlerbeschreibung getrennt werden, wenn die Antwort verfügbar ist.
Der Logikfehler, der durch die Unterstützung von NVidia Schild OP eingeführt wurde, wurde behoben. Vertrauen Sie auf Nicht-NVidia-Schild-Geräten auf die sicheren Display-Flags, selbst wenn der Anzeigetyp unbekannt ist.

* Zendesk #20549 - Umgang mit veralteten Playlists. Dieses Problem wurde behoben, indem das Intervall zwischen der Aktualisierung des Live-Manifests auf die Hälfte der erwarteten Segmentdauer reduziert wurde, wenn der vorherige Abruf keine neuen Segmente erhält.

* Zendesk #20742 - Die Speichernutzung scheint bei der Wiedergabe von Live-Inhalten auf FireTV weiter zu steigen. Der Absturz wird durch die JNI-Objektverweistabelle verursacht, die den Grenzwert erreicht hat. Dieses Problem wurde behoben, indem der Verweis auf das MediaFormat-Objekt gelöscht wurde, das beim Neustart des Decoders erstellt wurde.

* Zendesk #21125 - Return from live/linear ad break arly (CSAI). Es wurde eine Funktion hinzugefügt, die es dem Player ermöglicht, während einer Werbeunterbrechung zum Hauptinhalt zurückzukehren, wenn der Player die Aufteilung in Anzeigen-Hinweisen mithilfe des Splice im Opportunity-Detektor registriert.

* Zendesk #21334 - TVSDK-Wert für Zeitüberschreitung bei Anzeigenanfragen von Drittanbietern. AdvertisingMetadata wurde eine Einstellung adRequestTimeout hinzugefügt, die einen globalen Timeout für den Anzeigenaufruf ermöglicht.

**Version 1.4.21 (1566)**

* Zendesk #17781 - ADB screenCapture funktioniert nicht mehr. Dieses Problem wurde durch Hinzufügen der API DefaultMediaPlayer.create(Context context, boolean secureSurface) behoben, die die Bildschirmaufzeichnung ermöglicht.
Übergeben Sie &quot;false&quot;für secureSurface, um die Erfassung von Bildschirmen zu ermöglichen.
Wichtig: Es wird dringend empfohlen, diese Bildschirmaufzeichnungsfunktion nicht in einer Produktionseinstellung zu aktivieren.

* Zendesk #19074 - Video-Freeze während FFWD- und REW-Trick-Wiedergabe Die folgenden Probleme, die auftraten, wenn das trickPlay in der Wiedergabe einfrieren konnte, wurden behoben:

* Zendesk #19532 - Close Caption erscheint nicht in der richtigen Reihenfolge
   * FHS beginnt mit Trickplay, aber das erste iframe-Segment enthielt keinen Rahmen.
   * Wenn beim Herunterladen eines iFrame-Segments eine Fehlerbedingung auftritt, wird die Wiedergabe beim Trickplay beendet und die Wiedergabe wird angehalten.
   * Die Implementierung von Android MediaCodec wartet ewig auf die Verfügbarkeit der Eingabeschlange, während sie aufgefordert wurde, alle Ein-/Ausgabe-Puffer zu leeren.
Dieses Problem wurde behoben, indem die Reihenfolge der WebVTT-Hinweise umgekehrt wurde, sodass mehrere überlappende Hinweise angezeigt werden, um nach oben zu scrollen.

* Zendesk #19574 - Das TVSDK gibt keine M3U8-Antwortdaten für DRM- oder Nicht-DRM-Inhalte zurück. Wenn das Laden fehlschlägt, meldet das TVSDK den Hauptteil der Fehlerantwort an die Anwendung nicht.
Dieses Problem wurde behoben, indem TVSDK die Fehlerantwort als Fehler an die Anwendung melden konnte.

* Zendesk #19701 - Die Wiedergabe mit SAP/Diskontinuität einfrieren Der Player friert ein, wenn Audio und Video bei Diskontinuität nicht ausgerichtet sind.

* Fehler #PTPLAY-1162 - Aktualisierung der OpenSSL-Bibliothek auf Version 1.0.2f wurde behoben.

**Version 1.4.20 (1546)**

* Zendesk #17384 - Feature Request: ID3-Metadatenunterstützung für AAC-Wiedergabe Unterstützung für ID3-Tags in AAC-Medien wurde ab Version 1.4.20 im TVSDK für Android bereitgestellt.

* Zendesk #18358 - Player friert beim Bitratenwechsel mit nicht synchronisierten Unterbrechungen ein. Dieses Problem wurde behoben, indem die ABR-Stitching-Edge-Fälle ordnungsgemäß verarbeitet wurden.

* Zendesk #19232 - App, die TVSDK 1.4.18 verwendet, verhält sich merkwürdig zu älteren Amazon OS-Versionen 4 Dieses Problem wurde behoben, indem die versteckte Erstellung von Webansichten im Initialisierungsprozess des TVSDK-Players entfernt wurde, um Konflikte mit Geräten zu vermeiden, die Android-Webview nicht unterstützen.

* Zendesk #19585 - Wiedergabe mit langsamer Motion bei Übergang der adaptiven Bitrate
Wenn während des ABR-Wechsels das neue Profil eine andere Audio-Sampling-Rate als das aktuelle Profil aufweist, wird die Wiedergabe schnell oder langsam. Der Grund dafür ist, dass der Videopräsentator nicht benachrichtigt wird, dass sich das Audioformat geändert hat.
Dieses Problem wurde behoben, indem sichergestellt wurde, dass die Benachrichtigungskennzeichnung an der richtigen Stelle gesetzt ist.

* Zendesk #19683 - SAP DAI-Wiedergabe - Kein Audio für einige Sekunden.
In mehreren Fällen in der TVSDK-Logik wurde beim Vergleich des Zeitstempels von zwei Ausgabedarstellungssegmenten RENDITION_TIMEOUT_THRESHOLD als akzeptabler Wertebereich verwendet, da der Zeitstempel nicht immer mit einer Differenz von 0 ms abgeglichen werden kann. Wenn die Lücke im Bereich von RENDITION_TIMEOUT_THRESHOLD liegt, wird angenommen, dass es sich um eine Übereinstimmung handelt.

Die RENDITION_TIMEOUT_THRESHOLD wurde auf 100 ms festgelegt, sie hat sich jedoch als unzureichend für bestimmte Streams erwiesen. Dieses Problem wurde behoben, indem der Wert für RENDITION_TIMEOUT_THRESHOLD auf 200 ms erhöht wurde.

* Zendesk #19699 - Das TVSDK kann nicht zwischen VTT-Untertitelspuren wechseln Dieses Problem wurde behoben, indem das Player-Dump erstellt und das Manifest neu geladen wurde, wenn sich ein Tracking ändert, und indem das UTF8-Konvertierungsproblem bei der Zeichenfolgenkonvertierung korrigiert wurde, das sich auf die Namen der WebVTT-Untertitel auswirkte.

* Zendesk #19717 - Anzeigeproblem bei CC-Optionen Dieses Problem wurde durch die korrekte Verarbeitung der Unicode-Zeichenfolge behoben.

* Zendesk #19910 - TIT2 ID3 Tags wurden nicht erkannt Dieses Problem wurde behoben, indem ID3 v2.4-Zeichenfolgenkodierungen umfassender unterstützt und ID3 v2.3 unterstützt wurde.

* Zendesk #20135 - Das TVSDK löst mehrere onComplete -Ereignisse für VOD-Inhalte aus.
Dieses Problem wurde behoben, indem der Ereignis-Listener post_roll_complete an der richtigen Stelle und nicht im vollständigen Fall des Statusänderungsereignisses hinzugefügt wurde.

**Version 1.4.19 (1521)**

* Zendesk #4180 - Das TVSDK erzwingt HDCP nicht.
   * Dies ist eine teilweise Korrektur für dieses Ticket und behandelt nur das Problem für NVidia-Schutzgeräte.
Sie müssen die korrekt implementierte HDCP-Erkennungs-API im Nvidia Shield verwenden, um den HDCP-Status dynamisch zu verfolgen.

* Zendesk #18358 - Das TVSDK friert beim Bitratenwechsel ein, ohne dass Synchronisierungsabbrüche auftreten.
   * Dieses Problem wurde behoben, indem eine neue Warnung hinzugefügt wurde, um die PTS-Diskontinuität zu erkennen, und die PTS-Prüfung gezwungen wurde, die Suche nach dem richtigen Segment für jeden ABR-Switch zu wiederholen.
Um das Einfrieren zu beheben, sollte der Aufruf der Methode mediaPlayer.setCustomConfiguration als Argument forcePTSCheckForABR enthalten.

* Zendesk #19038 - Kein Live-Stream auf Asus Zenpad 10.

  Dieses Problem wurde behoben, indem die Medien-Codec-Informationen vorgeladen wurden, sodass Sie die Funktion zur Laufzeit nicht abfragen.

* Die folgenden Probleme sind mit Zendesk #19038 identisch:
   * Zendesk #19483 - Das TVSDK stürzt auf der Intel Plattform ab.
   * Zendesk #19171 - Abstürze auf Asus Memo Pad 7 mit Android 5.0.

**Version 1.4.18 (1503)**

* Zendesk #3324 - Primetime Ads Reporting verfolgt keine Werbeunterbrechungen, wenn in einem VMAP kein Anzeigenmedium vorhanden ist.
Wenn eine Werbeunterbrechung leer ist, wurden die Tracking-Ereignisse für den Start der Werbeunterbrechung und für das vollständige Tracking nicht gepingt. Dieses Problem wurde behoben, indem Werbeunterbrechungs-Pings für leere Werbeunterbrechungen wie VMAP AdBreak mit einem gültigen AdSource-Knoten gesendet wurden.

* Zendesk #18229 - SetCCVisiblity(VISIBLE) wird nach dem MediaPlayer.reset() -Aufruf ignoriert. Dieses Problem wurde durch Hinzufügen von setCCVisibility(Visibility.INVISIBLE), zur Funktion reset() in der MediaPlayer-Klasse behoben.

* Zendesk #18328 - Problem mit Dropped Frames auf Amazon Fire TV-Geräten der zweiten Generation für Inhalte mit 60FPS Dieses Problem wurde behoben, indem das kodierte FPS für die Entscheidungsfindung zur Schlafzeit und mit einer besser kodierten FPS-Prognoselogik angewendet wurde.

**Version 1.4.17 (1472)**

* Zendesk #2231 - Fehler beim Abrufen des in MediaPlayerNotification nicht verfügbaren Manifests behoben Dieses Problem wurde behoben, indem der Antworttext des Manifests bei einem Parse-Fehler eingeschlossen wurde.

* Zendesk #17703 - VideoEngineView verhindert keine Screenshots während der Videowiedergabe Die setSecure-Methode ist seit API 17 verfügbar, aber da API 17 4.2, 4.2.1 und 4.2.2 abdeckt, ist nicht bekannt, welche eine Ausnahme auslösen wird oder ob sie gerätespezifisch ist. Dieses Problem wurde behoben, indem VideoEngineView.setSecure in die try catch-Klausel eingeschlossen wurde.

* Zendesk #17919 - Content Suchen verursacht Heartbeat-Fehler Ein Fehler bezüglich der Position der Eingabedaten wurde als Ergebnis des Heartbeat-Aufrufs erzeugt, der beim Start der Suche nach dem Pre-Roll generiert wurde. Dieses Problem wurde behoben.

**1.4.16 a** (1454a)

* Zendesk #18215 - Manche AES-Streams können nicht geladen werden.
Dieses Problem wurde behoben, indem die Profil-DRM-Metadatengröße überprüft wurde, bevor der AES-Schlüssel geladen wurde.

**Version 1.4.16 (1454)**

* Zendesk #3875 - Tab S Abstürze während der Wiedergabe Wiederherstellen der Abhängigkeit von OKHTTP auf Auditude für CRS, da TVSDK jetzt direkt httpurlconnection anstelle von curl verwendet. Das Problem wurde durch das Löschen von Ausnahmen behoben, bevor ein anderer JNI-Aufruf durchgeführt wurde.

* Zendesk #4487 - Tracking Linear Channel of Content Das Problem wurde behoben, indem die Neuinitialisierung des Video Heartbeat Tracker während einer linearen Stream-Wiedergabesitzung ermöglicht wurde.

* Zendesk #17919 - Android - Content Suchen verursacht Heartbeat-Fehler Das Problem, dass der Heartbeat einen Fehlerstatus aufweist, wenn eine Suche in einem Kapitel auftritt, wurde behoben.

* Zendesk #18053 - Adobe Primetime stürzt beim Marshmallow ab. Das TVSDK stürzte unter Android M OS ab, wenn die TVSDK-Bibliothek Neon-Code verwendet, der die Farbkonvertierung YUV -> RGB durchführt. Das Problem wurde behoben, indem die Funktionen aktualisiert wurden, die dieses Problem verursachen, indem die Nicht-Neon-Version des Codes verwendet wurde.

* Zendesk #18072 - Android M - Application Crash Wenn Sie überprüfen, ob das Profil und die Ebene unterstützt werden, tritt beim Aufruf der MediaCodecList- und MediaCodecInfo-APIs ein Absturz auf. Das Problem wurde behoben, indem eine temporäre Bearbeitung bereitgestellt wurde, indem alle Codec-Informationen vorzeitig geladen wurden, um zu vermeiden, dass diese APIs nur dann aufgerufen werden, wenn Codec-Informationen benötigt werden.

* Zendesk #18074 - Arabische Untertitel, die nicht mit Android 6.0 auf Nexus funktionierten. Das Problem wurde durch die Unterstützung von CTS-Schriftarten für Android behoben.

**Aktualisierung der Version 1.4.15 (1438)**

* Zendesk #17437 - Lange Verzögerung beim Start von VOD-Inhalten mit einigen AES-Streams.
Um dieses Problem zu beheben, laden Sie bei mehreren im Manifest aufgelisteten Schlüsseln alle AES-Schlüssel parallel herunter.

**Version 1.4.15 (1435)**

* Zendesk #4278 - Glicks auf Android legen die Top-Boxen fest, wenn sich die adaptive Bitrate (ABR) ändert.
Die Lösung bestand darin, Unterstützung für nahtlosen ABR-Switch mit dem neuesten Android-Medien-Codec hinzuzufügen.

* Zendesk #17063 - Der Aufruf von mediaPlayer.reset() verursacht einen Fehler beim Zurücksetzen der Video-Engine.
Die Fehlerbehebung bestand darin, den ursprünglichen MediaErrorCode aus VideoEngineExceptions beim Senden von ErrorEvents einzuschließen.

* Zendesk #17130 - Eine kurze, aber merkliche Pause bei der Änderung der Bitrate auf FireTV.
(Wie #4278 oben) Die Fehlerbehebung bestand darin, Unterstützung für nahtlosen ABR-Switch mit dem neuesten Android-Medien-Codec hinzuzufügen.

* Zendesk #17666 - Zusätzliche Anzeigenmarkierungen, unerwartete oder keine Anzeigen beim Fortsetzen von Inhalten.
Die Korrektur war ein Problem bei prepareToPlay bei Video-on-Demand (VOD)-Inhalten. Die erste Suche wird zur lokalen Zeit statt zur virtuellen Zeit durchgeführt.

* Zendesk #17437 - Lange Verzögerung beim Start von VOD-Inhalten mit einigen AES-Streams.
Die Korrektur bestand darin, alle AES-Schlüssel parallel herunterzuladen, wenn mehrere Schlüssel im Manifest aufgelistet sind.

* Zendesk #17851 - Android TV - Black Frame während ABR Die Fehlerbehebung bestand darin, KEY_MAX_WIDTH und KEY_MAX_HEIGHT anzugeben, um die adaptive Wiedergabe zu aktivieren.

**Version 1.4.14 (1415)**

* Zendesk #3875 - Tab S stürzt während der Wiedergabe ab.
Um den Absturz zu verhindern, war eine zusätzliche Fehlerbehebung erforderlich.

* Zendesk #17245 - Fallback auf Android TV funktioniert nicht.
Es wurde ein zusätzliches Problem behoben, bei dem die Wiedergabe hängt, wenn das Fallback aktiviert ist, und die VMAP-Antwort eine leere Werbeunterbrechung aufweist.

**Version 1.4.14 (1412)**

* Zendesk #17245 - Fallback auf Android TV funktioniert nicht.
Eine Beschränkung für die Deaktivierung der kreativen Neuverpackung von Fallback-Anzeigen wurde entfernt.

**Version 1.4.13 (1388)**

* Zendesk #3502 - HLS Client-basierte Failover-Unterstützung während einer Werbeunterbrechung Allow Failover auf das Haupt-Manifest bei Aktualisierung des Live-Profilfehlers tritt während der Werbeunterbrechung auf.

* Zendesk #3875 - Tab S Abstürze während der Wiedergabe Um den Konflikt zwischen HttpUrlConnection und cURLm zu beheben, verwenden Sie eine Bibliothek eines Drittanbieters.

* Zendesk #4450 - Problem beim Festlegen benutzerdefinierter Metadaten für eine einzelne Platzierung in einem Content Resolver Fügen Sie den Opportunity-Einstellungen einen Setter hinzu.

**Version 1.4.12 (1388)**

* Zendesk #2751 - CSAI und CRS | Verbesserung: Behandeln Sie dynamische Elemente in bestimmten Mediendatei-URLs.
Der Creative Repackaging Service wurde aktualisiert, um Anzeigen mit dynamischen kreativen URLs ordnungsgemäß zu verarbeiten.

* Zendesk #3965 - Wenn Sie von der Trickplay-Wiedergabe zurück zur normalen Wiedergabe wechseln, wird die Wiedergabe ein wenig vorwärts gesprungen, bevor Sie die Wiedergabe starten.
   * Die Korrektur beinhaltet TVSDK, das die Zeit vor der Ratenänderung zurückgibt, bis alle Variablen aktualisiert wurden, anstatt zu versuchen, die GetStreamTime zu berechnen.
   * Es wurde ein Absturz behoben, der auftrat, wenn die Geschwindigkeit der Trick-Wiedergabe am Ende des Streams geändert wurde.
   * Die aktuelle Zeitberechnung während der Trickwiedergabe wurde korrigiert.

* Zendesk #3978 - Trickplay bei 8x und 16x häufig gefriert.
   * Wählen Sie immer das Trick Play-Profil mit der niedrigsten Bitrate aus, um eine konstante Pufferung zu vermeiden.
   * Erhöhen Sie das Bildintervall für das Überspringen, um eine hohe Trick-Play-Rate zu erzielen.
   * Behebung eines Fehlers, bei dem der Puffer nach Erreichen der Ziellänge während der Trickwiedergabe weiter wächst.

* Zendesk #3992 - Zusätzliche Trickplay-Geschwindigkeiten.
TrickPlay wurde aktualisiert, um höhere Raten als 16x zu akzeptieren. +/- 32, +/-64 und +/-128 sind nun auch zulässig.

* Zendesk #4007 - Interpretieren des GEOB-Objekts als Teil der Timeline-Metadaten (Android &amp; Web).
setByteArray- und getByteArray-API hinzugefügt.

* PTPLAY-7301 - Sofort bei Start am Random Access Point.
&quot;Instant On&quot;wurde aktualisiert, um einen Startpunkt ungleich null zu ermöglichen.

**Version 1.4.11 (1363)**

* Zendesk #2076 - Häufiger Stottern beim Abspielen von Videos auf Motorola Xoom mit Android 4.0.3 Hinzugefügt Geräte zur Zulassungsliste, um zu verhindern, dass sie versuchen, High-Profil-Inhalte abzuspielen.

* Zendesk #2197 - `[Ads]` Versand von Tracking-Anzeigenfehlern OperationFailedEvent mit Warnhinweis.

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` Nicht befülltes Makro
   * Fehler-Code 400 wird angezeigt, wenn Inline-Werbung schlechte Kreativinhalte aufweist.
   * `[ERRORCODE]` Makro wird URL-kodiert

**Version 1.4.10 (1354)**

* Zendesk #2941 - Live-Assets weisen im suchbaren Bereich keinen &quot;0&quot;auf. Zuvor war bei der Suche nach dem Anfang eines Live-Streams ein 3-Segment-Puffer vorhanden. Jetzt ist es möglich, bis zum Anfang eines Live-Streams zu suchen (d. h. bis zum Anfang des ersten Segments).

* Zendesk #3169 - Update Reference Player with Adobe Analytics integration Der Referenz-Player wurde mit der Adobe Analytics-Bibliothek als Beispielimplantation aktualisiert.
* Zendesk #3299 - Unexplainable trick play conduct
   * Es wurde ein Fehler behoben, durch den die Rückkehr zum Wiedergabestatus nach dem Anhalten der Trick-Wiedergabe mehrere Sekunden dauern konnte (manchmal 25+ Sekunden).
   * Es wurde ein Fehler behoben, durch den der aufrufende Trick zum zweiten Mal auf demselben Medium wiedergegeben wurde und der Stream zum aktuellen Zeitpunkt einfrieren konnte.
* Zendesk #3433 - Android und Flash - Probleme mit Untertiteln

GetLine für WebVTT hat einen &lt;cr>&lt;lf> angepasste Länge für ein Paket; die letzte Beschriftung könnte Zeichen aus vorherigen Beschriftungen enthalten.

* PTPLAY-6243 - Erweiterter Referenz-Player zum Erfassen von Debugging-Informationen

Die Beispiel-Referenzplayer für Android wurden um eine Option erweitert, um Debug-Protokolle zu aktivieren und die Ergebnisse per E-Mail zu versenden. Diese Option befindet sich im Menü Protokoll des Referenz-Players.

**Version 1.4.9 (1332)**

* Zendesk #2649 - Buffer Complete tritt auf, bevor der erste Puffer voll ist

Nach einer Suche ist dies der Fall, wenn die Video-Engine den Status auf &quot;PLAYING&quot;setzt, bevor der Video-Moderator zur Wiedergabe bereit ist. Tritt auf, wenn der Pufferstatus vor der Suche hoch ist. Fehlerbehebung durch Benachrichtigung der Video-Engine über niedrigen Pufferstatus. Bei einem niedrigen Pufferstatus der Video-Engine bewirkt der Aufruf von &quot;Abspielen&quot;eine Statusänderung zu &quot;PUFFERING&quot;anstelle von &quot;PLAYING&quot;. Die Wiedergabe wird fortgesetzt, wenn sich der Status in &quot;PLAYING&quot;ändert.

* Zendesk #2846 - Enhancement request: Ermöglicht das Festlegen einer anderen Benutzer-Agent-Zeichenfolge für Aufrufe, die von der Auditude-Bibliothek getätigt werden

Eine neue API wurde hinzugefügt, um den Benutzeragenten für anzeigenbezogene Aufrufe festzulegen: auditudeSettings.setUserAgent(&quot;user/agent&quot;). Wenn kein Benutzeragent festgelegt ist, wird die Standardeinstellung verwendet. Dies betrifft nur den Benutzeragenten für anzeigenbezogene Aufrufe. Der Benutzeragent für Medienaufrufe bleibt unverändert und lautet &quot;Adobe Primetime+&quot;.&lt;default useragent=&quot;&quot;>.

**Version 1.4.8 (1324)**

* Zendesk #1218 - 106000.33 Fehler mit lokalem ... Wenn das Laden des Manifests in FragmentierterHTTPStreamer::ThreadParseManifest() fehlschlägt, überprüfen Sie, ob die URL-Domäne localhost ist. Ändern Sie in diesem Fall die Domäne auf 127.0.0.1 und rufen Sie ThreadParseManifest auf.
* Zendesk #3072 - Automatischer Wechsel zu niedrigeren Bitraten. Die Berechnung der Pufferlänge wurde geändert, um die PTS-Nutzlast auf null zu überspringen.
* Zendesk #3168 - WebVTT-Untertitel werden nur für die ersten 10 Sekunden angezeigt.
* Zendesk #3193 - Request for a Profile change API in TVSDK, PlaybackEventListener.onProfileChanged() wurde hinzugefügt.

**Version 1.4.7 (1311)**

* Zendesk #2197 - Tracking von Anzeigenfehlern. Benachrichtigung hinzugefügt, dass Asset-Manifest nicht geladen werden konnte
* Zendesk #2575 - PSDK ignoriert benutzerdefinierte MARK-In-Stream-Anzeige vor Video
* Zendesk #2719 - Win Death mit Auditude-Anzeigen, festes Beacon-Tracking bei Umleitung zur relativen URL im auditude-Plugin
* Zendesk #2760 - DISCONTINUITY-Tag wird während des TrickPlay-Modus ignoriert
* Zendesk #2805 - Player-Absturz am Anfang der Wiedergabe, dieselbe Fehlerbehebung wie Zendesk #2719
* Zendesk #2817 - Android-Player - Der Player hängt manchmal und stoppt die Wiedergabe, behoben durch Erweiterung der Dekodierungspuffer von 2,0 auf 3,0 Sekunden
* Zendesk #2839 - Unterstützt Adobe Primetime PSDK ARMv8-Chipsätze?, wurde eine Fehlerbehebung für einen Absturz auf Galaxy S6 hinzugefügt.
* Zendesk #2885 - Auditude Absturz-Wiedergabe, dieselbe Fehlerbehebung wie Zendesk #2719
* Zendesk #2895 - Live-HLS-Fehler konsistent nach 10 Minuten Wiedergabe
* Zendesk #2925 - Feedback zum Android-Entwicklungs-Build (1.4.5), auf bestimmten Geräten, wenn wir das Paket in die Eingangs-Warteschlange einreihen, wenn das PTS negativ ist, wird der Decoder in einen seltsamen Zustand versetzt, dass wir für zukünftige Pakete immer ein negatives Ausgabe-PTS erhalten. Durch die Korrektur wird der PTS-Eingabefeld auf null gesetzt, wenn dies negativ ist, um dieses Problem zu vermeiden.
* PTPLAY-4645 - Deaktivieren Sie die RC4-Verschlüsselungsunterstützung in openssl. Es gibt bekannte Exploits für RC4. Wenn also versucht wird, eine Verbindung mit einem Server herzustellen, der nur RC4 unterstützt, schlägt dies fehl.

**Version 1.4.6 (1282)**

* Zendesk #2192 - Die Bitrate sinkt nicht immer unter schlechten Netzwerkbedingungen, was durch die Entfernung der schnellen Switch-Implementierung behoben wird.
* Zendesk #2631 - Arabische Untertitel unter Android: Text in mehreren Zeilen erscheint abgeschnitten, durch Anpassung der Schriftgröße für arabische Schriftarten festgelegt.
* Zendesk #2844 - Pufferung auf Hinweis 4 und die Zeit für den Fragmentdownload ist nicht genau.

Dieses Problem wurde behoben, indem Latenzzeiten zwischen Downloads von Videosegmenten zur Bandbreitenberechnung hinzugefügt wurden und die Logik für die Download-Zeit die vollständige Anfragezyklusdauer verwendet hat.

* Zendesk #2908 - Arabische Untertitel, die nicht mit Nexust 5, 6 und 7 funktionieren, wurden behoben, indem 2 weitere Fallback-Schriftarten für arabische Skripte hinzugefügt wurden.
* PTPLAY-4627 - Aktualisierung von Nielson appsdk auf Version 1.2.3.7
* PTPLAY-5084 - Unterstützung für Update-Failover des Live Master-Manifests

**Version 1.4.5 (1248)**

* Zendesk #1757 - Nur abgespielte Audio- oder Player stürzt bei einem Video-Bitratenprofil ab, Absturz Nexus 4 und Nexus 7 wurde behoben
* Zendesk #2072 - TimedMetadata for AdEvent enthält nicht die vollständige URL nur &quot;http&quot;
* Zendesk #2192 - Bitrate bei schlechten Netzwerkbedingungen nicht immer niedriger
* Zendesk #2256 - Zugriff auf Master-Playlist, aktualisiertes PSDK zum Senden von timedMetadata-Ereignissen für abonnierte Tags auf der Master-Playlist.
* Zendesk #2269 - Zwei verschiedene Untertitelsprachen werden gleichzeitig mit WebVTT auf dem Bildschirm angezeigt
* Zendesk #2417 - Player versucht, Untertitel vor dem Wiedergabebeginn herunterzuladen, verwendet WebVTT die falsche Segmentnummernvariable für die Segmentnummerübereinstimmung. Fehler wurden nur für Medien angezeigt, bei denen Segmentindizes bei null lagen.
* Zendesk #2470 - PSDK kehrt nicht aus dem AUSGESETZTEN Zustand zurück, wenn eine Bitratenänderung nach der Aussetzung erfolgt. In einer speziellen Situation, in der die intelligente Suche von RestoreGPUResource (Player aus dem Aussetzen wiederherstellen) aufgerufen und der Stream-Switch zuvor erkannt wurde, kann die intelligente Suche nicht abgeschlossen werden und zu konstanter Pufferung führen.
* Zendesk #2451 - Verdeckte Untertitelung &quot;bottom inset&quot;, Parameter &quot;bottomInset&quot;zum Untertitelcode hinzugefügt
* Zendesk #2480 - Deaktivieren der HTTP 302-Umleitungsoptimierung, Unterstützung für Einstellung der useRedirectUrl-Eigenschaft hinzugefügt
* Zendesk #2486 - Beacons von Drittanbietern
* Zendesk #2547 - Arabische Untertitel: Text sollte rechtsbündig ausgerichtet werden

**Version 1.4.4 (1195)**

* Zendesk #1158 - Wiedergabe schlägt bei Huawei Valiant fehl (Y301A1)
* Zendesk #1709 - Falsche Mediengröße und gestrecktes Video
* Zendesk #1757 - Nur Audio abgespielt, nachdem Profil zwischen Streams mit identischen SPA/PPS-Daten gewechselt hat
* Zendesk #2095 - HTTP-307-Status (Weiterleitung) bewirkt, dass der Adobe-Player die Wiedergabe stoppt
* Zendesk #2126 - Missing TimedMetaData event for last ADEVENT, Subscribed tags which after the last segment were not reporting to PSDK from AVE
* Zendesk #2227 - Lockups in VideoEngine nativeReset und nativePause
* Fehler #3921755 - Aktualisierung der OpenSSL-Bibliothek auf Version 1.0.1L

**Version 1.4.3 (1173)**

* Zendesk #1591 - RENDITION_M3U8_ERROR
* Zendesk #1870 - Geschlossene Beschriftung Ein- und Ausschalten
* PTPLAY-1818 - Wiedergabe des Tricks stoppt an der Anzeige, anstatt sie erneut durchzuführen
* PTPLAY-2736 - Eine zuvor angezeigte WebVTT-Beschriftung wird auf dem Bildschirm angezeigt, wenn die Wiedergabe eines Streams mit WebVTT-Beschriftung abgeschlossen ist
* PTPLAY-3773 - Eine Mid-Roll-Anzeige wird nicht wiedergegeben, wenn die Stream-Wiedergabe nach der Anzeigenposition gestartet wird

**Version 1.4.2**

* Zendesk #1561 - HLS Client-basierte Failover-Unterstützung in der Primetime. Verwendet die Programmdatumszeit, um Failover zu beheben
* Zendesk #1590 - LoadInfo.MediaDuration is always 0 (not fixed for audio-only)
* Zendesk #1626 - Potenzielles Speicherleck im Player. Kein aktueller Speicherleck, Problem mit NotificationHistory, das die letzten 1000 Benachrichtigungen speichert. Dieses Problem wurde auf 100 reduziert.
* Zendesk #2192 - Bitrate bei schlechten Netzwerkbedingungen nicht immer niedriger

**Version 1.4.1 (1121)**

* Zendesk #1951 - Lockup in VideoEngine.nativeReset() auf 4.0.x-Geräten
* Zendesk #2064 - Nativer Absturz SIGSEGV auf bestimmten intel-basierten Android-Geräten
* Zendesk #2075 - Lockup in VideoEngine.nativeReleaseGPUResource auf 4.0.x-Geräten Hinweis: Dieser Build ist &#42;&#42;&#42;erforderlich&#42;&#42;&#42; zur Unterstützung von Android 5.0 (Lollipop)
* Zendesk #1513 - Unterstützung für Android Lollipop
* Zendesk #1709 - Falsche Mediengröße und gestrecktes Video
* Zendesk #1871 - WebVTT-Untertitel verschwinden gelegentlich und erscheinen dann wieder, wenn ein Livestream mit WebVTT-Untertiteln angezeigt wird
* Zendesk #1996 - In PSDK 1.4.0 werden keine Zeitleisten-Markierungen angezeigt
* Zendesk #2046 - Absturz mit PSDK 1.4.1.1113, Absturz für Live-Streams behoben, wenn keine Anzeigen von der Zielgruppe zurückgegeben werden
* Fehler #3769657 - Aktualisierung der Version von curl auf 7.38.0
* PTPLAY-1575 - Wenn die ABR-Wiedergabe nur mit dem Audio-Stream beginnt und dann zu Audio-/Video-Stream wechselt, wird das Video nie gerendert, während die Audiowiedergabe fortgesetzt wird
* PTPLAY-2499 - Aktualisierung auf OpenSSL auf Version 1.0.1j, um aktuelle Schwachstellen zu beheben
* PTPLAY-2632 - Video wird nach Abschluss der Mid-Roll-Anzeige unter Android Lollipop nicht wiederhergestellt
* PTPLAY-2678 - Video-Stalls während Live-Lebenserwartungstests unter Android Lollipop

**Version 1.4.0**

* Zendesk #1024 - Funktion zum Entfernen von Anzeigen aus dem Stream über Manifest
* Zendesk #1293 - Problem mit der Auswahl der verdeckten Untertitel.
* Zendesk #1590 - LoadInfo.MediaDuration ist immer 0, mediaDuration zeigt jetzt den richtigen Wert an.
* Zendesk #1629 - player/app stürzt am Ende der Anzeigenwiedergabe auf Galaxy S4 ab
* Zendesk #1674 - ClosedCaption Nicht angezeigt, korrekte 708-Beschriftungsanzeige, wenn 0x03-ETX-Codes fehlen.
* PTPLAY-2157 - Standard-Stile für verdeckte Untertitel wurden von Gettern zurückgegeben, selbst wenn nach dem Festlegen und Überprüfen eines anderen Stils im Stream visuell andere Stile festgelegt wurden. Die Eigenschaften des Stils &quot;Geschlossene Beschriftung&quot;zeigen jetzt den Wert an, auf den sie festgelegt wurden.

## Bekannte Probleme in Version 1.4 {#known-issues-in}

**Version 1.4.31**

* PTPLAY-16803 - Geschlossene Beschriftung funktioniert nicht mit Audioinhalten, da das Beschriftungssystem Video benötigt, um zu funktionieren. Ohne Video gibt es keine Viewport-Dimension und ohne Viewport-Dimension können keine Grafiken für Beschriftungen angezeigt werden.
* PTPLAY-1634 - Das gleiche abonnierte Tag hat in verschiedenen Live-Fenstern unterschiedliche Zeitstempel. Wenn ein Live-Fenster verschoben wird, sollte dasselbe Tag in ihnen dieselben Zeitstempel enthalten. Manchmal haben jedoch auch dieselben Tags unterschiedliche Zeitstempel.
* PTPLAY-3197 - Absturz mit Signal 11 SIGSEGV-Fehler auf Acer Iconia-Gerät nach ~ 1 Stunde kontinuierlicher Wiedergabe
* PTPLAY-3310 - Mit etwas geringerem Bitratenaudio wird das Audio auf Acer Iconia choppy/stoty
* PTPLAY-3355 - WIN DEATH-Absturz auf Motorola Xoom mit 4.0.x nach ~ 1 Stunde kontinuierlicher Wiedergabe.
* PTPLAY-3557 - Das Zurücksetzen bei einer Werbeunterbrechung führt dazu, dass der Stream abgeschlossen wird
* PTPLAY-7079 - Wiedergabe-Fenster auf Android-Client funktioniert nicht mit Secure Stopp/Hard Stopp
* Fehler 3760144 - Die Auflösung kann sich ändern oder zu pulsieren scheinen, wenn der Stream auf einigen Geräten wie Kindle Fire 7 und Samsung Galaxy Nexus angehalten wird. Nur bei sorgfältiger Überprüfung zu beobachten
* Fehler #3761170 - searchToLocal in Live mit Anzeigen kann nicht wieder in Anzeigeninhalte suchen. Es empfiehlt sich, die currentTime-APIs für Live-Streams zu verwenden
* Fehler 3763370 - Live-Streams mit Anzeigen zeigen gelegentlich zwei Anzeigenmarkierungen nahe beieinander, wenn nur eine vorhanden sein sollte. Diese Anzeigenmarkierungen stellen dieselbe Anzeige dar und es wird nur eine wiedergegeben.
* Fehler 3763373 - Die Anzeigenmarkierung wird möglicherweise kurz ausgeblendet, wenn nach einer Anzeige in VOD-Streams gesucht wird. Die Anzeigenmarke wird wiederhergestellt und es gibt keine weiteren negativen Auswirkungen auf die Zeitleiste
* Bei einigen Geräten treten bekannte Wiedergabeprobleme auf. Siehe [Bekannte Geräteprobleme in Version 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Referenzimplementierung - Trick Play ist nicht in der Beispielanwendung implementiert
* Auf einigen Android TV-Geräten wird ein schwarzer Frame angezeigt, da der Decoder an den folgenden Übergangsstellen zurückgesetzt wird:
   * in den und aus dem Trickplay-Modus
   * Wechseln zwischen Audio-Spuren mit verspäteter Bindung
   * von einer Anzeige zum Hauptinhalt

**Version 1.4.23**

* Geschlossene Beschriftung funktioniert nicht mit Nur-Audio-Inhalten, da das Beschriftungssystem Video benötigt, um zu funktionieren. Ohne Video gibt es keine Viewport-Dimension und ohne Viewport-Dimension können Sie keine Grafiken für Beschriftungen anzeigen.
* Ab Version 1.4.23 unterstützt das TVSDK Gingerbread OS 2.3 nicht mehr. Dies liegt daran, dass das TVSDK die folgenden privaten Android-Bibliotheken verwendet hat, um Hardware-Informationen über Geräte mit Gingerbread OS zu erfassen:

   * `libstagefright.so`
   * `libcutils.so`

In der Android N-Version hat Google den Zugriff auf diese privaten Bibliotheken entfernt. Das Gingerbread-Betriebssystem macht derzeit weniger als 1 % des Android OS-Marktanteils weltweit aus. Nach Version 1.4.23 wird das Gingerbread-Betriebssystem daher nicht mehr vom TVSDK unterstützt.
Wenn Sie Version 1.4.23 (einschließlich Unterstützung für Android N) oder höher verwenden:
* Aktualisieren Sie Ihre Apps, um die Version 11 von minSdkVersion zu verwenden.
* Wenn Ihr Endbenutzer OS 2.3 ausführt, ist die SDK-Version niedriger als die minSdkVersion der Anwendung. Das System bricht die Installation oder Aktualisierung der Anwendung ab.
* Wenn Ihr Endbenutzer eine Version ausführt, die höher als OS 2.3 ist, wird die Anwendung ordnungsgemäß installiert.

Wenn Sie die minSdkVersion aktualisieren:

* Wenn Ihr Endbenutzer OS 2.3 ausführt, wird die Anwendung installiert, die Wiedergabe funktioniert jedoch nicht.
Dies gilt sowohl für die Aktualisierung als auch für die Neuinstallation.
* Wenn der Endbenutzer ein System über OS 2.3 ausführt, wird die App ordnungsgemäß installiert und der Inhalt wird korrekt wiedergegeben.

**Version 1.4.22**

* Der frühe Ausstieg aus Anzeigen funktioniert bei einigen der Mid-Roll-Anzeigen nicht, wenn die Spllice-out- und Spleice-in-Tags zu nahe beieinander liegen.

**Version 1.4.2**

* Das Zurücksetzen bei einer Werbeunterbrechung führt dazu, dass der Stream abgeschlossen wird.

Der Media Player sendet MediaPlayerState.Complete während des &quot;Trick Play&quot;-Rückspaltungsvorgangs fälschlicherweise, wenn er eine Anzeigengrenze erreicht. Der Player sollte dieses Ereignis im Modus &quot;Trick Play&quot;ignorieren, da das SDK andernfalls den Status korrekt verarbeitet.

**Version 1.4.0 (1086)**

* PTPLAY-1634 - Das gleiche abonnierte Tag hat in verschiedenen Live-Fenstern unterschiedliche Zeitstempel. Wenn Live-Fenster verschoben werden, sollte dasselbe Tag in jedem von ihnen über dieselben Zeitstempel verfügen. Manchmal haben jedoch auch dieselben Tags unterschiedliche Zeitstempel.
* PTPLAY-2541 - COMPONENT_CREATION_FAILURE wird manchmal nach mehreren Switches zum/vom alternativen Stream in Blackouts angezeigt
* Fehler 3726865 - Wenn ein MultiBitrate-LBA-Stream aus einem reinen Audio-Stream beginnt, wird das Video nicht angezeigt, wenn zu einem Audio-/Video-Stream gewechselt wird. Ab einem Audio-/Video-Stream wird dieses Problem nicht angezeigt und kann erfolgreich zwischen Audio- und Audio-/Videostreams wechseln
* Fehler 3760144 - Die Auflösung kann sich ändern oder zu pulsieren scheinen, wenn ein Stream auf einigen Geräten wie Kindle Fire 7 und Samsung Galaxy Nexus angehalten wird. Nur bei sorgfältiger Überprüfung zu beobachten
* Fehler #3761170 - searchToLocal in Live mit Anzeigen kann nicht wieder in Anzeigeninhalte suchen. Es ist am besten, die currentTime-APIs für Live-Streams zu verwenden
* Fehler 3763370 - Live-Streams mit Anzeigen zeigen gelegentlich zwei Anzeigenmarkierungen nahe beieinander, wenn nur eine vorhanden sein sollte. Diese Anzeigenmarkierungen stellen dieselbe Anzeige dar und es wird nur eine wiedergegeben.
* Fehler 3763373 - Die Anzeigenmarkierung wird möglicherweise kurz ausgeblendet, wenn nach einer Anzeige in VOD-Streams gesucht wird. Die Anzeigenmarke wird wiederhergestellt und es gibt keine weiteren negativen Auswirkungen auf die Zeitleiste
* Bei einigen Geräten treten bekannte Wiedergabeprobleme auf. Weitere Informationen finden Sie unter [Bekannte Geräteprobleme in Version 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Referenzimplementierung - Trick Play wird nicht in der Beispielanwendung implementiert.

## Bekannte Geräteprobleme in Version 1.4 {#known-device-issues-in}

| Gerät | Chipsatz | Problem | Ursache | Workaround |
|--- |--- |--- |--- |--- |
| Drop X | TI OMAP3 | ABR-Verzögerung wird erwartet, da der Decoder neu gestartet wird. |  |  |
| HTC-Design (unterscheidet sich von HTC Design HD) | QSD8250 | Video kann nicht wiedergegeben werden. Gibt den Fehler VIDEO_PROFILE_NOT_SUPPORTED zurück. | Das Design stellt keinen geeigneten HW-Decoder bereit. Es gibt den SW-Decoder von Stagefright. | Gerät neu starten. |
| HTC EVO 4G | QSD8650 | Kein HW-Decoder. | Qualcomm hat keinen HW-Decoder. | Upgrade auf Android 4.x. |
| Kindle FireSystem Version 6.0 | TI OMAP4 | Keine Wiedergabe von HLS-Streams. Video auf AIR funktioniert nicht. |  | Upgrade auf Systemversion 6.3. |
| Kindle Fire HD | TI OMAP4 | Kann in einen Status gelangen, in dem Video nicht wiedergegeben werden kann. Gibt die Fehler VIDEO_PROFILE_NOT_SUPPORTED und UNRECOVERABLE_ERROR zurück. | Der HW-Decoder wechselt in einen nicht wiederherstellbaren Status, wenn die App den HW-Decoder nicht vollständig herunterfährt, z. B. nach einem Absturz. Gilt auch für native Apps auf dem Gerät. | Starten Sie das Gerät neu. |
| Kindle Fire HD 8.9 | Snapdragon 800 | AVE stürzt nach mehreren ABR-Switches ab. |  |  |
| Motorola Atrix | Tegra2 | Generelle Leistungsprobleme mit AVE im Gegensatz zu AIR. Audio/Video wird nicht synchronisiert, die Videowiedergabe friert nach der Wiedergabe zwischen 9 und 15 Minuten ein. Abstürze. | Möglicherweise in Zusammenhang mit openGLES , das wir in AIR aktivieren. In der Untersuchung. |  |
| Nexus 7 (2. Generation) | S4Pro APQ8064 (Qualcomm) | Das Gerät hängt, wenn ein Film länger als 30 Minuten angehalten wird. | Geräteproblem, das an Google gemeldet wurde. | Die App sollte eine Zeitüberschreitung aufweisen, damit kein langer Pausenstatus zugelassen wird. |
| Nexus S (GB) | Hummer Vogel | Mit dem HW-Decoder können keine Videos wiedergegeben werden. | In Nexus S gibt es keinen Stagefright-basierten HW-Decoder, daher verwenden wir für Android 2.3 einen SW-Decoder. | Aktualisieren Sie auf ICS. |
| Nexus S (ICS) | Hummer Vogel | Gelegentlich flackern Videos. | Schlechte Daten können dazu führen, dass der Decoder in einen schlechten Zustand gerät. | Starten Sie das Gerät neu. |
| Nook TabletAndroid OS: 2.3 | TI OMAP 4 | Video wird nicht abgespielt und App hängt. | Stagefright wechselt in einen instabilen Status, nachdem die App einige Male ausgeführt wurde. Aufrufe von mediaplayer::QueryCodecs hängen. | Starten Sie das Gerät neu, um den Status zurückzusetzen. |
| Samsung Galaxy ACE | Qualcomm MSM7227 | Die SampleMediaPlayer-App kann nicht installiert werden. | Verwendet ARM v6 anstelle des gängigeren ARM v7-Chipsatzes. FP/AIR unterstützt dieses Gerät nicht. |  |
| Samsung Galaxy ACE2Android OS: 2.3.6 | NovaThor U 8500 | Video kann nicht wiedergegeben werden. | Dieser Chipsatz ist ein unbekannter Decoder für Android pre-ICS in AVE. |  |
| Samsung Galaxy S2 (GT-I9100) | Exynos | Die Videoleistung entspricht nicht der für dieses Gerät. | Der HW-Decoder gibt dekodierte Frames mit dem falschen PTS zurück. Sieht so aus, als nutzt der Decoder die Dekodierungszeit anstelle der Präsentationszeit. |  |
| Samsung Galaxy S2 GAndroid OS: 2.3.6 | TI OMAP4 | Abstürze beim Starten des Videos. |  | Aktualisieren Sie auf Android 2.3.7 oder 4.x. |
| Samsung Galaxy S3 (I747) | Qualcomm MSM8960 | Gelegentlich friert das Video ein, und nur die Audiowiedergabe wird dann nicht mehr responsiv. |  |  |
| Samsung Galaxy S3 I747M | SAMSUNG_M2ATT | Video friert ein. | Untersuchung. |  |
| Samsung Galaxy Tab 1 v10.1 | Tegra 2 | Die MBR-Transition kann bis zu drei Sekunden dauern. | Als Behebung für MBR-Abstürze starten wir den Decoder für jeden Stream-Switch neu, was bis zu drei Sekunden dauern kann. |  |
| Samsung Galaxy |  | Die SampleMediaPlayer-App kann nicht installiert werden. | Verwendet ARM v6 anstelle des gängigeren ARM v7-Chipsatzes. FP/AIR unterstützt dieses Gerät nicht. |  |
| Xoom | Tegra | Einige Frames werden zum Wechseln entfernt. Der Decoder wird nicht neu gestartet. | OMXAL-Beschränkung. |  |

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
