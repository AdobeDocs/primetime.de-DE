---
title: TVSDK 1.4 für HLS-Versionshinweise für Desktop
seo-title: TVSDK 1.4 für HLS-Versionshinweise für Desktop
description: TVSDK for Desktop HLS Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in TVSDK DHLS.
seo-description: TVSDK for Desktop HLS Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in TVSDK DHLS.
uuid: 84da27b7-299b-478d-88f5-ef943f0a8321
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: e4437a26-9454-4da1-ae87-0fce664aac3d
translation-type: tm+mt
source-git-commit: a94150abc2afff4af24ee83573e73124f8b3260a

---


# TVSDK 1.4 für HLS-Versionshinweise für Desktop {#tvsdk-for-desktop-hls-release-notes}

TVSDK for Desktop HLS Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in TVSDK DHLS.

## Neue Funktionen {#new-features}

**1.4.31**

* **Multi-CDN-Unterstützung für CRS-Anzeigen**

   * Standardmäßig werden alle transkodierten Assets auf dem Adobe-eigenen CDN auf Akamai gehostet. Mit der aktuellen Version bietet Adobe Creative Repackage Service (CRS) die Möglichkeit, die transkodierten Kreativelemente wie vom Kunden angegeben in mehrere CDNs hochzuladen.
   * TVSDK werden neue APIs hinzugefügt, um die Angabe der endgültigen kreativen CRS-URL zu ermöglichen, wenn die Standard-URL nicht verwendet wird. Informationen zur Verwendung dieser neuen APIs finden Sie in der Dokumentation.

### Neue Funktionen in früheren Versionen {#new-features-previous}

**1.4.30**

* **Rechnungsmetriken**

Um Kunden, die nur für die von ihnen verwendeten Artikel bezahlen möchten, anstatt für einen festen Preis unabhängig von der tatsächlichen Verwendung zu bezahlen, sammelt Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel die Kunden bezahlen müssen.

**1.4.24**

* **Persistente Netzwerkverbindung**

Wichtig: Sie müssen mindestens Adobe Flash Player Version 22 oder höher installiert haben.
Persistente Netzwerkverbindungen erstellen und speichern eine interne Liste von Netzwerkverbindungen, die für mehrere Anforderungen wiederverwendet werden können, anstatt für jede Netzwerkanforderung eine neue Verbindung zu öffnen. Persistente Netzwerkverbindungen sollten die Effizienz erhöhen und die Latenz im Netzwerkcode verringern.

In dieser Version wird diese Funktion in Apple Safari und Mozilla Firefox auf einem Mac nicht unterstützt.

**1.4.19**

* Stream-Integritätsunterstützung für VPAID-Anzeigen.
* Aktiviert die Option für die Registerkarte &quot;Ton&quot;im Flash Player FP 20.0.0.267 für Firefox 42 und höher, indem das Problem beim Hängen behoben wird.

**1.4.18**

* Primetime Desktop HLS TVSDK unterstützt jetzt VPAID 2.0 Lineare SWF-Kreative, um eine umfassende interaktive In-Stream-Anzeigenerfahrung zu ermöglichen.

**1.4.10**

* **Ad Fallback, Dissy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103)** Bei VAST-Anzeigen (Kreativelemente) mit aktivierter Ausweichregel behandelt TVSDK eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht stattdessen, Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Weitere Informationen finden Sie unter [Ad-Fallback für VAST- und VMAP-Anzeigen](../programming/tvsdk-1.4-for-android/ad-insertion/ad-fallback/android-1.4-ad-fallback.md).

**1.4.8**

* **Video Heartbeats Library (VHL) aktualisiert auf Version 1.5**

   * Möglichkeit zum Senden von Metadaten mit Video-Beginn und/oder Video/Anzeige/Beginn als Kontextdaten
   * Weniger Netzwerkverkehr - Heartbeats sind durchschnittlich weniger und kleiner.

**1.4.7**

* **Unterstützung der Personalisierung vor Ort**

Unterstützung für lokale Installationen von Adobe Individualization Server, um die Individualisierungsanforderung des Kunden an einen anderen Endpunkt anzupassen.

**1.4.6**

* **Beispiel-AES-Verschlüsselung (Flash Player-Version 17.0.0.134 erforderlich)**

Die Beispiel-basierte AES-Verschlüsselung wird jetzt unterstützt.

**1.4.2**

* **Video Heartbeats Library (VHL) aktualisieren auf Version 1.4.0.1**

   * Es wurde die Möglichkeit hinzugefügt, verschiedene Anwendungsfälle für Analysen - von anderen SDKs oder Playern - mit Adobe Analytics Video Essentials zu bündeln.
   * Die Anzeigenverfolgung wurde optimiert, indem die Methoden trackAdBreakStart und trackAdBreakComplete entfernt wurden. Die Werbeunterbrechung wird aus den trackAdStart- und trackAdComplete-Methodenaufrufen abgeleitet.
   * Die Eigenschaft playhead ist bei der Verfolgung von Anzeigen nicht mehr erforderlich.

**1.4.0**

* **Blackout-Signalisierung mit alternativem Content-Ersatz** Als Teil des 1.4 TVSDK-Updates unterstützt das TVSDK jetzt auch das Eingehen und Zurückkehren von regionalen Blackouts gegen lineare Inhalte. Das TVSDK kann nun zwei Manifestdateien parallel, main und alternative verarbeiten, um die Blackout-Signale auch dann zu überwachen, wenn anstelle der ursprünglichen Programmierung eine alternative Programmierung angezeigt wird.

* **Entfernen/Ersetzen von C3-Anzeigen** Jetzt ist keine zusätzliche Vorarbeit erforderlich, um dynamische neue Anzeigen in Video-on-Demand-Assets (VOD) einzufügen, die aus dem C3-Fenster herauskommen. Das TVSDK bietet jetzt eine API zum Entfernen benutzerdefinierter Inhaltsbereiche und zum dynamischen Einfügen neuer Anzeigen. Diese leistungsstarke neue Funktion ist auch in Fällen nützlich, in denen während der Übertragung Live-/Lineare Inhalte erscheinen und sofort zur Verwendung als On-Demand-Inhalte heruntergezogen werden, ohne dass genügend Zeit zum &quot;Bereinigen&quot;des Assets erforderlich ist.

## Behobene Probleme {#resolved-issues}

>[!NOTE]
>
>Alle TVSDK-Kunden, die CRS verwenden, sollten auf mindestens TVSDK 1.4.32 auf iOS-, Android- und Desktop-HLS aktualisieren. Dieses Upgrade wird als Ablösung für die vorhandene App-Implementierung verwendet. Überprüfen Sie nach der Aktualisierung in einem Proxy-Tool (z. B. Charles), ob die CRS-Anforderungen für kreative URLs erfüllt sind, um sicherzustellen, dass die Version im Pfad der Version 3.1 entspricht. Beispiel:
>
>`https://adunit.cdn.auditude.com/assets/3p/v3.1/218747/94b/c1b/94bc1b964cc67e115a5a6781c7329b90_ee92607938ffff46b083121f044c2746.m3u8`

