---
title: TVSDK 1.4 für Desktop HLS - Versionshinweise
description: TVSDK für Desktop HLS - Versionshinweise beschreiben, was neu oder geändert ist, welche gelösten und bekannten Probleme in TVSDK DHLS auftreten.
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
exl-id: 5e227c99-acf6-4b16-a35a-68e2928fdbfd
source-git-commit: 1bc2f6c230c262babf2958c32fee31afcad04c2f
workflow-type: tm+mt
source-wordcount: '5194'
ht-degree: 0%

---

# TVSDK 1.4 für Desktop HLS - Versionshinweise {#tvsdk-for-desktop-hls-release-notes}

TVSDK für Desktop HLS - Versionshinweise beschreiben, was neu oder geändert ist, die gelösten und bekannten Probleme in TVSDK DHLS.

## Neue Funktionen {#new-features}

**1.4.31**

* **Multi-CDN-Unterstützung für CRS-Anzeigen**

   * Standardmäßig werden alle transkodierten Assets auf einem von Adoben verwalteten CDN auf Akamai gehostet. Mit der neuesten Version bietet Adobe Creative Repackaging Service (CRS) die Möglichkeit, die transkodierten Kreativinhalte gemäß Kundenwunsch in mehrere CDNs hochzuladen.
   * TVSDK werden neue APIs hinzugefügt, um die Angabe der endgültigen kreativen CRS-URL zu ermöglichen, wenn die Standard-URL nicht verwendet wird. Informationen zur Verwendung dieser neuen APIs finden Sie in der Dokumentation .

### Neue Funktionen in früheren Versionen {#new-features-previous}

**1.4.30**

* **Abrechnungsmetriken**

Um Kunden aufzunehmen, die nur für ihre Verwendung zahlen möchten, anstatt einen festen Satz unabhängig von der tatsächlichen Verwendung zu verwenden, erfasst Adobe Nutzungsmetriken und verwendet diese Metriken, um zu bestimmen, wie viel Kunden abrechnen müssen.

**1.4.24**

* **Persistente Netzwerkverbindung**

Wichtig: Sie müssen mindestens Adobe Flash Player Version 22 oder höher installiert haben.
Beständige Netzwerkverbindungen erstellen und speichern eine interne Liste von Netzwerkverbindungen, die für mehrere Anforderungen wiederverwendet werden können, anstatt für jede Netzwerkanforderung eine neue Verbindung zu öffnen. Persistente Netzwerkverbindungen sollten die Effizienz steigern und die Latenz im Netzwerkcode verringern.

In dieser Version wird diese Funktion in Apple Safari und Mozilla Firefox auf einem Mac nicht unterstützt.

**1.4.19**

* Stream-Integritätsunterstützung für VPAID-Anzeigen.
* Die Tab-Option &quot;Stummschaltung&quot;im Flash Player FP 20.0.0.267 für Firefox 42 und höher wurde aktiviert, indem das Problem mit dem Aufhängen behoben wurde.

**1.4.18**

* Das Primetime Desktop HLS TVSDK unterstützt jetzt die Erstellung von linearen VPAID 2.0-SWF-Kreativinhalten, um ein interaktives, interaktives Anzeigenerlebnis im Stream zu ermöglichen.

**1.4.10**

* **Ad Fallback, Daisy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103)** Bei VAST-Anzeigen (Kreativen) mit aktivierter Ausweichregel behandelt das TVSDK eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht, stattdessen Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Weitere Informationen finden Sie unter [Anzeigen-Fallback für VAST- und VMAP-Anzeigen](../programming/tvsdk-1.4-for-android/ad-insertion/ad-fallback/android-1.4-ad-fallback.md).

**1.4.8**

* **Video Heartbeats Library (VHL) aktualisiert auf Version 1.5**

   * Möglichkeit zum Senden von Metadaten mit Videostart und/oder Video/Anzeige/Kapitelstart als Kontextdaten
   * Weniger Netzwerk-Traffic: Heartbeats sind im Durchschnitt weniger und kleiner.

**1.4.7**

* **On-Premise-Individualisierungsunterstützung**

Unterstützung für On-Premise-Installationen von Adobe Individualization Server, um die Individualisierungsanforderung des Kunden so anzupassen, dass sie an einen anderen Endpunkt gesendet wird.

**1.4.6**

* **AES-Beispielverschlüsselung (Flash Player Version 17.0.0.134 erforderlich)**

Beispielbasierte AES-Verschlüsselung wird jetzt unterstützt.

**1.4.2**

* **Aktualisierung der Video Heartbeats Library (VHL) auf Version 1.4.0.1**

   * Es wurde die Möglichkeit hinzugefügt, verschiedene Analytics-Anwendungsfälle von anderen SDKs oder Playern mit den Adobe Analytics-Video-Grundlagen zu bündeln.
   * Das Anzeigen-Tracking wurde optimiert, indem die Methoden trackAdBreakStart und trackAdBreakComplete entfernt wurden. Die Werbeunterbrechung wird aus den trackAdStart - und trackAdComplete -Methodenaufrufen abgeleitet.
   * Die Eigenschaft &quot;playhead&quot;ist beim Tracking von Anzeigen nicht mehr erforderlich.

**1.4.0**

* **Blackout-Signalisierung mit Ersatz für alternativen Inhalt** Als Teil des TVSDK-Updates für 1.4 unterstützt das TVSDK jetzt auch das Wechseln in regionale Blackouts und das Zurückkehren aus linearen Inhalten. Das TVSDK kann jetzt zwei Manifestdateien parallel, Hauptdatei und alternative verarbeiten, um Blackout-Signale zu überwachen, selbst wenn anstelle der ursprünglichen Programmierung alternative Programmierung angezeigt wird.

* **C3-Anzeigen entfernen/ersetzen** Jetzt ist keine zusätzliche Vorbereitung erforderlich, um neue Anzeigen dynamisch in Video-On-Demand-Assets (VOD) einzufügen, die aus dem C3-Fenster herauskommen. Das TVSDK bietet jetzt eine API zum Entfernen benutzerdefinierter Inhaltsbereiche und zum dynamischen Einfügen neuer Anzeigen. Diese leistungsstarke neue Funktion ist auch in Fällen nützlich, in denen Live-/lineare Inhalte während der Übertragung bereitgestellt werden und sofort zur Verwendung als On-Demand-Inhalt abgerufen werden, ohne dass genügend Zeit bleibt, das Asset zu &quot;bereinigen&quot;.

## Gelöste Probleme {#resolved-issues}

>[!NOTE]
>
>Alle TVSDK-Kunden, die CRS verwenden, sollten dringend auf mindestens TVSDK 1.4.32 für iOS, Android und Desktop HLS aktualisieren. Bei diesem Upgrade handelt es sich um einen Abbruch, der die vorhandene App-Implementierung ersetzt. Überprüfen Sie nach dem Upgrade in einem Proxy-Tool (z. B. Charles) nach den kreativen CRS-URL-Anforderungen, um sicherzustellen, dass die Version im Pfad die Version 3.1 widerspiegelt. Beispiel:
>
>`https://adunit.cdn.auditude.com/assets/3p/v3.1/218747/94b/c1b/94bc1b964cc67e115a5a6781c7329b90_ee92607938ffff46b083121f044c2746.m3u8`

