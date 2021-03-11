---
title: TVSDK 2.4.1 für Android-Versionshinweise
description: TVSDK 2.4.1 für Android Versionshinweise beschreiben die neuen und unterstützten Funktionen sowie die bekannten Probleme und Einschränkungen in TVSDK Android 2.4.1.
topic-tags: release-notes
products: SG_PRIMETIME
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '1963'
ht-degree: 0%

---


# TVSDK 2.4.1 für Android-Versionshinweise {#tvsdk-for-android-release-notes}

TVSDK 2.4.1 für Android Versionshinweise beschreiben die neuen und unterstützten Funktionen sowie die bekannten Probleme und Einschränkungen in TVSDK Android 2.4.1.

## TVSDK Android 2.4.1 {#tvsdk-android}

Adobe veröffentlicht TVSDK 2.4.1 für Android.

Um diese Version von TVSDK zu verwenden, stellen Sie sicher, dass Ihr System die unter [Systemanforderungen](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6) beschriebenen Anforderungen erfüllt.

Die Dokumentation finden Sie hier:

・ Online-Hilfesystem TVSDK 2.4 für Android-Hilfe

・ [Javadocs TVSDK 2.4 für Android Java API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)

Die Javadocs sind die ultimative Autorität, da sie automatisch direkt aus dem TVSDK-Quellcode generiert werden.