**Version 1.4.41**

* Zendesk #33777 - Localhost-Token-SWF für DHLS-Distribution-Build abgelaufen.

   Aktualisieren des localhost-Tokens für die PMP-Demo auf DHLS.

### Behobene Probleme in früheren Versionen {#resolved-issues-previous}

**Version 1.4.38** (891)

* Zendesk #30731 - TVSDK gibt nicht mehrere VPAID-Anzeigen in einer AdBreak ab.

   Korrektur der Wiedergabe mehrerer VPAID-Anzeigen in einem AdBreak.

* Zendesk #29968 - Dublette Billboard.

   Der Videoplayer kann das letzte Segment eines Zeitraums wiederholen, wenn ein ABR-Schalter eintritt. Dadurch wird manchmal das letzte Segment der Preroll wiederholt. Das wurde behoben.

**Version 1.4.35** (879)

* Zendesk #26058 - Unterstützt native VPAID-Ereignis

**Version 1.4.33** (873)

* Zendesk #21701 - Senden Sie die ursprüngliche kreative URL für 1401 CRS-Anforderung anstelle der normalisierten URL.

   Das Problem, bei dem bereits neu verpackte URLs zum Transkodieren angefordert werden, wurde behoben, wie vom CRS-Back-End gefordert.
* Zendesk #26197 - Anamorphische Komprimierung wird in der gewünschten Auflösung nicht wiederholt.

   **Hinweis**: Für dieses Problem ist Flash Player 24.0.0.194 oder höher erforderlich.

   Das Problem, bei dem fehlende Einträge in den Tabellen des Seitenverhältnisses zur Berechnung der Ausgabebreite verwendet wurden, wurde behoben.

* Zendesk #26840 - HDCP-Erkennung bei IE11 + Windows7 nach einem zweiten Versuch fehlschlägt.

   **Hinweis**: Für dieses Problem ist Flash Player 24.0.0.218 oder höher erforderlich.

   Dieses Problem wurde behoben, indem die Verarbeitung der Hauptmeldungswarteschlange von Adobe geändert wurde, um die gesamte Warteschlange zu durchlaufen, anstatt nur die erste Nachricht zu blockieren.

* Zendesk #27460 - Das neue Akamai-Konto kann eine POST-CDN-Anforderung nicht bearbeiten.

   Das neue CDN-Konto kann eine POST-CDN-Anforderung nicht bearbeiten. Dieses Problem wurde behoben, indem der Code aktualisiert wurde, damit die Anzeigenanforderung cdn.auditude.com statt POST GET lautet.
* Zendesk #27619 - Flash-Absturz unter Windows 10

   **Hinweis**: Für dieses Problem ist Flash Player 24.0.0.218 oder höher erforderlich.

   Dieses Problem wurde behoben, indem ein Fehler aufgrund langer URLs verhindert wurde.

* Zendesk #28218 - Das Tracking-Ereignis wird nicht ausgelöst, wenn der Absturz vom Wieder-Point ausgeführt wird

   Dieses Problem ist dasselbe wie in Zendesk #26592. Das Problem, bei dem Suchvorgänge zulässig waren, wenn sich der Medienplayer im Status &quot;VORBEREITT&quot;für VOD-Streams befindet, wurde behoben.

**Version 1.4.32** (867)

* Zendesk #26592 Tracking-Ereignis wird nicht ausgelöst, wenn die Wiedergabe vom Wiederaufnahmepunkt aus Beginn wird

Der Code aktualisierte das Pre-Roll-Werbeunterbrechungselement nicht, wenn der Wiederaufnahmepunkt nicht null war. Dieses Problem wurde behoben, indem Logik hinzugefügt wurde, um den Beginn zu aktualisieren, wenn die Zeitspanne nicht übereinstimmt.

* Zendesk #27022 Anzeigen werden nicht wiedergegeben, wenn ein Asset zum zweiten Mal wiedergegeben wird

Die Ausnahmen mit den Array-Methoden wurden behoben.

**Version 1.4.30** (855)

Die folgenden Probleme wurden in dieser Version für TVSDK behoben:

* Zendesk #22898 - Fehlende Untertitel sollten nicht dazu führen, dass die Wiedergabe fehlschlägt.

**Hinweis**: Für dieses Problem ist Flash Player 23.0.0.185 oder höher erforderlich.

Dieses Problem wurde behoben, indem TVSDK die Wiedergabe fortsetzen konnte, selbst wenn das Manifest WebVTT M3U8 fehlt, und eine Warnung registriert wurde.

* Zendesk #23454 - Anzeigen von Drittanbietern (VPAID) werden nicht korrekt behandelt

Dieses Problem wurde behoben, indem VPAID-Anzeigen auf der Grundlage von Inhalts-IDs und nicht auf Grundlage von Zeiträumen korrekt verarbeitet wurden.

* Zendesk #24528 - TVSDK-Nutzungsmetriken für die Rechnungsstellung.

Wichtig: Für dieses Problem ist Flash Player 23.0.0.185 oder höher erforderlich.

* Zendesk # 25432 Untertitelproblem beim Ändern der Größe des Players.

Wichtig: Für dieses Problem ist Flash Player 23.0.0.185 oder höher erforderlich.

Der Texturmap-Code für die Beschriftungsanzeige wurde so korrigiert, dass die Koordinaten während der Player-Größenänderung korrekt verarbeitet werden.

Die Video Heartbeat Library (VHL) wurde auf Version 1.5.9 aktualisiert, um die folgenden Probleme zu beheben:

* Zendesk #23730 - Bitratenmetriken sind leer

Dieses Problem wurde behoben, indem die Bitratenänderungen in VideoAnalyticsTracker verfolgt wurden.

* Es wurde eine neue API, assetDuration, zu PTVideoAnalyticsTrackingMetadata hinzugefügt, um die Asset-Dauer für Live-/Linear-Streams zu aktualisieren.

**Version 1.4.28** (848)

* Zendesk #25027 - Auditude funktioniert in 1.4.27 Desktop-Version nicht

Dieses Problem wurde behoben, indem der Code zur Prüfung von AUDITUDE_METADATA_KEY hinzugefügt und die Optionen AUDITUDE_METADATA_KEY und ADVERTISING_METADATA_KEY austauschbar gemacht wurden.

* Zendesk #24428 - Häufige Pufferung mit TVSDK bei der Wiedergabe eines DRM-HLS

Dieses Problem wurde behoben, indem berücksichtigt wurde, dass TVSDK, wenn keine Anzeigeneinrichtung eingerichtet wurde, die Verarbeitung beschleunigen kann, indem der Pre-Roll-Anzeigenspeicher- und Live-Reservierungsspeicher auf der Zeitschiene, die für die Synchronisierung der Anzeigeneinfügung vorgesehen ist, entfernt wird.