**Version 1.4.41**

* Zendesk #33777 - Localhost-Token-SWF für DHLS-Distribution-Build abgelaufen.

  Aktualisieren des localhost-Tokens für die PMP-Demo auf DHLS.

### Behobene Probleme in den vorherigen Versionen {#resolved-issues-previous}

**Version 1.4.38** (891)

* Zendesk #30731 - TVSDK gibt nicht mehrere VPAID-Anzeigen in einer AdBreak ab.

  Korrektur der Wiedergabe mehrerer VPAID-Anzeigen in einer AdBreak.

* Zendesk #29968 - Double Billboard.

  Der Videoplayer kann das letzte Segment eines Zeitraums wiederholen, wenn ein ABR-Wechsel stattfindet. Aus diesem Grund wurde manchmal das letzte Segment der Vorahne wiederholt. Dieses Problem wurde behoben.

**Version 1.4.35** (879)

* Zendesk #26058 - Unterstützt native VPAID-Ereignisse

**Version 1.4.33** (873)

* Zendesk #21701 - Senden Sie die ursprüngliche kreative URL für die CRS-Anforderung 1401 anstelle der normalisierten URL.

  Das Problem, dass bereits neu verpackte URLs zur Transkodierung angefordert werden, wurde gemäß den Anforderungen des CRS-Backend behoben.
* Zendesk #26197 - Anamorphe Komprimierung wird in der gewünschten Anzeigeauflösung nicht wiederholt.

  **Hinweis**: Dieses Problem erfordert Flash Player 24.0.0.194 oder höher.

  Das Problem, bei dem fehlende Einträge in den Seitenverhältnistabellen zur Berechnung der Ausgabebreite verwendet wurden, wurde behoben.

* Zendesk #26840 - HDCP-Erkennung schlägt in IE11 + Windows7 nach dem zweiten Versuch fehl.

  **Hinweis**: Dieses Problem erfordert Flash Player 24.0.0.218 oder höher.

  Dieses Problem wurde behoben, indem die Verarbeitung der Hauptnachrichten-Warteschlange von AdobeCP so geändert wurde, dass sie durch die gesamte Warteschlange iteriert wird, anstatt nur die allererste Nachricht zu blockieren.

* Zendesk #27460 - Das neue Akamai-Konto kann eine POST-CDN-Anfrage nicht verarbeiten.

  Das neue CDN-Konto kann eine POST-CDN-Anfrage nicht verarbeiten. Dieses Problem wurde behoben, indem der Code so aktualisiert wurde, dass die Anzeigenanforderung cdn.auditude.com anstelle von POST als GET angezeigt wurde.
* Zendesk #27619 - Flash-Absturz unter Windows 10

  **Hinweis**: Dieses Problem erfordert Flash Player 24.0.0.218 oder höher.

  Dieses Problem wurde behoben, indem ein Fehler aufgrund langer URLs verhindert wurde.

* Zendesk #28218 - Tracking-Ereignis wird nicht ausgelöst, während der Absturz vom Fortsetzungspunkt

  Dieses Problem ist dasselbe Problem wie in Zendesk #26592. Das Problem, bei dem Suchvorgänge zulässig waren, wenn sich der Medienplayer im Status &quot;VORBEREITET&quot;für VOD-Streams befindet, wurde behoben.

**Version 1.4.32** (867)

* Das Zendesk #26592-Tracking-Ereignis wird nicht ausgelöst, wenn die Wiedergabe ab dem Wiedergabezeitpunkt beginnt

Der Code aktualisierte das Pre-Roll-Werbeunterbrechungselement nicht, wenn der Wiederaufnahmepunkt nicht null war. Dieses Problem wurde durch Hinzufügen von Logik behoben, um den Code zu aktualisieren, wenn die Startzeiten des Bereichs nicht übereinstimmen.

* Zendesk #27022 Anzeigen werden nicht wiedergegeben, wenn ein Asset zum zweiten Mal wiedergegeben wird

Die Ausnahmen mit den Array-Methoden wurden behoben.

**Version 1.4.30** (855)

In dieser Version wurden die folgenden Probleme für TVSDK behoben:

* Zendesk #22898 - Fehlende Untertitel sollten nicht dazu führen, dass die Wiedergabe fehlschlägt.

**Hinweis**: Dieses Problem erfordert den Flash Player 23.0.0.185 oder höher.

Dieses Problem wurde behoben, indem TVSDK die Wiedergabe fortsetzen konnte, selbst wenn dem Manifest WebVTT M3U8 fehlt, und einfach eine Warnung registrieren.

* Zendesk #23454 - Anzeigen von Drittanbietern (VPAID) werden nicht korrekt verarbeitet

Dieses Problem wurde behoben, indem VPAID-Anzeigen ordnungsgemäß auf der Grundlage von Inhalts-IDs und nicht von Zeitbereichen verarbeitet wurden.

* Zendesk #24528 - TVSDK-Nutzungsmetriken für die Abrechnung.

Wichtig: Dieses Problem erfordert den Flash Player 23.0.0.185 oder höher.

* Problem mit verdeckten Untertiteln in Zendesk # 25432 beim Ändern der Größe des Players.

Wichtig: Dieses Problem erfordert den Flash Player 23.0.0.185 oder höher.

Der Texturmap-Code für die Beschriftungsanzeige wurde so korrigiert, dass die Koordinaten während der Größenanpassung des Players ordnungsgemäß verarbeitet werden.

Die Video Heartbeat Library (VHL) wurde auf Version 1.5.9 aktualisiert, um die folgenden Probleme zu beheben:

* Zendesk #23730 - Bitratenmetriken sind leer

Dieses Problem wurde behoben, indem die Bitratenänderungen in VideoAnalyticsTracker verfolgt wurden.

* Es wurde eine neue API, assetDuration, zu PTVideoAnalyticsTrackingMetadata hinzugefügt, um die Asset-Dauer für Live-/Linear-Streams zu aktualisieren.

**Version 1.4.28** (848)

* Zendesk #25027 - Auditude funktioniert in der Desktop-Version 1.4.27 nicht

Dieses Problem wurde behoben, indem der Code hinzugefügt wurde, um die AUDITUDE_METADATA_KEY zu überprüfen, und indem die AUDITUDE_METADATA_KEY und ADVERTISING_METADATA_KEY austauschbar gemacht wurden.

* Zendesk #24428 - Häufiges Pufferproblem bei Verwendung von TVSDK zum Abspielen eines DRM-HLS