・ [C++ API-Dokumentation TVSDK 2.4 für Android C++ API](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

Jede Java-Klasse verfügt über eine entsprechende C++-Klasse. Die C++-Dokumentation enthält mehr erklärendes Material als die JavaAdocs. Lesen Sie daher die C++-Dokumentation, um ein tieferes Verständnis der Java-API zu erhalten.

・ Migrationshandbuch ([TVSDK 2.4 für Android Migration Guide](../migration-guides/tvsdk-14-25-android.md))

In diesem Handbuch wird beschrieben, was Sie ändern müssen, um eine Anwendung basierend auf TVSDK 1.4 zu einer Anwendung zu migrieren, die auf TVSDK 2.4 basiert.

## Neue Funktionen {#new-features}

TVSDK 2.4.1 für Android bietet viele Leistungsverbesserungen im Vergleich zu früheren Versionen. Es bietet eine hochwertige Anzeige.

Diese Version enthält alle Funktionen der Versionen 2.4 und 2.4.1 und es werden keine Funktionen mehr unterstützt.

Die wichtigsten neuen Funktionen in Version 2.4.1:

* HLS-Version 4-Funktionen

   * **Videowiedergabe**  (Wiedergabe, Pause, Suche) mit Player-Steuerung für Live-, Linear- und VOD-Streams.
   * **Untertitel.** TVSDK kann 608/708 Untertitel mit einer Auswahl an Schriftarten, Schriftgrößen, Farben und Hintergrund anzeigen. Es kann auch Videos mit Rollup-Beschriftungen unterstützen und zwischen Sprachspuren wechseln, sofern diese verfügbar sind.
   * **Trick play** Modeshows unterstützen schnelle Vorwärts- und Rückspulen für HLS-Streams, die I-Frames verwenden. Alle Steuerelemente für die Videowiedergabe funktionieren auf dem Inhalt. Für den externen Videowiedergabemodus ist Slow-Motion (forward) mit Raten zwischen 0 und 1 verfügbar.
   * **Mit der adaptiven Bitrate (ABR)** kann der Player anhand von Netzwerk- und anderen Bedingungen dynamisch festlegen, welche von mehreren Versionen desselben Inhaltsstreams wiedergegeben werden sollen. Sie können Parameter dynamisch oder in der Manifestdatei festlegen, um zwischen aggressiven, mäßigen und konservativen Auswahlrichtlinien zu wählen.
   * **Byte-** Übergänge ermöglichen es einer einzelnen TS-Datei, mehrere TS-Segmente zu enthalten.
   * **Alternative Audiowiedergabe** ermöglicht es dem Player, zwischen verfügbaren Audiospuren zu wechseln.
   * **ID3-Unterstützung.** TVSDK kann HLS-Audio- und Videostreams mit ID3-Audio-Metadaten wie Künstlername, Titel und Album wiedergeben.
   * **Failover. **TVSDK verwendet Strategien, um die unterbrechungsfreie Wiedergabe fortzusetzen, obwohl Hostserver, Wiedergabelisten und Segmente fehlschlagen.
   * **Multi-Kanal Audio-Pass-Through (DD+).** TVSDK kann Dolby Digital Plus-Audiodaten (E-AC3) an unterstützende Hardware weitergeben.

* Inhaltsschutzfunktionen

   * **DRM für HLS.** Alle Video-Wiedergabe-APIs funktionieren mit verschlüsselten Videoinhalten, die durch Adobe Access geschützt sind. Die folgenden DRM-Funktionen werden unterstützt:

      * Lizenzrotation
      * Schlüsselrotation
      * Lizenzzwischenspeicherung
      * Richtlinienzeit
      * IV Drehung

* **AES 128-Wiedergabe.** TVSDK kann erweiterte Verschlüsselungsstandard (AES) HLS-Inhalte mit Schlüsselgröße von 128 Bit abspielen.
* **Protected HLS (PHLS)** bietet eine begrenzte Anzahl vordefinierter DRM-Richtlinien, eine Untergruppe der Funktionen von Adobe Access, um leichtes DRM über HLS für Live- und VOD-Streams zu ermöglichen.

* Funktionen für Werbung/alternative Inhalte und Monetarisierung

   * **Verfolgung von serverseitig eingefügten Anzeigen.** TVSDK kann Anzeigen verfolgen, die vom Adobe Cloud-Anzeigeneinfügedienst eingefügt wurden. Es unterstützt lineare Anzeigen in den Formaten VAST2, VAST3 und VMAP für VOD und Live/Lineare Streams.
   * **Benutzerdefinierte HLS-Tags.** TVSDK verwendet seine  `MediaPlayerConfig` Klasse, um die Benachrichtigung der Player-Anwendung zu aktivieren, wenn benutzerdefinierte HLS-Tags im Stream angezeigt werden.
   * **Einfügen clientseitiger Anzeigen** Die Zielgruppenbibliothek für Einfügen und Einfügen funktioniert mit Adobe Auditude-Servern, um Anzeigen für das dynamische Einfügen in Live-, Linear- und VOD-Inhalte bei Pre-Roll-, Mid-Roll- oder Post-Roll-Positionen aufzulösen.
   * **Benutzerdefinierte Anzeigenauflöser.** Die  `ContentResolver, OpportunityGenerator,` und  `MediaPlayerClientFactory` Schnittstellen ermöglichen es Ihnen, einen benutzerdefinierten Content-Resolver zu implementieren und einen benutzerdefinierten Opportunitätsdetektor für die Arbeit mit TVSDK zu registrieren. Die Klassen `TestAdResolver` und `AuditudeResolver` bieten C++-Beispiele für die Implementierung eines Inhaltsauflösers. Sie finden ein JavaScript-Beispiel unter `samples/jspsdk/testapp/psdk.js`.
   * **Konsistentes Anzeigenverhalten.** Verwenden Sie die  `AdPolicySelector` Oberfläche, um ein konsistentes Verhalten aller Player für Vorgänge wie Suchen und Trick Play zu aktivieren, wenn Anzeigen im Inhalt vorhanden sind. Wenn Sie keine eigene Implementierung durchführen, verwendet TVSDK `DefaultAdPolicySelector`.
   * **Entfernen/ersetzen Sie C3-Anzeigen.** Verwenden Sie die entsprechende TVSDK-API, um benutzerdefinierte Inhaltsbereiche zu entfernen und neue Anzeigen ohne zusätzliche Vorarbeit dynamisch einzufügen. Dies ist praktisch, wenn Live-/Lineare Inhalte gesendet und dann sofort ohne Bereinigung auf Anfrage verfügbar gemacht werden.

Die wichtigsten neuen Funktionen Version 2.4:

* **Sofortiges Aktivieren von VOD und** liveWenn Sie die Option &quot;Sofort aktivieren&quot;aktivieren, initialisiert und puffert das TVSDK Medien vor dem Beginn der Wiedergabe. Da Sie mehrere `MediaPlayerItemLoader`-Instanzen gleichzeitig im Hintergrund starten können, können Sie mehrere Streams puffern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird die Wiedergabe sofort auf den Beginn des neuen Kanals wiedergegeben. TVSDK 2.4 unterstützt auch das Instant On für Live-Streams. Die Live-Streams werden erneut gepuffert, wenn das Live-Fenster verschoben wird.

* **Leistungsverbesserungen **Die neue TVSDK 2.4-Architektur bietet verschiedene Leistungsverbesserungen:

   * **Untersegmentierung** : TVSDK reduziert die Größe der einzelnen Fragmente so schnell wie möglich auf die Wiedergabe im Beginn.
   * **Parallele Anzeigendownloads** : TVSDK ruft Anzeigen parallel zur Inhaltswiedergabe ab, bevor die Werbeunterbrechungen angeklickt werden, sodass Anzeigen und Inhalte nahtlos wiedergegeben werden können.
   * **Verzögerte Anzeigenauflösung**  - Mit dieser Funktion warten wir nicht auf die Auflösung von Nicht-Preroll-Anzeigen, bevor die Wiedergabe beginnt, und verringern so die Startzeit. APIs wie Suchen und Trick-play sind immer noch nicht zulässig, bis alle Anzeigen aufgelöst sind.

* **MP4-Inhaltswiedergabe**

Diese Version von TVSDK unterstützt die Wiedergabe von MP4 als Hauptinhalt.

* **Persistente Netzwerkverbindungen**

TVSDK unterhält eine Reihe von wiederverwendbaren Netzwerkverbindungen, sodass es nicht den Mehraufwand für die Erstellung und Zerstörung einer Netzwerkverbindung für jede Netzwerkanforderung verursacht.

* **Auflösungsbasierter Ausgabeschutz**

Diese Funktion verknüpft die Wiedergabebeschränkungen mit bestimmten Auflösungen und bietet feinere DRM-Steuerelemente.

* **Trick play with adaptive bit rate (ABR)**

Diese Funktion ermöglicht es TVSDK, während des Tricks Play-Modus zwischen iFrame-Streams zu wechseln. Sie können Profil ohne iFrame verwenden, um Tricks mit geringeren Geschwindigkeiten auszuführen.

* **Smoother Trick Play**

Diese Verbesserungen verbessern die Benutzerfreundlichkeit:

・ Adaptive Auswahl der Bitrate und Bildrate während der Trick-Wiedergabe, basierend auf Profil von Bandbreite und Puffer

・ Verwenden Sie den Hauptstrom anstelle des IDR-Streams, um eine schnelle Wiedergabe mit bis zu 30 fps zu erzielen.

* **Verbesserte ABR-Logik**

Die neue ABR-Logik basiert auf der Pufferlänge, der Änderungsrate der Pufferlänge und der gemessenen Bandbreite. Dadurch wird sichergestellt, dass die ABR die richtige Bitrate wählt, wenn die Bandbreite schwankt, und auch die Anzahl der auftretenden Bitratenwechsel optimiert wird, indem die Rate überwacht wird, mit der sich die Pufferlänge ändert.

* **Rechnungsstellung**

TVSDK sammelt automatisch Metriken, wobei der Kaufvertrag des Kunden eingehalten wird, um regelmäßige Nutzungsberichte zu erstellen, die für die Abrechnung erforderlich sind. Auf jedem Stream-Beginn-Ereignis verwendet TVSDK die Adobe Analytics-Dateneinfüge-API, um Abrechnungsmetriken wie Inhaltstyp, durch Anzeigeneinfügung aktivierte Flags und DRM-aktivierte Flags - je nach Dauer des abrechnungsfähigen Streams - an die eigene Report Suite von Adobe Analytics Primetime zu senden. Dies beeinträchtigt oder wird nicht in die eigenen Adobe Analytics Report Suites oder Server-Aufrufe des Kunden aufgenommen. Auf Anfrage wird dieser Bericht zur Rechnungsnutzung regelmäßig an Kunden gesendet. Dies ist die erste Phase der Abrechnungsfunktion, die nur die Nutzungsabrechnung unterstützt. Sie kann mithilfe der in der Dokumentation beschriebenen APIs auf Grundlage des Kaufvertrags konfiguriert werden.

## Unterstützte Funktionen {#supported-features}

TVSDK für Android 2.4 unterstützt eine Reihe von Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.

>[!NOTE]
>
>In den Funktionsmatrix-Tabellen unten bedeutet eine Ö, dass die Funktion in der aktuellen Version unterstützt wird.

### Hauptwiedergabefunktionen {#core-playback-features}

| **Funktion** | **Inhaltstyp** | **HLS** | **DASH** |
|---|---|---|---|
| Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | VOD + Live | √ | Ö (nur VOD) |
| FER - Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | FER VOD | √ | Nicht unterstützt |
| MP3 | VOD | Nicht unterstützt | Nicht unterstützt |
| MP4-Inhaltswiedergabe | VOD | √ | √ |
| Adaptive Bit Rate Switching Logic | VOD + Live | √ | Nicht unterstützt |
| Wiedergabe nur Audio | VOD + Live | √ | Nicht unterstützt |
| Untertitel - 608/708 | VOD + Live | √ | Ö (nur VOD) |
| Untertitel - WebVTT | VOD + Live | √ | Ö (nur VOD) |
| Manifest-Failover | VOD + Live | √ | Ö (nur VOD) |
| Erweiterte Failover | VOD + Live | √ | Ö (nur VOD) |
| Servicequalitäts- und Player-Benachrichtigungen | VOD + Live | √ | Ö (nur VOD) |
| Unterstützung für Cookie-Kopfzeilen | VOD + Live | √ | Ö (nur VOD) |
| Unterstützung für benutzerdefinierte Kopfzeilen | VOD + Live | Nicht unterstützt | Nicht unterstützt |
| Puffersteuerungsparameter festlegen | VOD + Live | √ | Ö (nur VOD) |
| Festlegen der Steuerelemente für adaptive Bitraten | VOD + Live | √ | Ö (nur VOD) |
| Benutzerdefinierte Manifest-Tags (HLS)/Ereignis-Streams (DASH) | VOD + Live | √ | Ö (nur VOD) |
| Spätes gebundenes Audio | VOD + Live | √ | Ö (nur VOD) |
| 302 Umleitung | VOD + Live | √ | Ö (nur VOD) |

### Erweiterte Wiedergabe-Funktionen {#advanced-playback-features}

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td> 
   <td><strong>Inhaltstyp</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Wiedergabe mit Versatz</td> 
   <td>Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Wiedergabe nur Audio</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Trick Play </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Glattes Trick Play (mit ABR)</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>ID3-Analyse (HLS) / Timed Metadata (DASH)</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Blackouts </td> 
   <td>VOD + Live</td> 
   <td>Nicht unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Sofort ein</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Unterstützung für Diskontinuitätsmarker (HLS) </li> 
     <li>Mehrzeit (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>302 Umleitungs-Stickiness</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Ö (nur VOD)</td> 
  </tr>
  <tr>
   <td>Miniaturansicht-Scrubbing (Iframe und JPEG)</td> 
   <td>VOD + Live</td> 
   <td>Nicht unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Stream-Integrität </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
 </tbody>
</table>

### Hauptfunktionen der Ad Insertion (CSAI) {#core-ad-insertion-features-csai}

| **Funktion** | **Inhaltstyp** | **HLS** | **DASH** |
|---|---|---|---|
| Allgemeine Wiedergabe, Anzeige aktiviert | VOD + Live | √ | Ö (nur VOD-Vorrollen) |
| FER-Inhalt mit aktivierten Anzeigen | VOD | √ | Nicht unterstützt |
| Standardverhalten von Werbeanzeigen | VOD + Live | √ | Ö (nur VOD-Vorrollen) |
| VAST 2.0/3.0 | VOD + Live | √ | Ö (nur VOD-Vorrollen) |
| VMAP 1.0 | VOD + Live | √ | Ö (nur VOD-Vorrollen) |
| MP4-Anzeigen | VOD + Live | Ö (aus CRS) | Ö (aus CRS, nur Vorrollen) |

### Erweiterte Ad Insertion-Funktionen (CSAI) {#advanced-ad-insertion-features-csai}

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td> 
   <td><strong>Inhaltstyp</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Trick Play mit aktivierten Anzeigen</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Nur Anzeige </td> 
   <td>VOD</td> 
   <td>Nicht unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Targeting-Parameter</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte Parameter</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>Benutzerdefiniertes Anzeigenverhalten</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte Anzeigen-Tags</td> 
   <td>Live</td> 
   <td>√ </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte Anzeigenauflösungen</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Freirad benutzerdefinierter Anzeigenauflösung</td> 
   <td>VOD</td> 
   <td>Nicht unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>C3 Anzeigenaustausch </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Verzögertes Laden von Werbeanzeigen</td> 
   <td>VOD</td> 
   <td>√ </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Unterstützung von Diskontinuitätsmarken - SSAI (HLS) </li> 
     <li>Mehrzeit (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ergänzende Anzeigen, Banneranzeigen und anklickbare Anzeigen</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>VPAID 2.0</td> 
   <td>VOD + Live</td> 
   <td>Ö (JS) </td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>Vorzeitiger Anzeigenausstieg</td> 
   <td>Live</td> 
   <td>√ </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Regelbasierte kreative VOD + Livebriorisierung</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>CRS-Regeln </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Nicht unterstützt</td> 
  </tr>
 </tbody>
</table>

## Inhaltsschutzfunktionen {#content-protection-features}

| **Funktion** | **Inhaltstyp** | **HLS** | **DASH** |
|---|---|---|---|
| AES-Verschlüsselung | VOD + Live | √ | Ö (nur VOD) |
| Beispiel-AES-Verschlüsselung | VOD + Live | √ |  |
| Tokenisierte Streams | VOD + Live | √ |  |
| DRM | VOD + Live | Nur Primetime-DRM (Zukunft: Widevine) | Nur widew |
| Externe Wiedergabe (RBOP) | VOD + Live | Nur Primetime-DRM | Nicht unterstützt |
| Lizenzdrehung | VOD + Live | Nur Primetime-DRM | Nicht unterstützt |
| Schlüsseldrehung | VOD + Live | Nur Primetime-DRM | Nicht unterstützt |

### Integrationsfunktionen {#integration-features}

| **Funktion** | **Inhaltstyp** | **HLS** | **DASH** |
|---|---|---|---|
| Adobe Analytics VHL-Integration | VOD + Live | √ | √ |
| Rechnungsstellung | VOD + Live | √ | Nicht unterstützt |

## Nicht unterstützte Funktionen{#features-not-supported}

Diese Version von TVSDK unterstützt nicht:

* Werbeunterbrechung.
* Langsame Bewegung im Trick-Spiel.
* Suchen und Trickplay mit MP4-Inhalt.
* Anzeigeneinfügung mit MP4-Hauptinhalt.
* Suchen Sie nach der Wiedergabe einer Anzeige.
* Wiedergabe von Anzeigen mit reinen Audiomedien.

## Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

Diese Version von TVSDK hat folgende Probleme:

* Gerätespezifisch (Samsung Galaxy Tab 4) stürzt VOD DRM LBA mit Auditude ab und klickt auf Anzeigen
* Post-Roll-Anzeigen werden für einen bestimmten Inhalt nicht wiedergegeben.
* Das Festlegen der Untertitel auf CJK-Sprachen funktioniert nicht.
* Videos können aus dem Trick-Modus automatisch zwischen VOD und Live herauskommen.
* VHL - Falsche Heartbeat-Aufrufe werden gesendet, wenn ein Inhalt aus einem Offset Beginn wird.
* Bei der Wiedergabe von VPAID-Anzeigen fehlen VHL-Heartbeat-Aufrufe für Ereignis:type:play-Anzeige.
* Pre-Roll-Anzeige wird auch dann wiedergegeben, wenn die adBreakPolicy-SKIP ausgewählt wurde.
* Nach dem Wechsel zum Complete-Status-Player kehrt mit SKIP adBreakPolicy für Post-Roll-Anzeigen zum Wiedergabestatus zurück.

Ohne Video gibt es keine Viewport-Dimension und ohne Viewport-Dimension können keine Grafiken für Beschriftungen angezeigt werden.

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).