* Zendesk #24344 - Deaktivieren Sie WebVTT-Dateien, um die Beginn zu verkürzen.

**Hinweis**: Für dieses Problem ist Flash Player 23 oder höher erforderlich.

Dieses Problem wurde behoben, indem die WebVTT-Dateien nur geladen wurden, wenn Bildunterschriften angezeigt werden müssen.

* Zendesk #24994 - Untertitel werden beim Zurückkehren von Werbeunterbrechungen vom Player entfernt

**Hinweis**: Für dieses Problem ist Flash Player 23 oder höher erforderlich.

Der falsche EOC-Code führte dazu, dass die Beschriftungsanzeige verschwand. Dieses Problem wurde behoben, indem die 608 Beschriftungscodes RU2, RU3 und RU4 gezwungen wurden, die korrekte Sichtbarkeit im aktuellen aktiven Fenster zu gewährleisten.

**Version 1.4.27** (844)

* Zendesk #21554 - TVSDK-Fehlerbeacons, die nicht für application-type = video/mp4 ausgelöst werden

Dieses Problem wurde behoben, indem TVSDK die korrekten URLs zur Fehlerverfolgung für ungültige Asset-Formate ping.

* Zendesk #23402 - Unvollständige Wiedergabe der Anzeige

**Hinweis**: Für dieses Problem ist Flash Player 23 oder höher erforderlich.

Nachdem bei bestimmten Anforderungen ein 404-Fehler ausgegeben wurde, kann es zu einem Absturz kommen. Dieses Problem wurde behoben, indem sichergestellt wurde, dass die Verbindung nicht geschlossen wird, während die Antwort verarbeitet wird. Die Auflösung stellt sicher, dass die VPAID-Anzeigendateien nicht falsch gezählt werden, sodass sie beim Herunterladen nicht freigegeben werden.

* Zendesk #23621 - Retry schlägt bei 400 und 404 fehl

**Hinweis**: Für dieses Problem ist Flash Player 23 oder höher erforderlich.

Korrektur des Fehlers, der beim Wechseln zwischen verschiedenen Profilen zu einer Beschädigung der DRM-Metadaten führte.

* Zendesk #23705 - Einfrieren von Videoanzeigen bei AdStitched-Pausen

**Hinweis**: Für dieses Problem ist Flash Player 23 oder höher erforderlich.

Dieses Problem ist dasselbe wie in Zendesk #23621.

* Zendesk #23905 - Einige Werbeunterbrechungen werden bei Werbeunterbrechungen übersprungen

**Hinweis**: Für dieses Problem ist Flash Player 23 oder höher erforderlich.

Der native Windows-Netzwerkcode wurde behoben, um sicherzustellen, dass Verbindungen keine Griffe schließen, die derzeit von anderen Verbindungen verwendet werden.

* Ticket #24029 - HLS FER-Streams geben nicht alle Mid-Roll-Anzeigen in der .json-Datei im mittleren Roll-Format wieder.

Dieses Problem wurde behoben, indem es Kunden ermöglichte, benutzerdefinierte Parameter in der Opportunity-Instanz separat festzulegen, sodass Clients OpportunityGenerator nicht überschreiben müssen.

**Version 1.4.26** (839)

* Zendesk #18854 - Aktualisieren der Logik der kreativen Auswahl basierend auf CRS-Regeln
   * Unterstützung für die Aktualisierung der Logik der kreativen Auswahl basierend auf CRS-Regeln

* Zendesk #22725 - playManager.beginPlayback()-Implementierung in der Beispielanwendung für Desktop

   * Korrektur, indem dieser redundante Aufruf am Ende von startPlaybackFromFlashVars entfernt wurde, da die Methode von setupVideo() aufgerufen wurde

* Zendesk #22807 - Null-Referenz-Ausnahme für SeekManager

   * Korrektur durch Bereitstellung des erforderlichen NULL-Zeigerschutzes innerhalb von SeekManager in Bezug auf _dispatcher

* Zendesk #22822 - Häufige Pufferung bei Verwendung von TVSDK zur Wiedergabe eines klaren HLS

   * Korrektur, indem die anfängliche Chance, die von adSignalingModeOpportunityGenerator generiert wurde, entfernt wurde, wenn keine Anzeige vorhanden ist

* Zendesk #23378 - Stream-Integritätsblöcke rule.xml

   * Korrektur durch das Laden der Datei &quot;rules.xml&quot;über den Arbeitsablauf für die Stream-Integrität

**Version 1.4.24** (817)

* Zendesk #19851 - Wenn sich der Player an eine andere Bitrate anpasst, springt er einige Frames zurück in die Zeit mit der neuen Bitrate, was zu einem unangenehmen Erlebnis führt

**Hinweis**: Für dieses Problem ist Flash Player 22.0.0.175 oder höher erforderlich.

Das Problem, bei dem der DRM-Adapter nach dem Herunterladen eines kleinen Teils eines Segments nicht ordnungsgemäß wiederhergestellt wird, wurde behoben.

* Zendesk #20784 - Analytics: Auslösen von Inhaltsbeendigungen für Live-Video-Transitionen

Dieses Problem wurde behoben, indem eine API (trackVideoComplete) hinzugefügt wurde, mit der der Abschluss von Inhalten während einer LINEAR/LIVE-Videoverfolgungssitzung manuell ausgelöst wird.

Die folgenden Bibliotheken wurden aktualisiert:

* Zendesk #21643 - VPAID-Anzeigen werden nicht vollständig wiedergegeben

   * AdobeMobile-Bibliothek auf 4.10.0
   * VHL-Bibliothek zu 1.5.6
   * VHL-Nielsen-Bibliothek zu 1.6.7

Dieses Problem wurde behoben, indem ein Viewport mit einer Nullhöhe verwendet wurde, um die Bühne zu füllen, wenn eine VPAID-Anzeige abgespielt wird.

* Zendesk #22110 - Analytics: Hinzufügen ein Feld h:sc:ssl an die Heartbeat-Verfolgungsaufrufe

Die SSL-bezogenen Probleme wurden behoben und die VHL-Bibliothek, die in TVSDK verwendet wird, wurde auf die neueste Version aktualisiert.

* Zendesk #22608 - Video zeigt gelegentlich einen schwarzen Bildschirm an (Flash Player 22.0.0.175 oder höher erforderlich)

Während der adaptiven Bitrate mit der maximalen Bitrate wird beim Neuladen des Videos gelegentlich ein schwarzer Bildschirm angezeigt, auch wenn dem Client Updates zur Position angezeigt werden und sich der Client so verhält, als würde er Inhalte wiedergeben.

**Version 1.4.23** (809)

* Zendesk #2887 - Problem mit dem Überspringen von Werbeanzeigen nach dem Rollen, wenn die Anzeigenregellogik auf das TVSDK angewendet wird

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.240 oder höher erforderlich.