Dieses Problem wurde behoben, indem berücksichtigt wurde, dass TVSDK die Verarbeitung beschleunigen kann, wenn keine Anzeige eingerichtet wird, indem das Pre-roll-Anzeigen-Halten und die Live-Reservierung in der Timeline, die zur Synchronisierung der Anzeigeneinfügung konzipiert ist, entfernt werden.

* Zendesk #24344 - Deaktivieren Sie WebVTT-Dateien, um die Startzeiten zu verbessern.

**Hinweis**: Dieses Problem erfordert Flash Player 23 oder höher.

Dieses Problem wurde behoben, indem die WebVTT-Dateien nur geladen wurden, wenn Beschriftungen angezeigt werden müssen.

* Zendesk #24994 - Verdeckte Untertitel werden beim Zurückkehren aus der Werbeunterbrechung vom Player abgesetzt

**Hinweis**: Dieses Problem erfordert Flash Player 23 oder höher.

Der falsche EOC-Code führte dazu, dass die Beschriftungsanzeige verschwand. Dieses Problem wurde behoben, indem die 608 Beschriftungscodes RU2, RU3 und RU4 gezwungen wurden, die korrekte Sichtbarkeit im aktuellen aktiven Fenster zu gewährleisten.

**Version 1.4.27** (844)

* Zendesk #21554 - TVSDK-Fehlerbeacons werden nicht für application-type = video/mp4 ausgelöst

Dieses Problem wurde behoben, indem TVSDK die korrekten Fehler-Tracking-URLs für ungültige Asset-Formate ping.

* Zendesk #23402 - Unvollständige Anzeigenwiedergabe

**Hinweis**: Dieses Problem erfordert Flash Player 23 oder höher.

Nach einem 404-Fehler bei bestimmten Anfragen kann ein Absturz auftreten. Dieses Problem wurde behoben, indem sichergestellt wurde, dass die Verbindung nicht heruntergefahren wird, während die Antwort verarbeitet wird. Die Lösung stellt sicher, dass die VPAID-Anzeigendateien nicht falsch gezählt werden, sodass sie beim Herunterladen nicht veröffentlicht werden.

* Zendesk #23621 - Retry schlägt in 400 und 404 fehl

**Hinweis**: Dieses Problem erfordert Flash Player 23 oder höher.

Fehlerkorrektur - Beim Wechseln zwischen verschiedenen Profilen treten jetzt keine DRM-Metadatenbeschädigungen mehr auf.

* Zendesk #23705 - Videoanzeigen frieren während AdStitched-Pausen

**Hinweis**: Dieses Problem erfordert Flash Player 23 oder höher.

Dieses Problem ist dasselbe Problem wie in Zendesk #23621.

* Zendesk #23905 - Manche Werbeunterbrechungen überspringen bei Werbeunterbrechungen

**Hinweis**: Dieses Problem erfordert Flash Player 23 oder höher.

Der native Windows-Netzwerkcode wurde behoben, um sicherzustellen, dass Verbindungen keine Handles schließen, die derzeit von anderen Verbindungen verwendet werden.

* Ticket #24029 - HLS FER-Streams geben nicht alle Mid-Roll-Anzeigen in der Mid-Roll-JSON-Datei wieder.

Dieses Problem wurde behoben, indem Clients benutzerdefinierte Parameter in der Opportunity-Instanz separat festlegen konnten, sodass Clients OpportunityGenerator nicht überschreiben mussten.

**Version 1.4.26** (839)

* Zendesk #18854 - Aktualisieren der kreativen Auswahllogik basierend auf CRS-Regeln
   * Unterstützung für die Aktualisierung der kreativen Auswahllogik basierend auf CRS-Regeln

* Zendesk #22725 - playManager.beginPlayback() -Implementierung in der Beispielanwendung für Desktop

   * Korrektur, indem dieser redundante Aufruf am Ende von startPlaybackFromFlashVars entfernt wird, da die Methode von setupVideo() aufgerufen wird.

* Zendesk #22807 - SeekManager - Null-Referenz-Ausnahme

   * Korrigiert durch die Bereitstellung des erforderlichen NULL-Zeigerschutzes innerhalb von SeekManager in Bezug auf _dispatcher

* Zendesk #22822 - Häufige Pufferung bei Verwendung von TVSDK zur Wiedergabe eines klaren HLS

   * Es wurde behoben, indem die anfängliche Chance, die von adSignalingModeOpportunityGenerator generiert wurde, entfernt wurde, wenn keine Anzeige vorhanden ist.

* Zendesk #23378 - Stream-Integritätsblöcke rules.xml

   * Behoben durch Laden der Datei rules.xml über den Workflow für die Stream-Integrität

**Version 1.4.24** (817)

* Zendesk #19851 - Wenn sich der Player an eine andere Bitrate anpasst, springt er einige Frames zurück in die neue Bitrate, was zu einem unangenehmen Erlebnis führt

**Hinweis**: Dieses Problem erfordert Flash Player 22.0.0.175 oder höher.

Das Problem, dass der DRM-Adapter nach dem Herunterladen eines kleinen Bruchs eines Segments nicht ordnungsgemäß wiederhergestellt wird, wurde behoben.

* Zendesk #20784 - Analytics: Auslösen von Inhaltsbeendigungen für Live-Videoübergänge

Dieses Problem wurde behoben, indem eine API (trackVideoComplete) hinzugefügt wurde, um den Abschluss von Inhalten während einer LINEAR/LIVE-Videoverfolgungssitzung manuell Trigger.

Die folgenden Bibliotheken wurden aktualisiert:

* Zendesk #21643 - VPAID-Anzeigen werden nicht vollständig wiedergegeben

   * AdobeMobile-Bibliothek auf 4.10.0
   * VHL-Bibliothek zu 1.5.6
   * VHL-Nielsen-Bibliothek zu 1.6.7

Dieses Problem wurde behoben, indem ein Viewport mit einer Höhe von null verwendet wurde, um die Bühne zu füllen, wenn eine VPAID-Anzeige wiedergegeben wird.

* Zendesk #22110 - Analytics: h hinzufügen:sc:ssl -Feld zu den Heartbeat-Tracking-Aufrufen

Die SSL-bezogenen Probleme wurden behoben und die VHL-Bibliothek, die in TVSDK verwendet wird, wurde auf die neueste Version aktualisiert.

* Zendesk #22608 - Video zeigt gelegentlich einen schwarzen Bildschirm an (Flash Player 22.0.0.175 oder höher erforderlich)

Während der adaptiven Bitrate zeigt das Neuladen des Videos mit der maximalen Bitratenbegrenzung gelegentlich einen schwarzen Bildschirm an, obwohl der Client Aktualisierungen zur Position sieht und sich der Client verhält, als würde er Inhalte wiedergeben.

**Version 1.4.23** (809)

* Zendesk #2887 - Problem beim Überspringen von Post-Roll-Anzeigen, wenn die Anzeigenregellogik auf das TVSDK angewendet wird

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.240 oder höher.