Das Problem, bei dem die Post-Roll-Anzeigen übersprungen wurden, wenn die Anzeigenregellogik auf das TVSDK angewendet wurde, wurde behoben.

* Zendesk #19863 - Anzeige mit VPAID-Mediendatei verworfen

Wenn eine riesige Inline-Anzeige über mehrere Mediendateien mit einer VPAID-Anzeige als erste Anzeige verfügt, wird die Inline-Anzeige nicht für Live-Streams wiedergegeben. Dieses Problem wurde behoben, indem stattdessen eine andere Mediendatei abgerufen wurde.

* Zendesk #21021 - Spätes Binden von Audio, wodurch sich das Audiosegment wiederholt

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.240 oder höher erforderlich.

Das Problem mit der Audiowiederholung wurde behoben.

* Zendesk #21125 - Frühzeitige Rückkehr von Live-/linearen Werbeunterbrechungen

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.240 oder höher erforderlich.

Diese Version unterstützt die Rückkehr von einer Werbeunterbrechung frühzeitig vor der Wiedergabe der Werbeunterbrechung bis zum Abschluss. Die frühe Rückkehr wird durch ein benutzerdefiniertes Manifest-Tag angezeigt.

* Zendesk # 21369 Verspätete Bindung Audio verursacht eine inkonsistente Zeit

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.240 oder höher erforderlich.

Das Problem mit der Audiowiederholung wurde ebenfalls behoben.

* Zendesk #21760, 20921 - Audio Video Desync on Seek.

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.240 oder höher erforderlich.

Das Problem mit der Audiowiederholung wurde behoben.

* Zendesk #22024 - Fehler beim Ausführen des TVSDK

Das Problem, bei dem der Referenz-Player keinen Stream abspielte und beim Beginn eine Ausnahme auslöste, wurde behoben.

**Version 1.4.22** (791)

* Zendesk #17580 - Primetime-Laufzeitfehler mit Code 3357

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.197 oder höher erforderlich.

Die zufälligen 3357-Fehler, die beim Aufruf von storeVoucher() durch das ordnungsgemäße Initialisieren der deviceID aufgetreten sind, wurden behoben.

* Zendesk #21334 - TVSDK-Wert für die Zeitüberschreitung bei Anzeigen-Anfragen von Drittanbietern

In dieser Version wurde der Zeitlimit für globale Anzeigenanforderungen hinzugefügt.

**Version 1.4.21** (782)

* Zendesk #19580 TVSDK wartet vor dem Senden von `PTTimedMetadataChangedNotification` Benachrichtigungen auf den Abschluss des Content-Resolvers

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.182 oder höher erforderlich.

Dieses Problem wurde im Desktop Reference Player behoben, indem es die Möglichkeit bereitstellte, Anzeigen-Tags festzulegen und einen benutzerdefinierten Opportunitätsgenerator hinzuzufügen, der anzeigt, wie benutzerspezifische Hinweise abonniert werden und wie diese Hinweise in einer VOD-Datei verarbeitet werden.

* Zendesk #20806 Zukünftige Mid-Roll-Anzeigen im DVR-Fenster werden nach dem Austauschen von Cams nicht ausgelöst

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.182 oder höher erforderlich.

Dieses Problem wurde behoben, indem die App aktualisiert wurde, um _resource.metadata.setValue(DefaultMetadataKeys.ENABLE_LIVE_PREROLL, &quot;false&quot;) so festzulegen, dass das Einfügen von Pre-Roll-Werbeanzeigen in einen PIP-Swap deaktiviert wird. Daher wird keine Pre-Roll-Gelegenheit generiert.

Es wurde eine Sortierfunktion eingeführt, um die nicht sequenzierte Anzeigenplatzierung zu korrigieren, die zu einer negativen Hauptinhaltsdauer führte.

* Zendesk #20522: VPAID 2.0-Anzeigen können nicht übersprungen werden

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.182 oder höher erforderlich.

* Dieses Problem wurde behoben, indem VPAID-Anzeigen während des Anzeigenverlusts übersprungen wurden.
* Wenn die Richtlinie für Werbeunterbrechungen auf &quot;Überspringen&quot;festgelegt ist, werden Ereignisse für Anzeigen und Werbeunterbrechungen weiterhin ausgelöst. Der Player-Status ist inkonsistent.

Dieses Problem wurde behoben, um sich korrekt zu verhalten und keine Ereignis auszulösen, wenn der Werbeunterbrechung übersprungen wird.

* Zendesk #209555 Festlegen von Schlüssel-Wert-Paaren in der Eigenschaft customParameters über den Opportunitätsgenerator

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.182 oder höher erforderlich.

Die Auditude-Anforderung analysiert die Auditude-Einstellungen für benutzerdefinierte Parameter, wenn eine Anzeigeneinheit für Werbeanforderungen erstellt wird.

Dieses Verhalten wurde geändert, um benutzerdefinierte Parameter aus dem Opportunity-Objekt in die Anforderung einzubeziehen. Außerdem können nicht mehrere Möglichkeiten mit verschiedenen benutzerdefinierten Parametern in einer Auditude-Anforderung zusammengefasst werden.

* Zendesk #21227 - m3u8 wird nicht konsistent wiedergegeben

**Hinweis**: Für dieses Problem ist Flash Player 21.0.0.211 oder höher erforderlich.

Dieses Problem wurde behoben, indem TVSDK das Manifest (HLS-Profile) ignorieren konnte, das den AC3-Codec enthält, den TVSDK nicht unterstützt (Surround).

**Version 1.4.20** (762)

* Zendesk #19181 - Trick play fast forward to live point lock stream.

**Hinweis**: Für dieses Problem ist Flash Player 20.0.0.306 oder höher erforderlich.

* Zendesk #19286 - Flash Player-Absturz beim Suchen in einem FER-Stream.

**Hinweis**: Für dieses Problem ist Flash Player 20.0.0.306 oder höher erforderlich.

Die gelegentlichen Änderungen, die beim Suchen in Google Chrome aufgetreten sind, wurden durch Herunterfahren der Abfragen behoben, wenn die Abfragen zu lange dauern, bis eine Antwort eingeht, oder wenn der Socket heruntergefahren wird.

* Zendesk #19305 - Choppy-Wiedergabe bei der Wiedergabe eines Streams mit A/V-Unterbrechung aufgetreten.

**Hinweis**: Für dieses Problem ist Flash Player 20.0.0.306 oder höher erforderlich.

Dieses Problem wurde durch eine Warnung des Berichte behoben.

* Zendesk # 19359 - Flash Player ist aufgrund der Position von #EXT-X-FAXS-CM abgestürzt: -Attribut im Manifest auf Einstellungsebene.

Dieses Problem wurde behoben, wenn das Tag #EXT-X-FAXS-CM oben in der Wiedergabeliste angezeigt wurde, bevor einzelne Bitraten oder Segmente in der Wiedergabeliste angezeigt wurden.

* Zendesk #19489 - Plugin &quot;Fast Forward to Live Point stalls&quot;(Live-Stream)