Das Problem, bei dem die Post-Roll-Anzeigen übersprungen wurden, wenn die Anzeigenregellogik auf das TVSDK angewendet wurde, wurde behoben.

* Zendesk #19863 - Ad with VPAID media file discarded

Wenn eine riesige Inline-Anzeige über mehrere Mediendateien mit einer VPAID-Anzeige als erste Anzeige verfügt, wird die Inline-Anzeige nicht für Live-Streams wiedergegeben. Dieses Problem wurde behoben, indem stattdessen eine andere Mediendatei abgerufen wurde.

* Zendesk #21021 - Verspätete Bindung Audio, das zu Wiederholungen von Audiosegmenten führt

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.240 oder höher.

Das Problem mit der Audiowiederholung wurde behoben.

* Zendesk #21125 - Rückkehr von Live/Lineare Anzeigenunterbrechung früh

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.240 oder höher.

Diese Version unterstützt die Rückkehr von einer Werbeunterbrechung frühzeitig vor der Wiedergabe der Werbeunterbrechung bis zum Abschluss. Die frühe Rückgabe wird durch ein benutzerdefiniertes Manifest-Tag angezeigt.

* Zendesk # 21369 Verspätete Bindung Audio verursacht eine inkonsistente Zeit

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.240 oder höher.

Das Problem mit der Audiowiederholung, das behoben wurde, hat dieses Problem ebenfalls behoben.

* Zendesk #21760, 20921 - Audio Video Desync on Seek.

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.240 oder höher.

Das Problem mit der Audiowiederholung wurde behoben.

* Zendesk #22024 - Fehler beim Ausführen des TVSDK

Das Problem, dass der Referenz-Player keinen Stream wiedergibt und beim Start eine Ausnahme auslöst, wurde behoben.

**Version 1.4.22** 791.

* Zendesk #17580 - Primetime-Laufzeitfehler mit Code 3357

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.197 oder höher.

Die zufälligen 3357-Fehler, die durch die ordnungsgemäße Initialisierung der deviceID beim Aufruf von storeVoucher() aufgetreten sind, wurden behoben.

* Zendesk #21334 - TVSDK-Wert für Zeitüberschreitung bei Anzeigenanfragen von Drittanbietern

In dieser Version wurde das globale Zeitlimit für Anzeigenanforderungen hinzugefügt.

**Version 1.4.21** 782.

* Zendesk #19580 TVSDK wartet vor dem Senden auf den Abschluss des Content Resolver `PTTimedMetadataChangedNotification` Benachrichtigungen

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.182 oder höher.

Dieses Problem wurde im Desktop Reference Player behoben, indem Anzeigen-Tags festgelegt und ein benutzerdefinierter Opportunity-Generator hinzugefügt wurde, der anzeigt, wie benutzerspezifische Hinweise abonniert werden können und wie diese Hinweise in einer VOD-Datei verarbeitet werden.

* Zendesk #20806 Zukünftige Mid-Roll-Anzeigen im DVR-Fenster werden nach dem Tausch von Cams nicht mehr Trigger

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.182 oder höher.

Dieses Problem wurde behoben, indem die App so aktualisiert wurde, dass _resource.metadata.setValue(DefaultMetadataKeys.ENABLE_LIVE_PREROLL, &quot;false&quot;) festgelegt wurde, um das Einfügen von Pre-roll-Anzeigen in einen PIP-Swap zu deaktivieren. Daher wird keine Pre-Roll-Gelegenheit generiert.

Eine Sortierfunktion wurde eingeführt, um die nicht sequenzielle Anzeigenplatzierung zu korrigieren, die zu einer negativen Hauptinhaltsdauer führte.

* Zendesk #20522: VPAID 2.0-Anzeigen können nicht übersprungen werden

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.182 oder höher.

* Dieses Problem wurde behoben, indem VPAID-Anzeigen während des Anzeigenversands übersprungen wurden.
* Wenn die Werbeunterbrechungsrichtlinie auf &quot;Überspringen&quot;festgelegt ist, werden weiterhin Anzeigen- und Werbeunterbrechungsereignisse gesendet. Der Player-Status ist inkonsistent.

Dieses Problem wurde behoben, um sich korrekt zu verhalten und Ereignisse nicht zu senden, wenn eine Werbeunterbrechung übersprungen wird.

* Zendesk #20955 Festlegen von Schlüssel-Wert-Paaren in der Eigenschaft customParameters über den Opportunity-Generator

**Hinweis**: Dieses Problem erfordert Flash Player 21.0.0.182 oder höher.

Die Auditude Request analysiert die AuditudeSettings für benutzerdefinierte Parameter beim Erstellen einer Anzeigeneinheit für Werbeanfragen.

Dieses Verhalten wurde geändert, um benutzerdefinierte Parameter aus dem Opportunity-Objekt in die Anfrage aufzunehmen. Außerdem können nicht mehrere Möglichkeiten mit verschiedenen benutzerdefinierten Parametern in einer Auditude-Anfrage gepackt werden.

* Zendesk #21227 - m3u8 schlägt durchgängig fehl

**Hinweis**: Dieses Problem erfordert den Flash Player 21.0.0.211 oder höher.

Dieses Problem wurde behoben, indem das TVSDK das Manifest (HLS-Unterprofile) ignorieren konnte, das den AC3-Codec enthält, den das TVSDK nicht unterstützt (Surround).

**Version 1.4.20** 762.

* Zendesk #19181 - Trick play fast forward to live point stürzt den Stream ab.

**Hinweis**: Dieses Problem erfordert den Flash Player 20.0.0.306 oder höher.

* Zendesk #19286 - Flash Player stürzte ab, während sie in einem FER-Stream hin- und hersuchten.

**Hinweis**: Dieses Problem erfordert den Flash Player 20.0.0.306 oder höher.

Die gelegentlichen Änderungen, die bei der Suche in Google Chrome aufgetreten sind, wurden durch das Herunterfahren der Abfragen behoben, wenn die Abfragen zu lange dauern, bis eine Antwort abgerufen wird, oder wenn der Socket heruntergefahren wird.

* Zendesk #19305 - Choppy-Wiedergabe beim Abspielen eines Streams mit A/V-Unterbrechungen aufgetreten.

**Hinweis**: Dieses Problem erfordert den Flash Player 20.0.0.306 oder höher.

Dieses Problem wurde durch Meldung einer Warnung behoben.

* Zendesk # 19359 - Flash Player ist aufgrund der Position von #EXT-X-FAXS-CM abgestürzt: -Attribut im Manifest auf Setebene.

Dieses Problem wurde behoben, als das Tag #EXT-X-FAXS-CM oben in der Wiedergabeliste angezeigt wurde, bevor einzelne Bitraten oder Segmente in der Wiedergabeliste angezeigt wurden.

* Zendesk #19489 - Fast Forward to Live Point stalls plugin (Live-Stream)