Dieses Problem ist mit Zendesk #19181 identisch.

* Zendesk #19699 - TVSDK kann nicht zwischen WebVTT-Untertitelspuren wechseln

Dieses Problem wurde behoben, indem der Player beim Ändern einer Verfolgung abgeblättert und das Manifest neu geladen wurde und das UTF8-Zeichenfolgenkonvertierungsproblem korrigiert wurde, das die Verfolgungsnamen der Dublette-Byte-WebVTT-Beschriftung beeinflusste.

**Version 1.4.19** (1.4.19.738)

* Zendesk #18234 - Flash Player stürzt bei der Wiedergabe der Streams mit Unicode-Zeichenfolgen in CC ab

Dieses Problem erfordert Flash Player FP 20.0.0.267 oder höher und wurde durch die korrekte Verarbeitung der Unicode-Zeichenfolge behoben.

* Zendesk #18304 - Stream Integrity Support for VPAID Ads

Diese Funktion erfordert Flash Player FP 20.0.0.267 oder höher und wurde in Version 1.4.19 eingeführt.

* Zendesk #18766 - Referenz-Player kann nicht-lateinische Unicode-Zeichen in CC-Tracknamen anzeigen

Diese Funktion erfordert Flash Player FP 20.0.0.267 oder höher und wurde durch die korrekte Verarbeitung der Unicode-Zeichenfolge behoben.

* Zendesk #18804 - Player stürzt in Firefox 42 ab

Dieses Problem erfordert Flash Player FP 20.0.0.235 oder höher und ist dasselbe Problem wie Zendesk #18723.

* Zendesk #18864 - Absturz des vollständigen Flash Player-Plugins

Dieses Problem erfordert Flash Player FP 20.0.0.235 oder höher und ist mit Zendesk #18723 identisch.

* Zendesk #18998 - Wenn Audio- und Video-Zeitstempel nicht übereinstimmen, kam es zu einem endlosen Herunterladen von Segmenten bei Diskontinuität.

Dieses Problem wurde behoben, indem die Lücke zwischen Zeitstempeln ignoriert und nur der heruntergeladene Inhalt wiedergegeben wurde.

* Zendesk #19093 - Mid-Roll-Anzeigen können nur einmal mit Live- und Full-Ereignis-Replay-Inhalten (FER) angesehen werden. Diese Anzeigen konnten jedoch nicht mehr beobachtet werden, wenn sie schnell weitergeleitet oder über die Anzeigen hinaus gesucht wurden

Wenn in Primetime in der standardmäßigen adPolicy-Auswahl eine Mid-Roll-Anzeige angezeigt wird, wird adBreak nach Abschluss einer Suche nicht an die gesuchte Position verschoben. Um die Anzeige nach der Suche erneut wiederzugeben, muss die Anwendung die Funktion selectAdBreaksToPlay() außer Kraft setzen.

* Zendesk #19101 - Durch das Zurückspulen in ungelöste Midroll-Anzeigen wird die Anzeigenplatzierung entfernt.

Dieses Problem wurde behoben, indem der Player die Funktion &quot;playMetrics time&quot;, &quot;minimumOpportunityTime&quot;und &quot;Timeline&quot;aktualisieren konnte.

* Zendesk #19102 - Probleme mit dem FER- und Trick-Modus

Dieses Problem erfordert Flash Player FP 20.0.0.267 oder höher und wurde behoben, indem die Datei advertisingMetadata.adSignalingMode korrekt eingestellt wurde.

* Zendesk #19175 - Manchmal werden Preroll-Anzeigen nicht angezeigt, wenn der Stream zum ersten Mal wiedergegeben wird.

Dieses Problem wurde behoben, indem eine neue API, adRequestTimeout, zu den AuditudeSettings für eine Zeitüberschreitung bei einer Anzeigenanforderung hinzugefügt wurde. Benutzer können jetzt den standardmäßigen 10-s-Anzeigenanforderungs-Timeout überschreiben.

**Version 1.4.18** (1.4.18.722)

* Zendesk #3324 - Der Berichte Primetime-Anzeigen verfolgt keine Werbeunterbrechungen, wenn in einem VMAP keine Anzeigenmedien vorhanden sind.

Wenn eine Werbeunterbrechung leer ist, wurden der Beginn der Werbeunterbrechung und die Ereignis der vollständigen Verfolgung nicht gepingt. Dieses Problem wurde behoben, indem Werbeunterbrechungen für Beginn-Pings für leere Werbeunterbrechungen, wie z. B. VMAP AdBreak, mit einem gültigen AdSource-Knoten gesendet wurden.

**Version 1.4.17** (1.4.17.702)

* Zendesk #17168 - Beschriftungen werden nach dem Umschalten zwischen Sichtbarkeit für etwa 10 Sekunden nicht angezeigt

Dieses Problem wurde behoben, indem Unterstützung für das EXT-X-MEDIA-TIME-Tag für VT-Untertiteldateien bereitgestellt wurde.

* Zendesk #17983 - Wenn keine Schlüssel für ein Manifest heruntergeladen werden, schlägt die gesamte Manifestwiedergabe fehl

**Hinweis**: Sie müssen mindestens über Flash Player FP 19.0.0.245 oder höher verfügen.

Beim Abspielen von Live-Inhalten gibt es möglicherweise ungültige Schlüssel im Manifest (z. B. für Blackout-Zeiträume), aber andere Zeitbereiche haben möglicherweise gültige Schlüssel und werden weiterhin abgespielt. Wenn zuvor ein Schlüssel, der in einem Manifest aufgelistet war, nicht heruntergeladen werden konnte, schlug das gesamte Manifest fehl. Jetzt schlägt das Manifest nur dann fehl, wenn alle aufgelisteten Schlüssel nicht heruntergeladen werden können. Wenn einige Schlüssel gültig sind, aber einige dieser Schlüssel nicht heruntergeladen werden konnten, wird Inhalt wiedergegeben. Wir werden immer noch scheitern, wenn wir versuchen, ein Segment zu spielen, das einen Schlüssel erfordert, den wir nicht haben.

* Zendesk #18554 - Stream-Integrität, in einigen Fällen durch Herunterschneiden der Cookies

**Hinweis**: Sie müssen mindestens über Flash Player FP 19.0.0.245 oder höher verfügen.

Es wurde ein Fehler im Code zur Cookie-Manipulation behoben, durch den Cookie-Werte abgeschnitten werden könnten.

**Version 1.4.16** (1.4.16.684)

* Zendesk #3732 - Hinzufügen Unterstützung von Proxys in Chrome für Stream-Integrität (Flash Player FP 19.0.0.207 oder höher erforderlich)

Das ist eine Verbesserung.

* Zendesk #4244 - Streaming-Probleme beim PTS-Rollover

Dieses Problem wurde behoben, indem Rollover erkannt und die Diskontinuität pro Nutzlasttyp verwaltet wurde und nicht generell.