Dieses Problem ist mit Zendesk #19181 identisch.

* Zendesk #19699 - TVSDK kann nicht zwischen WebVTT-Untertitelspuren wechseln

Dieses Problem wurde behoben, indem der Player-Dump erstellt und das Manifest neu geladen wurde, wenn sich ein Tracking ändert, und indem das UTF8-Zeichenfolgenkonvertierungsproblem korrigiert wurde, das sich auf die Tracking-Namen der Double-Byte-WebVTT-Beschriftung auswirkte.

**Version 1.4.19** (1.4.19.738)

* Zendesk #18234 - Flash Player stürzt die Wiedergabe der Streams mit Unicode-Zeichenfolgen in CC ab

Dieses Problem erfordert Flash Player FP 20.0.0.267 oder höher und wurde behoben, indem die Unicode-Zeichenfolge ordnungsgemäß verarbeitet wurde.

* Zendesk #18304 - Stream Integrity Support for VPAID Ads

Diese Funktion erfordert Flash Player FP 20.0.0.267 oder höher und wurde in Version 1.4.19 eingeführt.

* Zendesk #18766 - Reference Player kann nicht lateinische Unicode-Zeichen in CC-Nachnamen nicht anzeigen

Diese Funktion erfordert Flash Player FP 20.0.0.267 oder höher und wurde behoben, indem die Unicode-Zeichenfolge ordnungsgemäß verarbeitet wurde.

* Zendesk #18804 - Player stürzt in Firefox 42 ab

Dieses Problem erfordert Flash Player FP 20.0.0.235 oder höher und ist dasselbe Problem wie Zendesk #18723.

* Zendesk #18864 - Absturz des vollständigen Flash Player-Plugins

Dieses Problem erfordert Flash Player FP 20.0.0.235 oder höher und ist mit Zendesk #18723 identisch.

* Zendesk #18998 - Wenn Audio- und Video-Zeitstempel nicht übereinstimmen, kam es zu einem endlosen Herunterladen von Segmenten bei Diskontinuität.

Dieses Problem wurde behoben, indem die Lücke zwischen Zeitstempeln und dem heruntergeladenen Inhalt ignoriert wurde.

* Zendesk #19093 - Mid-Roll-Anzeigen können nur einmal mit Live- und Full-Event-Wiederholungsinhalten (FER) angesehen werden. Diese Anzeigen können jedoch nicht erneut angesehen werden, wenn sie schnell weitergeleitet werden oder nach den Anzeigen suchen

Wenn in der standardmäßigen adPolicy-Auswahl von Primetime eine Mid-Roll-Anzeige überwacht wird, wird die adBreak beim Abschluss einer Suche nicht an die gewünschte Position verschoben. Um die Anzeige nach der Suche erneut wiederzugeben, muss die Anwendung die Funktion selectAdBreaksToPlay() überschreiben.

* Zendesk #19101 - Durch das Zurücksetzen in nicht aufgelöste Midroll-Anzeigen wird die Anzeigenplatzierung entfernt.

Dieses Problem wurde behoben, indem der Player die Zeit für die Wiedergabe von Metriken, die minimale OpportunityTime und die Timeline aktualisieren konnte.

* Zendesk #19102 - Probleme mit FER und Trick-Modus

Dieses Problem erfordert Flash Player FP 20.0.0.267 oder höher und wurde behoben, indem advertisingMetadata.adSignalingMode korrekt eingestellt wurde.

* Zendesk #19175 - Manchmal werden Vorahnen nicht angezeigt, wenn der Stream zum ersten Mal wiedergegeben wird.

Dieses Problem wurde behoben, indem eine neue API, adRequestTimeout, zu den AuditudeSettings für eine Zeitüberschreitung bei Anzeigenanfragen hinzugefügt wurde. Benutzer können jetzt das standardmäßige 10s-Anzeigenanforderungs-Timeout überschreiben.

**Version 1.4.18** (1.4.18.722)

* Zendesk #3324 - Primetime Ads Reporting verfolgt keine Werbeunterbrechungen, wenn in einem VMAP kein Anzeigenmedium vorhanden ist.

Wenn eine Werbeunterbrechung leer ist, wurden die Tracking-Ereignisse für den Start der Werbeunterbrechung und für das vollständige Tracking nicht gepingt. Dieses Problem wurde behoben, indem Werbeunterbrechungs-Pings für leere Werbeunterbrechungen wie VMAP AdBreak mit einem gültigen AdSource-Knoten gesendet wurden.

**Version 1.4.17** (1.4.17.702)

* Zendesk #17168 - Beschriftungen werden nach dem Umschalten der Sichtbarkeit zehn Sekunden lang nicht angezeigt

Dieses Problem wurde behoben, indem Unterstützung für das EXT-X-MEDIA-TIME-Tag für VTT-Untertiteldateien bereitgestellt wurde.

* Zendesk #17983 - Wenn keine Schlüssel für ein Manifest heruntergeladen werden, schlägt die gesamte Manifestwiedergabe fehl

**Hinweis**: Sie müssen mindestens über Flash Player FP 19.0.0.245 oder höher verfügen.

Wenn manchmal Live-Inhalte wiedergegeben werden, kann es im Manifest zu ungültigen Schlüsseln kommen (z. B. für Blackout-Zeiträume), aber andere Zeitbereiche verfügen möglicherweise über gültige Schlüssel und werden weiterhin wiedergegeben. Wenn zuvor ein in einem Manifest aufgelisteter Schlüssel nicht heruntergeladen werden konnte, schlug das gesamte Manifest fehl. Jetzt schlägt das Manifest nur fehl, wenn alle aufgelisteten Schlüssel nicht heruntergeladen werden können. Wenn einige Schlüssel gültig sind, einige dieser Schlüssel jedoch nicht heruntergeladen werden konnten, wird der Inhalt wiedergegeben. Wir werden immer noch scheitern, wenn wir versuchen, ein Segment zu spielen, das einen Schlüssel erfordert, den wir nicht haben.

* Zendesk #18554 - Stream Integrity trimmt die Cookies in einigen Fällen herunter

**Hinweis**: Sie müssen mindestens über Flash Player FP 19.0.0.245 oder höher verfügen.

Es wurde ein Fehler im Cookie-Manipulations-Code behoben, durch den Cookie-Werte abgeschnitten werden konnten.

**Version 1.4.16** (1.4.16.684)

* Zendesk #3732 - Unterstützung für Proxys in Chrome für Stream-Integrität hinzufügen (Flash Player FP 19.0.0.207 oder höher erforderlich)

Dies ist eine Verbesserung.

* Zendesk #4244 - Streaming-Probleme beim PTS-Rollover

Dieses Problem wurde behoben, indem Rollover erkannt und die Diskontinuität pro Nutzlasttyp verwaltet wurde und nicht im Allgemeinen.

* Zendesk #4487 - Tracking Linear Channel of Content

Dieses Problem wurde behoben, indem der Video Heartbeat-Tracker während einer linearen Stream-Wiedergabesitzung neu initialisiert wurde.

* Zendesk #17427 - Adobe Stream Integrity not working through a proxy on Chrome (Win7) ()

**Hinweis**: Die Lösung erfordert Flash Player FP 19.0.0.207 oder höher.

Dieses Problem ist mit Zendesk #3732 identisch.

* Zendesk #17907 - Lag on pHLS Live Stream mit Flash Player 19

**Hinweis**: Die Lösung erfordert Flash Player FP 19.0.0.207 oder höher.

Dieses Problem wurde behoben, indem die Live-Streams verarbeitet wurden, in denen sich die Domänen der TS-Dateien beim erneuten Laden des Live-Manifests ändern und die Dateien zweimal heruntergeladen wurden.

* Zendesk #17931 - Wiedergabe von HLS-Inhalten mit Verzögerung am Anfang fehlgeschlagen

**Hinweis**: Die Lösung erfordert Flash Player FP 19.0.0.207 oder höher.

Das Problem wurde behoben, indem in den ersten 2 Sekunden der ersten TS-Datei Streams ohne Audio verarbeitet wurden.

* Zendesk #17934 - Live-Streaming-Fehler mit Flash 19.0.0.185

**Hinweis**: Die Lösung erfordert Flash Player FP 19.0.0.207 oder höher.

Das Problem wurde behoben, indem Live-Streams mit zeitlichem Wechseln zwischen Audio- und Video-Frames auf Segmentgrenzen behandelt wurden.

* Zendesk #17973 - Neuester Flash Player 19.0.0.185 stürzt während des Mid-Roll ab

**Hinweis**: Die Lösung erfordert Flash Player FP 19.0.0.207 oder höher.

Das Problem wurde behoben, indem ungemischtes Audio mit Mid-Roll-Anzeigeneinfügung behandelt wurde. (Der Parserwechsel erfolgt, und der Inhalt wird zu jedem Zeitpunkt der Wiedergabe zur Mid-Roll-Anzeige oder mitten in der Anzeigenwiedergabe usw. überführt.)

* Zendesk #18049 - Absturz von Flash 19 mit Firefox 42 Beta

Dieses Problem ist dasselbe wie Zendesk #17973.

**Version 1.4.15** (1.4.15.678)

* Zendesk #4377: Lösen Sie das AD_BREAK_SKIPPED-Ereignis aus, wenn Sie eine Werbeunterbrechung aufgrund der Anzeigenrichtlinie überspringen.

Die Fehlerbehebung bestand darin, AD_BREAK_SKIPPED hinzuzufügen, wenn eine Anzeige übersprungen wird.

* Zendesk #4496 - Stream Integrity: Fehler 102100 mit Umleitungen zu tokenisierten Streams.

Die Korrektur bestand darin, Unterstützung für das Festlegen der AVNetworkConfiguration -Eigenschaft useCookieHeaderForAllRequests über das TVSDK hinzuzufügen.

* Zendesk #17179 - Flash Player stürzt bei mehreren SAP-Änderungen für verschlüsselte Inhalte ab.

Ein Absturz während der Wiedergabe verschlüsselter Inhalte wurde behoben.

**Hinweis**: Für die Fehlerbehebung ist Flash Player 19.0.0.200 oder höher erforderlich.

* Zendesk #17499 - How do we not remove midroll after watch but remove preroll from fer content

AdBreakTimelineItem (AdBreakTimelineItem.placementType) wurde ein Typ hinzugefügt, sodass AdPolicySelector eine andere Richtlinie für Pre-roll-, Mid-Roll- und Post-Roll-Inhalte zurückgeben kann.

* Zendesk #17665 - Bandbreitenbeschränkung

Die Korrektur bestand darin, die Logik zu entfernen, um die Zielpuffergröße bei Beginn der Pufferung auf die anfängliche Puffergröße zu ändern.

**Version 1.14.14** (1.4.14.771)

* Zendesk #17363 - Fix README-Dokumentation für Referenzplayer

   * Klarere Anweisungen zum Herunterladen und Installieren von playerglobal.swc.
   * Fügen Sie Anweisungen zum Aktualisieren der Projektkonfiguration mit einer bestimmten Flash Player-Version hinzu.
   * Aktualisieren Sie die AdvertisingOverlay-Projektkonfiguration, um die minimale Player-Version zu verwenden.
   * Aktualisieren der ReferenzCore-Projektkonfiguration für die Verwendung der Player-Version 11.9

* Zendesk #17471 - Player Freezes

Teilweise Korrektur für ein Problem, bei dem eine Anzeige nicht von Anfang an nach der Suche wiedergegeben wird.

* Zendesk #17496 - Podbuster wird bei der Suche im DVR-Fenster nicht aufgelöst

Stellen Sie benutzerdefinierte Parameter für jede Werbeunterbrechung bereit.

**Version 1.4.13** (1.4.13.660)

* Zendesk #4037 - No Useable Profile Error (Kein nutzbarer Profilfehler) (Flash Player 18.0.0.232 oder höher erforderlich)

URL-Parsing-Problem beheben, wenn der Abfrageparameter &quot;http&quot;enthält

* Zendesk #4260 - Flash Player 18 stürzt in IE11 ab (Flash Player 18.0.0.232 oder höher ist erforderlich)

Es wurde ein Absturz beim Abspielen von Videos im Vollbildmodus mit IE11 behoben

* Zendesk #4262 - Adobe Primetime-Player stürzt bei Windows 10 ab (Flash Player 18.0.0.232 oder höher ist erforderlich)

Fehlerkorrektur - Es wurde ein Absturz beim Abspielen von Videos im Vollbildmodus mit FireFox unter Windows behoben.

* Zendesk #4279 - HLS TVSDK-Anzeigeneinfügung -302 Umleitungsproblem auf iOS und Desktop

Es wurde ein Problem behoben, bei dem der Typ einer URL nicht richtig erkannt wurde, da sie keine Erweiterung hatte.

* Zendesk #4306 - Absturz des Flash Players nur bei Vollbildaufrufen unter Windows (erfordert Flash Player 18.0.0.232 oder höher)

Es wurde ein Absturz beim Abspielen von Videos im Vollbildmodus unter Windows behoben.

* Zendesk #4480 - Fehlende ID3-Tag-Ereignisse (Flash Player 18.0.0.232 oder höher erforderlich)

**1.4.12 **(1.4.12.656)

* Zendesk #2751 - CSAI und CRS | Verbesserung: Umgang mit dynamischen Elementen in bestimmten URLs von Mediendateien.

Der Creative Repackaging Service wurde aktualisiert, um Anzeigen mit dynamischen kreativen URLs ordnungsgemäß zu verarbeiten.

* PTPLAY - 2114 - Unterstützung für MP4-Wiedergabe.