* Zendesk #4487 - Tracking Linear Kanal of Content

Dieses Problem wurde behoben, indem der Video Heartbeat-Tracker während einer linearen Stream-Wiedergabesitzung erneut initialisiert wurde.

* Zendesk #17427 - Adobe Stream Integrity working not working through a proxy on Chrome (Win7) ()

**Hinweis**: Die Auflösung erfordert Flash Player FP 19.0.0.207 oder höher.

Dieses Problem ist mit Zendesk #3732 identisch.

* Zendesk #17907 - Auf pHLS Live Stream mit Flash Player 19 starten

**Hinweis**: Die Auflösung erfordert Flash Player FP 19.0.0.207 oder höher.

Dieses Problem wurde behoben, indem die Live-Streams behandelt wurden, bei denen sich die Domänen der TS-Dateien beim erneuten Laden des Live-Manifests ändern und die Dateien zweimal heruntergeladen wurden.

* Zendesk #17931 - Wiedergabe von HLS-Inhalten mit Tonschiefer am Anfang fehlgeschlagen

**Hinweis**: Die Auflösung erfordert Flash Player FP 19.0.0.207 oder höher.

Das Problem wurde behoben, indem Streams ohne Audio in den ersten 2 Sekunden der ersten TS-Datei behandelt wurden.

* Zendesk #17934 - Live-Streaming-Fehler mit Flash 19.0.0.185

**Hinweis**: Die Auflösung erfordert Flash Player FP 19.0.0.207 oder höher.

Das Problem wurde behoben, indem Live-Streams mit Zeitüberschreitungen zwischen Audio- und Videorahmen an Segmentgrenzen behandelt wurden.

* Zendesk #17973 - Der neueste Flash Player 19.0.0.185 stürzt während des Mid-Roll ab

**Hinweis**: Die Auflösung erfordert Flash Player FP 19.0.0.207 oder höher.

Das Problem wurde behoben, indem ungemusterte Audiodaten mit dem Einfügen von Mid-Roll-Anzeigen behandelt wurden. (Der Parser-Schalter tritt an jeder Stelle in der Wiedergabe auf und der Inhalt wird an die mittlere oder mittlere Anzeige Transition usw.)

* Zendesk #18049 - Flash 19-Absturz mit Firefox 42 beta

Dieses Problem ist mit Zendesk #17973 identisch.

**Version 1.4.15** (1.4.15.678)

* Zendesk #4377: Ereignis AD_BREAK_SKIPPED beim Überspringen einer Werbeunterbrechung aufgrund der Anzeigenrichtlinie

Die Korrektur bestand darin, AD_BREAK_SKIPPED hinzuzufügen, wenn eine Anzeige übersprungen wurde.

* Zendesk #4496 - Stream-Integrität: Fehler 102100 mit Umleitungen zu tokenisierten Streams.

Das Problem wurde behoben, um Unterstützung für das Festlegen der AVNetworkConfiguration-Eigenschaft useCookieHeaderForAllRequests über das TVSDK hinzuzufügen.

* Zendesk #17179 - Flash Player stürzt bei mehreren SAP-Änderungen für verschlüsselte Inhalte ab.

Ein Absturz bei der Wiedergabe verschlüsselter Inhalte wurde behoben.

**Hinweis**: Für die Fehlerbehebung ist Flash Player 19.0.0.200 oder höher erforderlich.

* Zendesk #17499 - Wie entfernen wir nach der Armbanduhr keine Zwischenrollen, sondern entfernen das Vorspann aus dem fertigen Inhalt

Es wurde ein Typ zu AdBreakTimelineItem (AdBreakTimelineItem.placementType) hinzugefügt, sodass AdPolicySelector eine andere Richtlinie für Pre-Roll-, Mid-Roll- und Post-Roll-Inhalte zurückgeben kann.

* Zendesk #17665 - Bandbreitendrehung

Die Korrektur bestand darin, die Logik zu entfernen, um die Puffergröße der Zielgruppe auf die anfängliche Puffergröße zu ändern, wenn die Pufferung beginnt.

**Version 1.14.14** (1.4.14.771)

* Zendesk #17363 - FEHLERBEHEBUNG DER README-Dokumentation für den Referenzplayer

   * Genauere Anweisungen zum Herunterladen und Installieren von playerglobal.swc.
   * Hinzufügen Anweisungen zum Aktualisieren der Projektkonfiguration mit einer bestimmten Flash-Player-Version.
   * Aktualisieren Sie die Projektkonfiguration AdvertisingOverlay, um die Mindestplayer-Version zu verwenden.
   * Aktualisieren Sie die ReferenzCore-Projektkonfiguration, um eine bestimmte Player-Version 11.9 zu verwenden.

* Zendesk #17471 - Player-Freezes

Teilweise Korrektur für ein Problem, bei dem eine Anzeige nicht von Anfang an nach der Suche wiedergegeben wird.

* Zendesk #17496 - Podbuster wird beim Zurücksuchen im DVR-Fenster nicht aufgelöst

Stellen Sie für jede Werbeunterbrechung benutzerdefinierte Parameter bereit.

**Version 1.4.13** (1.4.13.660)

* Zendesk #4037 - Kein brauchbarer Profil-Fehler (Flash Player 18.0.0.232 oder höher erforderlich)

URL-Parsing-Problem beheben, wenn Abfrage-Parameter &quot;http&quot;enthält

* Zendesk #4260 - Flash Player 18 stürzt in IE11 ab (Flash Player 18.0.0.232 oder höher erforderlich)

Ein Absturz beim Abspielen von Videos im Vollbildmodus mit IE11 wurde behoben

* Zendesk #4262 - Adobe Primetime player stürzt bei Windows 10 ab (Flash Player 18.0.0.232 oder höher erforderlich)

Es wurde ein Absturz bei der Wiedergabe von Videos im Vollbildmodus mit FireFox unter Windows behoben.

* Zendesk #4279 - HLS TVSDK-Anzeigeneinfügung -302 Umleitungsproblem unter iOS und Desktop

Es wurde ein Problem behoben, bei dem der Typ einer URL nicht richtig erkannt wurde, weil sie keine Erweiterung hatte

* Zendesk #4306 - Flash Player stürzt nur ab, wenn der Vollbildmodus unter Windows ausgeführt wird (Flash Player 18.0.0.232 oder höher erforderlich)

Ein Absturz beim Abspielen von Videos im Vollbildmodus unter Windows wurde behoben.

* Zendesk #4480 - Fehlende ID3-Tag-Ereignis (Flash Player 18.0.0.232 oder höher erforderlich)

**1.4.12 **(1.4.12.656)

* Zendesk #2751 - CSAI und CRS| Verbesserung: Verarbeiten Sie dynamische Elemente in bestimmten Mediendatei-URLs.

Der Dienst für kreative Umverpackungen wurde aktualisiert, um Anzeigen mit dynamischen kreativen URLs korrekt zu bearbeiten.