Die grundlegende Wiedergabe von MP4-Inhalten wird jetzt unterstützt, einschließlich Wiedergabe, Pause und Suche.

Für Folgendes ist Flash Player 18.0.0.225 oder höher erforderlich:

* Zendesk #3992 - Zusätzliche TrickPlay-Geschwindigkeiten.

TrickPlay akzeptiert jetzt Raten über 16x: +/- 32, +/-64 und +/-128.

* Zendesk #3113 - Absturz des Flash Player-Plugins

Es wurde ein Absturz beim Versuch behoben, eine Weiterleitungsanzeige in Mac Firefox wiederzugeben.

* Zendesk #4037 - No Useable Profile Error
* Zendesk #4262 - Adobe Primetime-Player stürzt unter Windows 10 ab

Fehlerkorrektur - In Windows Firefox ist die Wiedergabe im Vollbildmodus jetzt nicht mehr unterbrochen.

**Version 1.4.11** (1.4.11.648)

* Zendesk #1869 - Problem Changing Font Size (erfordert Flash Player 18.0.0.200)

Lassen Sie die Verwendung von Untertitelgrößen im WebVTT-Untertitelcode zu.

* Zendesk #3113 - Flash Player-Plugin-Absturz (erfordert Flash Player 18.0.0.200)
* Zendesk #3268 - Desktop: Der Videoplayer flackert nach +- 40/50 Sekunden und beginnt nach +- 90 Sekunden schwarz zu werden (Flash Player 18.0.0.200 erforderlich)

Fehler beim Staging-Video behoben.

* Zendesk #3670 - INVALID_PARAMETER error in VOD during search im Referenz-Player (erfordert Flash Player 18.0.0.200)

InvalidateProfiles in ThreadSeek , wenn ein neuer Zeitraum erkannt wird.

* Zendesk #3896 - Flash Player-Absturz mit Stream-Integrity auf ON in Chrome (erfordert Flash Player 18.0.0.200)

Es wurde ein Absturz im nativen Netzwerkmodus in Pepper behoben

* Zendesk #3905 - TVSDK-Player wird nicht geladen, wenn er auf CDN gehostet wird

Es wurden Probleme behoben, durch die ein Platzhalter-Token gefunden wurde, wenn die pageDomain sich von der swf-Domäne unterscheidet.

**Version 1.4.10** (1.4.10.642)

* Zendesk #3249 - TVSDK Web Player stürzt Flash in Firefox ab

Es wurde ein gelegentlicher Flash Player-Absturz mit Firefox auf Mac behoben, der auftrat, wenn ein Stream, der auf einem externen Monitor wiedergegeben wurde, zu einem höheren Bitratenstream wechselte.(erfordert Flash Player 18.0.0.160)

* Zendesk #3268 - Desktop: Videoplayer flackert nach `+-` 40/50 Sekunden und beginnt nach schwarz zu werden `+-` 90 Sekunden