* PTPLAY - 2114 - Unterstützung für MP4-Wiedergabe.

Die grundlegende Wiedergabe von MP4-Inhalten wird jetzt unterstützt, einschließlich Wiedergabe, Pause und Suchen.

Für Flash Player 18.0.0.225 oder höher ist Folgendes erforderlich:

* Zendesk #3992 - Zusätzliche TrickPlay-Geschwindigkeiten.

TrickPlay akzeptiert jetzt Raten über 16x: +/- 32, +/-64 und +/-128.

* Zendesk #3113 - Flash Player-Plugin-Absturz

Ein Absturz beim Versuch, eine Umleitungsanzeige unter Mac Firefox wiederzugeben, wurde behoben.

* Zendesk #4037 - Fehler &quot;Kein brauchbares Profil&quot;
* Zendesk #4262 - Adobe Primetime-Player stürzt bei Windows 10 ab

Abstürze in Windows Firefox während der Wiedergabe im Vollbildmodus behoben.

**Version 1.4.11** (1.4.11.648)

* Zendesk #1869 - Problem beim Ändern der Schriftgröße (Flash Player 18.0.0.200 erforderlich)

Untertitelgrößen dürfen im WebVTT-Untertitelcode verwendet werden.

* Zendesk #3113 - Flash Player Plugin Crashing (Flash Player 18.0.0.200 erforderlich)
* Zendesk #3268 - Desktop: Beginn mit Videoplayer, die nach +- 40/50 Sekunden flackern und nach +- 90 Sekunden schwarz werden (Flash Player 18.0.0.200 erforderlich)

Fehlerbehebung bei der Anzeige des Videos

* Zendesk #3670 - INVALID_PARAMETER-Fehler bei VOD beim Suchen im Referenz-Player (Flash Player 18.0.0.200 erforderlich)

InvalidateProfiles in ThreadSeek, wenn ein neuer Zeitraum erkannt wird.

* Zendesk #3896 - Flash Player stürzt ab, wenn die Stream-Integrität auf &quot;ON&quot;für Chrome eingestellt ist (Flash Player 18.0.0.200 erforderlich)

Absturz im nativen Netzwerkmodus in Pfeffer behoben 

* Zendesk #3905 - TVSDK-Player wird nicht geladen, wenn er auf CDN gehostet wird

Es wurden Probleme beim Suchen des Platzhaltertokens behoben, wenn pageDomain von der SWF-Domäne abweicht.

**Version 1.4.10** (1.4.10.642)

* Zendesk #3249 - TVSDK Web Player stürzt Flash auf Firefox ab

Es wurde ein gelegentlicher Flash Player-Absturz mit Firefox auf einem Mac behoben, der auftrat, wenn ein Stream auf einem externen Monitor zu einem höheren Bitratenstream wechselte.(Flash Player 18.0.0.160 erforderlich)

* Zendesk #3268 - Desktop: Videoplayer-Beginn, die nach `+-` 40/50 Sekunden flackern und nach `+-` 90 Sekunden schwarz werden

Es wurde ein Problem in Mac Chrome behoben, durch das Stream flackern und schließlich schwarz werden konnte. (Flash Player 18.0.0.161 erforderlich)

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` -Makro nicht gefüllt

   * Fehlercode 400 wird angezeigt, wenn Inline-Anzeige ein falsches kreatives Element enthält.
   * `[ERRORCODE]` Makro wird URL-kodiert

* Zendesk #3601 - Erweiterungsanfrage: Wrapper Companion Management

   * TVSDK zeigt Wrapperbegleiter an, die Ressourcen (html, iframe oder static) enthalten, die an das Inline-Netz geschlossen werden. (wenn die Inline keinen Eintrag für diese Größe enthält)
   * Wrapperbegleiter mit Ressource werden ignoriert, wenn sie nicht für die Anzeige verwendet werden. (nicht zur Verfolgung verwendet)
   * Nur Wrapper-Begleiter mit NO-Ressource werden für Verfolgungszwecke verwendet. (Wrapper-Begleiter, der nur die Verfolgung enthält)

**Version 1.4.9**

* Zendesk #2615 - Problem beim Entfernen der HLS-Ansicht vom Desktop-Display

clearVideo()-Methode zu MediaPlayer hinzugefügt. Löscht den angezeigten Videobild, indem der AVStream vom StageVideo-Objekt gelöscht wird. Sollte nur aufgerufen werden, wenn das Video angehalten wird, und replaceCurrentResource oder replaceCurrentItem muss aufgerufen werden, bevor play() erneut aufgerufen werden kann. 

* Zendesk #3169 - Update Reference Player with Adobe Analytics integration

Referenz-Player wurde mit der Adobe Analytics-Integration aktualisiert

* Zendesk #3296 - Desktop HLS TVSDK - Anzeigen von Drittanbietern VAST, die nicht abgespielt werden

Bei den MIME-Typen für das HLS-Format wurde zwischen Groß- und Kleinschreibung unterschieden. Dies war falsch und wurde geändert, sodass die Groß-/Kleinschreibung nicht mehr berücksichtigt wird.

**Version 1.4.8**

* Zendesk #2737 - Desktop Player - Fehler 106000 (Flash Player 17.0.0.184 erforderlich)
* Zendesk #3007 - Pre-Roll-Anzeigen, die nach der Aktualisierung auf Flash Player 17 nicht angezeigt werden (Flash Player 17.0.0.184 erforderlich)
* Zendesk #3085 - HLS-Player für Desktop löst 106000 Fehler nach 60 Sekunden aus (Flash Player 17.0.0.184 erforderlich)

**Version 1.4.7**

* Zendesk #2760 - DISCONTINUITY-Tag während des TrickPlay-Modus ignoriert (Flash Player-Version 17.0.0.158 erforderlich)
* Zendesk #2760 - DISCONTINUITY-Tag während des TrickPlay-Modus ignoriert (Flash Player-Version 17.0.0.158 erforderlich)

**Version 1.4.6**

* Zendesk #2652 - Auditude-Dokumentation für HLS auf dem Desktop, Clarified Auditude media_id für HLS-Dokumentation auf dem Desktop

**Version 1.4.5**

* Zendesk #2256 - Zugriff auf Master-Playlist, PSDK aktualisiert, um timedMetadata-Ereignis für abonnierte Tags in der Master-Playlist auszulösen. (Flash Player-Version 17.0.0.134 erforderlich)
* Zendesk #2417 - Player, der versucht, Untertitel vor dem Beginn der Wiedergabe herunterzuladen, verwendete WebVTT die falsche Segmentnummernvariable für die Segmentnummerübereinstimmung. Fehler werden nur für Medien angezeigt, deren Segmentindizes bei Null beginnen. (Flash Player-Version 17.0.0.134 erforderlich)
* Zendesk #2537 - Flash Player stürzt bei der Verwendung des Ppper-Plugins mit Chrome ab (Flash Player-Version 17.0.0.134 erforderlich)
* Zendesk #2547 - Arabische Untertitel: Text sollte rechtsbündig ausgerichtet sein (Flash Player Version 17.0.0.134 erforderlich)

**Version 1.4.4**

* Zendesk #1561 - Siehe: `[Adobe Primetime]` Aktualisieren: Client-basierte HLS-Failover-Unterstützung für PROGRAMM-DATE-TIME im Desktop-PSDK (Flash Player-Version 16.0.0.305 oder höher erforderlich)
* Zendesk #2197 - `[Ads]` Verfolgung von Anzeigenfehlern
* Zendesk #2286 - Funktionsanforderung: Informationen zum Status des Anzeigenladens (VPAID) angeben
* Zendesk #2285 - Funktionsanforderung: Anzeige nach einer bestimmten Timeout-Dauer überspringen
* Fehler #3921755 - OpenSSL library update to version 1.0.1L in Flash Player (Flash Player-Version 16.0.0.305 oder höher erforderlich)

**Version 1.4.2**

* Zendesk #1303 - Vertical Offset for Closed Caption (Flash Player Version 16.0.0.235 oder höher erforderlich), erwartetes Veröffentlichungsdatum: Dezember 2014)
* Zendesk #1870 - Geschlossene Beschriftung aktivieren und deaktivieren (Flash Player Version 16.0.0.235 oder höher erforderlich, voraussichtliches Veröffentlichungsdatum: Dezember 2014)
* Zendesk #2110 - Die Wiedergabe wird gestoppt, nachdem versucht wurde, während einer VPAID-Anzeige den Vollbildmodus zu aktivieren (Flash Player-Version 16.0.0.235 oder höher erforderlich, voraussichtliches Veröffentlichungsdatum: Dezember 2014)
* Zendesk #2199 - `[VPAID]` Player reagiert nicht, wenn nach einer Werbeunterbrechung gesucht wird
* Zendesk #2358 - Siehe: `[Analytics]` Falsche Kapiteldaten

**Version 1.4.1**

* Die Blackouts-API wurde aktualisiert, um mit der Android- und iOS-Implementierung konsistent zu sein.

**Version 1.4.0**

* Zendesk #1024 - Funktion zum Entfernen von Anzeigen aus dem Stream über Manifest
* Zendesk #1423 - Fehler bei der HLS-Wiedergabe blockiert Flash Player (ohne Fehler gemeldet)
* Zendesk #1674 - ClosedCaption Nicht angezeigt, korrekte 708-Beschriftungsanzeige, wenn 0 x 03 ETX-Codes fehlen.

</p>
</details>

## Bekannte Probleme {#known-issues}

* &quot;Untertitel&quot;funktioniert nicht mit reinen Audioinhalten, da das Untertitelsystem nur mit Videos arbeiten kann.
Ohne Video gibt es keine Viewport-Dimension und ohne Viewport-Dimension können keine Grafiken für Beschriftungen angezeigt werden.
* Die Stream-Integrität ist in Google Chrome aufgrund der Chrome-Sandbox-Beschränkungen etwas langsamer.
* Wenn Sie in TVSDK 1.4 autoPlay deaktivieren, kann ein DRM-Fehler auftreten, wenn der Player mindestens eine Minute lang untätig bleibt. Um dieses Problem zu umgehen, ändern Sie, wenn Sie autoPlay deaktivieren, aber Assets vorladen, den Inhalt `ReferenceCore.as` von `onPlaybackManagerPrepared`:

>if (_playManager.autoPlay) {
>_playManager.play();
>} else {
>_playManager.play();
>_playManager.pause();
>}

* **Version 1.4.13** PTPLAY-8501 - Wenn VMAP zwei direkte, nicht transkodierte MP4-Anzeigen zurückgibt, wird dieselbe Fallback-Anzeige zweimal wiedergegeben.

* **Version 1.4.2** In der Version 16 von Flash Player wurde ein Problem mit der ABR-Logik &quot;Abschalten&quot;identifiziert, nachdem der Player in ein leeres Pufferverfahren-Ereignis umgewandelt wurde. Das Problem verhindert, dass die Bitrate in Umgebung mit schlechter Bandbreite heruntergeschaltet wird, sobald der Player in einen Pufferzustand wechselt. Um das Problem zu umgehen, stellen Sie sicher, dass Ihre App `BufferControlParameters.initialBufferTime` während der Pufferung (d. h. während eines `BufferControlParameters.playbackBufferTime` Ereignisses) die gleiche wie `BufferEvent.BUFFERING_BEGIN` vorübergehend ist, und setzen Sie sie dann auf die festgelegten Werte für das `BufferEvent.BUFFERING_END` Ereignis zurück. Die Behebung dieses Problems ist in der nächsten Patch-Version von Flash Player Version 16 verfügbar.

* **Version 1.4.0**

   * PTPLAY-1634 - Das gleiche abonnierte Tag hat unterschiedliche Zeitstempel in verschiedenen Live-Fenstern. Wenn Live-Fenster verschoben werden, sollte dasselbe Tag in jedem von ihnen dieselben Zeitstempel haben. Manchmal haben dieselben Tags jedoch unterschiedliche Zeitstempel.
   * PTPLAY-28 - Die Zeitleiste von MediaPlayer enthält keine leeren Umbrüche.
   * Eine domänenübergreifende Richtliniendatei (crossdomain.xml) ist erforderlich, damit Inhalte von einer anderen Domäne gestreamt werden können. [Festlegen einer crossdomain.xml-Datei für HTTP-Streaming](https://www.adobe.com/devnet/adobe-media-server/articles/cross-domain-xml-for-streaming.html).
   * Fehler #3694203 - In einem DVR-Stream kann die Suche von einer Wiedergabe-Mid-Roll zu einer anderen Mid-Roll-Anzeige zum Einfrieren des Browsers führen
   * Fehler #3753725 - selectPolicyForSeekIntoAd berücksichtigt nicht, wenn der Werbeunterbrechung beobachtet wurde
   * Fehler #3754529 - Pre-Roll-Anzeigen werden nicht aus dem Stream entfernt, wenn sie in einem Live-DVR-Stream wiedergefunden werden
   * Fehler #3761896 - Wenn die Suche während der Anzeigenwiedergabe zulässig ist, passen Anzeigenmarken nach der Suche erneut an. Problemumgehung ist nicht die Verwendung von ITEM_UPDATED-Rückruf während der Suche
   * Fehler #3779889 - Der vollständige Aufruf wird nicht ausgeführt, wenn das Ende der Trick-Wiedergabe in Video Analytics erreicht wird
   * Fehler #VA-779 - Der Bitratenänderungs-Ereignis-Heartbeat wird nicht für Enhanced Video Analytics mit Heartbeat-Support-Referenzimplementierung gesendet - Trick play wird nicht in der Beispielanwendung implementiert.

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite &quot; [Adobe Primetime - Training und Support](https://helpx.adobe.com/support/primetime.html) &quot;.