Es wurde ein Problem in Mac Chrome behoben, bei dem der Stream zunächst flackerte und schließlich schwarz wurde. (erfordert Flash Player 18.0.0.161)

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` Nicht befülltes Makro

   * Fehler-Code 400 wird angezeigt, wenn Inline-Werbung schlechte Kreativinhalte aufweist.
   * `[ERRORCODE]` Makro wird URL-kodiert

* Zendesk #3601 - Verbesserungsanfrage: Wrapper Companion Management

   * TVSDK zeigt Wrapper-Companion an, das Ressourcen enthält (HTML, iframe oder statisch ), die an das Inline-Netzwerk geschlossen werden. ( wenn die Inline keinen für diese Größe enthält)
   * Wrapperbegleiter mit Ressource werden ignoriert, wenn sie nicht für die Anzeige verwendet werden. (wird nicht für Tracking verwendet)
   * Für Tracking-Zwecke werden nur Wrapper-Begleiter mit NO-Ressource verwendet. ( Wrapper-Companion, die nur tracking enthalten )

**Version 1.4.9**

* Zendesk #2615 - Problem beim Entfernen der HLS-Ansicht vom Desktop-Display

Die Methode clearVideo() wurde zu MediaPlayer hinzugefügt. Löscht den angezeigten Videoframe, indem der AVStream aus dem StageVideo-Objekt gelöscht wird. Sollte nur aufgerufen werden, wenn das Video angehalten wurde, und replaceCurrentResource oder replaceCurrentItem muss aufgerufen werden, bevor play() erneut aufgerufen werden kann.

* Zendesk #3169 - Update des Referenz-Players mit Adobe Analytics-Integration

Der Referenz-Player wurde mit der Adobe Analytics-Integration aktualisiert.

* Zendesk #3296 - Desktop HLS TVSDK - VAST Drittanbieteranzeigen werden nicht wiedergegeben

MIME-Typen für das HLS-Format hatten zwischen Groß- und Kleinschreibung unterschieden. Dies war falsch und wurde geändert, sodass bei ihnen nicht mehr zwischen Groß- und Kleinschreibung unterschieden wird.

**Version 1.4.8**

* Zendesk #2737 - Desktop Player - Fehler 106000 (Flash Player 17.0.0.184 erforderlich)
* Zendesk #3007 - Pre-roll-Anzeigen werden nach der Aktualisierung auf Flash Player 17 nicht angezeigt (erfordert Flash Player 17.0.0.184)
* Zendesk #3085 - Desktop HLS Player gibt 106000 Fehler nach 60 Sekunden aus (Flash Player 17.0.0.184 erforderlich)

**Version 1.4.7**

* Zendesk #2760 - DISCONTINUITY-Tag, das während des TrickPlay-Modus ignoriert wird (Flash Player-Version 17.0.0.158 erforderlich)
* Zendesk #2760 - DISCONTINUITY-Tag, das während des TrickPlay-Modus ignoriert wird (Flash Player-Version 17.0.0.158 erforderlich)

**Version 1.4.6**

* Zendesk #2652 - Dokumentation zur Auditude für Desktop-HLS, geklärte Dokumentation zur Auditude media_id für Desktop-HLS

**Version 1.4.5**

* Zendesk #2256 - Access to Übergeordnet Playlist, aktualisiertes PSDK zum Senden von timedMetadata-Ereignissen für abonnierte Tags auf der Übergeordneten Wiedergabeliste. (erfordert Flash Player-Version 17.0.0.134)
* Zendesk #2417 - Player versucht, Untertitel vor dem Wiedergabebeginn herunterzuladen, verwendet WebVTT die falsche Segmentnummernvariable für die Segmentnummerübereinstimmung. Fehler wurden nur für Medien angezeigt, bei denen Segmentindizes bei null lagen. (erfordert Flash Player-Version 17.0.0.134)
* Zendesk #2537 - Flash-Player stürzt bei Verwendung des Ppper-Plug-ins mit Chrome ab (Flash Player-Version 17.0.0.134 erforderlich)
* Zendesk #2547 - Arabische Untertitel: Der Text sollte rechtsbündig ausgerichtet werden (Flash Player Version 17.0.0.134 erforderlich)

**Version 1.4.4**

* Zendesk #1561 - Re: `[Adobe Primetime]` Aktualisieren: HLS-Client-basierte Failover-Unterstützung für PROGRAM-DATE-TIME im Desktop-PSDK (Flash Player-Version 16.0.0.305 oder höher erforderlich)
* Zendesk #2197 - `[Ads]` Tracking von Anzeigenfehlern
* Zendesk #2286 - Feature Request: Informationen zum Ladestatus von Anzeigen (VPAID) angeben
* Zendesk #2285 - Feature Request: Überspringen einer Anzeige nach einer bestimmten Zeitüberschreitungsdauer
* Fehler #3921755 - Aktualisierung der OpenSSL-Bibliothek auf Version 1.0.1L in Flash Player (Flash Player Version 16.0.0.305 oder höher erforderlich)

**Version 1.4.2**

* Zendesk #1303 - Vertical Offset for Closed Caption (Flash Player Version 16.0.0.235 oder höher erforderlich, erwartetes Veröffentlichungsdatum: Dezember 2014)
* Zendesk #1870 - Closed Caption Turning On and Off (Geschlossene Beschriftung aktivieren und deaktivieren) (erfordert Flash Player-Version 16.0.0.235 oder höher, erwartetes Veröffentlichungsdatum: Dezember 2014)
* Zendesk #2110 - Die Wiedergabe hängt stecken, nachdem versucht wurde, während einer VPAID-Anzeige den Vollbildmodus zu aktivieren (Flash Player-Version 16.0.0.235 oder höher, erwartetes Veröffentlichungsdatum: Dezember 2014)
* Zendesk #2199 - `[VPAID]` Player reagiert nicht bei Suche nach vergangener Werbeunterbrechung
* Zendesk #2358 - Re: `[Analytics]` Falsche Kapiteldaten

**Version 1.4.1**

* Die Blackouts-API wurde aktualisiert und ist nun mit der Implementierung von Android und iOS konsistent.

**Version 1.4.0**

* Zendesk #1024 - Funktion zum Entfernen von Anzeigen aus dem Stream über Manifest
* Zendesk #1423 - HLS-Wiedergabefehler blockiert Flash Player (ohne Fehler gemeldet)
* Zendesk #1674 - ClosedCaption Nicht angezeigt, korrekte 708-Beschriftungsanzeige, wenn 0x03-ETX-Codes fehlen.

## Bekannte Probleme {#known-issues}

* Geschlossene Beschriftung funktioniert nicht mit Nur-Audio-Inhalten, da das Beschriftungssystem Video benötigt, um zu funktionieren.
Ohne Video gibt es keine Viewport-Dimension und ohne Viewport-Dimension können Sie keine Grafiken für Beschriftungen anzeigen.
* Die Stream-Integrität ist in Google Chrome aufgrund von Chrome-Sandbox-Einschränkungen etwas langsamer.
* Wenn Sie in TVSDK 1.4 autoPlay deaktivieren, kann ein DRM-Fehler auftreten, wenn der Player mindestens eine Minute lang inaktiv bleibt. Um dieses Problem zu umgehen, ändern Sie beim Deaktivieren von autoPlay, aber beim Vorausfüllen von Assets `ReferenceCore.as` durch Änderung des Inhalts von `onPlaybackManagerPrepared`:

```
if (_playbackManager.autoPlay) {
_playbackManager.play();
} else {
_playbackManager.play();
_playbackManager.pause();
}
```

* **Version 1.4.13** PTPLAY-8501 - Wenn VMAP zwei direkte MP4-Anzeigen zurückgibt, die nicht transkodiert sind, wird dieselbe Absturzanzeige zweimal wiedergegeben.

* **Version 1.4.2** In der Flash Player-Version 16 wurde ein Problem mit der ABR-Logik, die das Herunterschalten der Seite ermöglicht, erkannt, nachdem der Player in ein leeres Pufferereignis gelangt ist. Das Problem verhindert, dass die Bitrate in Umgebungen mit schlechter Bandbreite nach dem Pufferstatus des Players heruntergeschaltet wird. Um das Problem zu umgehen, muss Ihre App die `BufferControlParameters.initialBufferTime` identisch sein `BufferControlParameters.playbackBufferTime` vorübergehend während des Pufferstatus (d. h. auf einer `BufferEvent.BUFFERING_BEGIN` -Ereignis) und setzen Sie es dann zurück auf die festgelegten Werte unter `BufferEvent.BUFFERING_END` -Ereignis. Die Fehlerbehebung für dieses Problem wird in der nächsten Patch-Version von Flash Player Version 16 verfügbar sein.

* **Version 1.4.0**

   * PTPLAY-1634 - Das gleiche abonnierte Tag hat in verschiedenen Live-Fenstern unterschiedliche Zeitstempel. Wenn Live-Fenster verschoben werden, sollte dasselbe Tag in jedem von ihnen über dieselben Zeitstempel verfügen. Manchmal haben dieselben Tags jedoch unterschiedliche Zeitstempel.
   * PTPLAY-28 - Die MediaPlayer-Timeline enthält keine leeren Umbrüche.
   * Eine domänenübergreifende Richtliniendatei (crossdomain.xml) ist erforderlich, damit Inhalte von einer anderen Domäne gestreamt werden können. [Einrichten einer crossdomain.xml-Datei für HTTP-Streaming](https://helpx.adobe.com/adobe-media-server/dev/configure-dynamic-streaming-live-streaming.html).
   * Fehler #3694203 - In einem DVR-Stream kann die Suche aus einer Wiedergabe während der Wiedergabe in eine andere Mid-Roll-Anzeige zum Einfrieren des Browsers führen
   * Fehler #3753725 - selectPolicyForSeekIntoAd berücksichtigt nicht, wenn die Werbeunterbrechung gesehen wurde
   * Fehler #3754529 - Pre-Roll-Anzeigen werden nicht aus dem Stream entfernt, wenn Sie in einem Live-DVR-Stream wiedersuchen
   * Fehler 3761896 - Wenn die Suche während der Anzeigenwiedergabe zulässig ist, werden Anzeigenmarken nach der Suche neu angepasst. Problemumgehung ist die Verwendung des Rückrufs &quot;ITEM_UPDATED&quot;während der Suche nicht.
   * Fehler 3779889 - Der vollständige Aufruf wird nicht durchgeführt, wenn das Ende der Trick Play-Funktion in Video Analytics erreicht wird
   * Fehler #VA-779 - Der Ereignis-Heartbeat zur Bitratenänderung wird nicht für Enhanced Video Analytics mit Referenzimplementierung zur Heartbeat-Unterstützung gesendet - Trick play wird nicht in der Beispielanwendung implementiert.

## Hilfreiche Ressourcen {#helpful-resources}

* Die vollständige Hilfedokumentation finden Sie unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
