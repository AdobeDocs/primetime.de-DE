---
title: TVSDK 2.4.1 für Android - Versionshinweise
description: In den Versionshinweisen zu TVSDK 2.4.1 für Android werden die neuen und unterstützten Funktionen sowie die bekannten Probleme und Einschränkungen in TVSDK Android 2.4.1 beschrieben.
topic-tags: release-notes
products: SG_PRIMETIME
exl-id: 3de09048-ae32-43b4-a019-34b217931a4c
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '1962'
ht-degree: 0%

---

# TVSDK 2.4.1 für Android - Versionshinweise {#tvsdk-for-android-release-notes}

In den Versionshinweisen zu TVSDK 2.4.1 für Android werden die neuen und unterstützten Funktionen sowie die bekannten Probleme und Einschränkungen in TVSDK Android 2.4.1 beschrieben.

## TVSDK Android 2.4.1 {#tvsdk-android}

Adobe veröffentlicht TVSDK 2.4.1 für Android.

Um diese Version von TVSDK zu verwenden, stellen Sie sicher, dass Ihr System die unter [Systemanforderungen](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6).

Hier finden Sie die Dokumentation:

・ Online-Hilfesystem TVSDK 2.4 für Android-Hilfe

・ [Javadocs TVSDK 2.4 für Android Java API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)

Die Javadocs sind die ultimative Autorität, da sie automatisch direkt aus dem TVSDK-Quellcode generiert werden.

・ [C++ API-Dokumentation TVSDK 2.4 für Android C++ API](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

Jede Java-Klasse verfügt über eine entsprechende C++-Klasse. Die C++-Dokumentation enthält mehr erklärendes Material als die Javadocs. Weitere Informationen zur Java-API finden Sie in der C++-Dokumentation .

・ Migrationsleitfaden ([TVSDK 2.4 für Android-Migrationshandbuch](../migration-guides/tvsdk-14-25-android.md))

In diesem Handbuch wird beschrieben, was Sie ändern müssen, um eine Anwendung, die auf TVSDK 1.4 basiert, zu einer Anwendung zu migrieren, die auf TVSDK 2.4 basiert.

## Neue Funktionen {#new-features}

TVSDK 2.4.1 für Android bietet viele Leistungsverbesserungen gegenüber früheren Versionen. Es bietet ein hochwertiges Anzeigeerlebnis.

Diese Version enthält alle Funktionen der Versionen 2.4 und 2.4.1, und keine Funktionen werden mehr unterstützt.

Hier finden Sie die wichtigsten neuen Funktionen in Version 2.4.1:

* HLS-Version 4-Funktionen

   * **Videowiedergabe** (Wiedergabe, Pause, Suche) mit Player-Kontrolle für Live-, Linear- und VOD-Streams.
   * **verdeckte Untertitel.** TVSDK kann 608/708 geschlossene Untertitel mit einer Auswahl an Schriftarten, Schriftgrößen, Farben und Hintergrund anzeigen. Es kann auch Videos mit Rollup-Beschriftungen unterstützen und zwischen Sprachspuren wechseln, sofern diese verfügbar sind.
   * **Wiedergabemodus auswählen** unterstützt schnelle Vorwärts- und Rückspulen für HLS-Streams, die I-Frames verwenden. Alle Steuerelemente für die Videowiedergabe funktionieren auf dem Inhalt. Langsame Bewegung (Vorwärts) ist für den externen Videowiedergabemodus mit Raten zwischen 0 und 1 verfügbar.
   * **Adaptive Bitrate (ABR)** ermöglicht dem Player, basierend auf Netzwerk- und anderen Bedingungen dynamisch auszuwählen, welche von mehreren Versionen desselben Inhalts-Streams wiedergegeben werden sollen. Sie können Parameter dynamisch oder in der Manifestdatei festlegen, um unter aggressiven, moderaten und konservativen Auswahlrichtlinien auszuwählen.
   * **Byte-Bereiche** aktivieren Sie eine einzelne TS-Datei, die mehrere TS-Segmente enthält.
   * **Alternative Audioausgabeformate** den Player aktivieren, um zwischen verfügbaren Audiospuren zu wechseln.
   * **ID3-Unterstützung.** TVSDK kann HLS-Audio- und Videostreams mit ID3-Audio-Metadaten wie Künstlername, Titel und Album wiedergeben.
   * **Failover. **TVSDK verwendet Strategien, um die unterbrechungsfreie Wiedergabe trotz Fehlern von Host-Servern, Wiedergabelisten und Segmenten fortzusetzen.
   * **Mehrkanal-Audio-Pass-Through (DD+).** TVSDK kann Dolby Digital Plus Audio (E-AC3)-Daten an unterstützende Hardware übergeben.

* Inhaltsschutzfunktionen

   * **DRM für HLS.** Alle Videowiedergabe-APIs funktionieren mit verschlüsselten Videoinhalten, die durch Adobe Access geschützt sind. Die folgenden DRM-Funktionen werden unterstützt:

      * Lizenzwechsel
      * Schlüsselrotation
      * Lizenzzwischenspeicherung
      * Policy time
      * IV Rotation

* **AES 128-Wiedergabe.** TVSDK kann HLS-Inhalte des erweiterten Verschlüsselungsstandards (AES) mit einer Schlüsselgröße von 128 Bit wiedergeben.
* **Geschützte HLS (PHLS)** bietet eine begrenzte Anzahl vordefinierter DRM-Richtlinien, eine Untergruppe der Funktionen von Adobe Access, um einfache DRM über HLS für Live- und VOD-Streams zu ermöglichen.

* Funktionen für Werbung/alternative Inhalte und Monetarisierung

   * **Tracking für serverseitig eingefügte Anzeigen.** TVSDK kann durch den Adobe Cloud-Anzeigeneinfüge-Dienst eingefügte Anzeigen verfolgen. Es unterstützt lineare Anzeigen in VAST2-, VAST3- und VMAP-Formaten für VOD- und Live/Linear-Streams.
   * **Benutzerdefinierte HLS-Tags.** TVSDK verwendet seine `MediaPlayerConfig` -Klasse, um die Benachrichtigung der Player-Anwendung zu aktivieren, wenn benutzerdefinierte HLS-Tags im Stream angezeigt werden.
   * **Client-seitige Anzeigeneinfügung.** Die Auditude-Anzeigeneinfüge-Bibliothek arbeitet mit Adobe Auditude-Servern zusammen, um Anzeigen für das dynamische Einfügen in Live-, Linear- und VOD-Inhalte bei Pre-Roll-, Mid-Roll- oder Post-Roll-Positionen aufzulösen.
   * **Benutzerdefinierte Anzeigenauflöser.** Die `ContentResolver, OpportunityGenerator,` und `MediaPlayerClientFactory` -Schnittstellen ermöglichen es Ihnen, einen benutzerdefinierten Inhalts-Resolver zu implementieren und einen benutzerdefinierten Opportunity-Detektor für die Verwendung mit TVSDK zu registrieren. Die `TestAdResolver` und `AuditudeResolver` -Klassen bieten C++-Beispiele für die Implementierung eines Content Resolver. Ein JavaScript-Beispiel finden Sie unter `samples/jspsdk/testapp/psdk.js`.
   * **Konsistentes Anzeigenverhalten.** Verwenden Sie die `AdPolicySelector` -Schnittstelle verwenden, um ein konsistentes Verhalten aller Player für Vorgänge wie Suchen und Trick Play zu ermöglichen, wenn Anzeigen im Inhalt vorhanden sind. Wenn Sie Ihre eigene Implementierung nicht vornehmen, verwendet TVSDK `DefaultAdPolicySelector`.
   * **Entfernen/ersetzen Sie C3-Anzeigen.** Verwenden Sie die entsprechende TVSDK-API, um benutzerdefinierte Inhaltsbereiche zu entfernen und neue Anzeigen dynamisch einzufügen, ohne dass zusätzliche Vorbereitungsarbeiten erforderlich sind. Dies ist praktisch, wenn Live-/lineare Inhalte übertragen und dann sofort ohne Bereinigung auf Anfrage zur Verfügung gestellt werden.

Hier finden Sie die wichtigsten neuen Funktionen der Version 2.4:

* **Sofortiges Aktivieren für VOD und Live** Wenn Sie Sofort aktivieren, initialisiert und puffert das TVSDK Medien vor dem Start der Wiedergabe. Da mehrere `MediaPlayerItemLoader` Instanzen gleichzeitig im Hintergrund, können Sie mehrere Streams puffern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, beginnt die Wiedergabe auf dem neuen Kanal sofort. TVSDK 2.4 unterstützt auch das Instant On für Live-Streams. Die Live-Streams werden beim Verschieben des Live-Fensters erneut gepuffert.

* **Leistungsverbesserungen **Die neue TVSDK 2.4-Architektur bietet verschiedene Leistungsverbesserungen:

   * **Untersegmentierung** - TVSDK reduziert die Größe jedes Fragments weiter, um die Wiedergabe so bald wie möglich zu starten.
   * **Parallele Anzeigendownloads** - TVSDK ruft Anzeigen parallel zur Inhaltswiedergabe vor, bevor die Werbeunterbrechung auftritt, und ermöglicht so die nahtlose Wiedergabe von Anzeigen und Inhalten.
   * **Verzögerte Anzeigenauflösung** - Mit dieser Funktion warten wir nicht auf die Auflösung von Nicht-Pre-Pup-Anzeigen, bevor wir die Wiedergabe starten, und verringern so die Startzeit. APIs wie Suche und Trick-Play sind immer noch nicht erlaubt, bis alle Anzeigen aufgelöst sind.

* **MP4-Inhaltswiedergabe**

Diese Version von TVSDK unterstützt die Wiedergabe von MP4 als Hauptinhalt.

* **Persistente Netzwerkverbindungen**

TVSDK unterhält eine Reihe wiederverwendbarer Netzwerkverbindungen, sodass bei der Erstellung und Zerstörung einer Netzwerkverbindung für jede Netzwerkanforderung kein Mehraufwand entsteht.

* **Auflösungsbasierter Ausgabeschutz**

Diese Funktion verknüpft Wiedergabeschränkungen mit bestimmten Auflösungen und bietet feinere DRM-Steuerelemente.

* **Trickplay mit adaptiver Bitrate (ABR)**

Mit dieser Funktion kann TVSDK im Trick Play-Modus zwischen iFrame-Streams wechseln. Sie können Nicht-iFrame-Profile verwenden, um Tricks mit geringeren Geschwindigkeiten abzuspielen.

* **Smoother Trick Play**

Diese Verbesserungen verbessern das Benutzererlebnis:

・ Adaptive Auswahl der Bitrate und Framerate während der Trickwiedergabe basierend auf der Bandbreite und dem Pufferprofil

・ Verwenden Sie den Hauptstrom anstelle des IDR-Streams, um eine schnelle Wiedergabe mit bis zu 30 fps zu ermöglichen.

* **Verbesserte ABR-Logik**

Die neue ABR-Logik basiert auf der Pufferlänge, der Änderungsrate der Pufferlänge und der gemessenen Bandbreite. Dadurch wird sichergestellt, dass die ABR bei Bandbreitenschwankungen die richtige Bitrate auswählt und die Anzahl der tatsächlichen Bitratenwechsel optimiert, indem die Geschwindigkeit überwacht wird, mit der sich die Pufferlänge ändert.

* **Rechnungsstellung**

TVSDK erfasst automatisch Metriken gemäß dem Kundenverkaufsvertrag, um regelmäßige Nutzungsberichte zu generieren, die für Abrechnungszwecke erforderlich sind. Bei jedem Stream-Startereignis verwendet TVSDK die Adobe Analytics-Dateneinfüge-API, um Abrechnungsmetriken wie Inhaltstyp, durch Anzeigeneinfügung aktivierte Flags und DRM-aktivierte Flags - basierend auf der Dauer des abrechnungsfähigen Streams - an die Report Suite von Adobe Analytics Primetime zu senden. Dies beeinträchtigt nicht die Report Suites oder Server-Aufrufe des Kunden, die er selbst in Adobe Analytics Report Suites oder Server-Aufrufen verwendet. Auf Anfrage wird dieser Rechnungsverwendungsbericht regelmäßig an Kunden gesendet. Dies ist die erste Phase der Abrechnungsfunktion, die nur die Nutzungsabrechnung unterstützt. Sie kann mithilfe der in der Dokumentation beschriebenen APIs basierend auf dem Kaufvertrag konfiguriert werden.

## Unterstützte Funktionen {#supported-features}

TVSDK 2.4 unterstützt eine Reihe von Funktionen, die Sie implementieren können, um Ihren Videoanwendungen Funktionen hinzuzufügen.

>[!NOTE]
>
>In den Funktionsmatrix-Tabellen unten bedeutet eine Ö, dass die Funktion in der aktuellen Version unterstützt wird.

### Kernfunktionen der Wiedergabe {#core-playback-features}

| **Funktion** | **Content-Typ** | **HLS** | **DASH** |
|---|---|---|---|
| Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | VOD + Live | ï | Ö (nur VOD) |
| FER - Allgemeine Wiedergabe (Wiedergabe, Pause, Suche) | FER VOD | ï | Nicht unterstützt |
| MP3 | VOD | Nicht unterstützt | Nicht unterstützt |
| MP4-Inhaltswiedergabe | VOD | ï | ï |
| Adaptive Bit Rate Switching Logic | VOD + Live | ï | Nicht unterstützt |
| Nur-Audio-Wiedergabe | VOD + Live | ï | Nicht unterstützt |
| Geschlossene Untertitel - 608/708 | VOD + Live | ï | Ö (nur VOD) |
| Geschlossene Untertitel - WebVTT | VOD + Live | ï | Ö (nur VOD) |
| Manifest-Failover | VOD + Live | ï | Ö (nur VOD) |
| Erweitertes Failover | VOD + Live | ï | Ö (nur VOD) |
| QoS- und Player-Benachrichtigungen | VOD + Live | ï | Ö (nur VOD) |
| Unterstützung für Cookie-Kopfzeilen | VOD + Live | ï | Ö (nur VOD) |
| Unterstützung für benutzerdefinierte Kopfzeilen | VOD + Live | Nicht unterstützt | Nicht unterstützt |
| Puffersteuerungsparameter festlegen | VOD + Live | ï | Ö (nur VOD) |
| Festlegen von adaptiven Bitratensteuerelementen | VOD + Live | ï | Ö (nur VOD) |
| Benutzerdefinierte Manifest-Tags (HLS)/Ereignis-Streams (DASH) | VOD + Live | ï | Ö (nur VOD) |
| Spätes gebundenes Audio | VOD + Live | ï | Ö (nur VOD) |
| 302 Umleitung | VOD + Live | ï | Ö (nur VOD) |

### Erweiterte Wiedergabefunktionen {#advanced-playback-features}

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td> 
   <td><strong>Content-Typ</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Wiedergabe mit Versatz</td> 
   <td>Live</td> 
   <td>ï</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Nur-Audio-Wiedergabe</td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Trick Play </td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Glattes Trick Play (mit ABR)</td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>ID3-Analyse (HLS)/Zeitgesteuerte Metadaten (DASH)</td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Blackouts </td> 
   <td>VOD + Live</td> 
   <td>Nicht unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Sofort aktiviert</td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Unterstützung von Diskontinuitätsmarkierungen (HLS) </li> 
     <li>Mehrzeiträume (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>302 Weiterleitungs-Sticky</td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Ö (nur VOD)</td> 
  </tr>
  <tr>
   <td>Miniatur-Scrubbing (Iframe und JPEG)</td> 
   <td>VOD + Live</td> 
   <td>Nicht unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Stream-Integrität </td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Nicht unterstützt</td> 
  </tr>
 </tbody>
</table>

### Zentrale Ad Insertion-Funktionen (CSAI) {#core-ad-insertion-features-csai}

| **Funktion** | **Content-Typ** | **HLS** | **DASH** |
|---|---|---|---|
| Allgemeine Wiedergabe, Anzeigen aktiviert | VOD + Live | ï | Ö (nur VOD-Vorrollen) |
| Fairer Inhalt mit aktivierten Anzeigen | VOD | ï | Nicht unterstützt |
| Standardmäßige Anzeigenverhalten | VOD + Live | ï | Ö (nur VOD-Vorrollen) |
| VAST 2.0/3.0 | VOD + Live | ï | Ö (nur VOD-Vorrollen) |
| VMAP 1.0 | VOD + Live | ï | Ö (nur VOD-Vorrollen) |
| MP4-Anzeigen | VOD + Live | Ö (aus CRS) | Ö (von CRS, nur Vorrollen) |

### Erweiterte Ad Insertion-Funktionen (CSAI) {#advanced-ad-insertion-features-csai}

<table> 
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td> 
   <td><strong>Content-Typ</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Trick Play mit aktivierten Anzeigen</td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
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
   <td>ï</td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte Parameter</td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>Benutzerdefiniertes Anzeigenverhalten</td> 
   <td>VOD + Live</td> 
   <td>ï</td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte Anzeigen-Tags</td> 
   <td>Live</td> 
   <td>ï </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Benutzerdefinierte Anzeigenauflöser</td> 
   <td>VOD + Live</td> 
   <td>ï </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Freewheel Custom Ad Resolver</td> 
   <td>VOD</td> 
   <td>Nicht unterstützt</td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>C3 Ad Replacement </td> 
   <td>VOD + Live</td> 
   <td>ï </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Lazy Ad Loading</td> 
   <td>VOD</td> 
   <td>ï </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Unterstützung von Diskontinuitätsmarkierungen - SSAI (HLS) </li> 
     <li>Mehrzeiträume (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>ï </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Companion Ads, Banneranzeigen und klickbare Anzeigen</td> 
   <td>VOD + Live</td> 
   <td>ï </td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>VPAID 2.0</td> 
   <td>VOD + Live</td> 
   <td>Ö (JS) </td> 
   <td>Ö (nur VOD-Vorrollen)</td> 
  </tr>
  <tr>
   <td>Beenden einer frühzeitigen Anzeige</td> 
   <td>Live</td> 
   <td>ï </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>Regelbasierte kreative VOD + Live-Priorisierung</td> 
   <td>VOD + Live</td> 
   <td>ï </td> 
   <td>Nicht unterstützt</td> 
  </tr>
  <tr>
   <td>CRS-Regeln </td> 
   <td>VOD + Live</td> 
   <td>ï </td> 
   <td>Nicht unterstützt</td> 
  </tr>
 </tbody>
</table>

## Inhaltsschutzfunktionen {#content-protection-features}

| **Funktion** | **Content-Typ** | **HLS** | **DASH** |
|---|---|---|---|
| AES-Verschlüsselung | VOD + Live | ï | Ö (nur VOD) |
| AES-Beispielverschlüsselung | VOD + Live | ï |  |
| Tokenisierte Streams | VOD + Live | ï |  |
| DRM | VOD + Live | Nur Primetime DRM (Future: Widevine) | Nur widew |
| Externe Wiedergabe (RBOP) | VOD + Live | Nur Primetime DRM | Nicht unterstützt |
| Lizenzrotation | VOD + Live | Nur Primetime DRM | Nicht unterstützt |
| Hauptrolle | VOD + Live | Nur Primetime DRM | Nicht unterstützt |

### Integrationsfunktionen {#integration-features}

| **Funktion** | **Content-Typ** | **HLS** | **DASH** |
|---|---|---|---|
| Adobe Analytics VHL-Integration | VOD + Live | ï | ï |
| Rechnungsstellung | VOD + Live | ï | Nicht unterstützt |

## Nicht unterstützte Funktionen {#features-not-supported}

Diese TVSDK-Version unterstützt nicht:

* Werbeunterbrechung.
* Langsame Bewegung im Trickspiel.
* Suchen und trickplay mit MP4-Inhalt.
* Anzeigeneinfügung mit MP4-Hauptinhalt.
* Suchen Sie, wann eine Anzeige wiedergegeben wird.
* Wiedergabe von Anzeigen mit Nur-Audio-Medien.

## Bekannte Probleme und Einschränkungen {#known-issues-and-limitations}

Diese TVSDK-Version weist die folgenden Probleme auf:

* Gerätespezifischer Absturz (Samsung Galaxy Tab 4) von VOD DRM LBA mit Auditude und Klick auf Anzeigen
* Die Post-Roll-Anzeige wird für einen bestimmten Inhalt nicht wiedergegeben.
* Das Festlegen der Beschriftung auf CJK-Sprachen funktioniert nicht.
* Video kann aus dem Trickmodus automatisch zwischen VOD und Live herauskommen.
* VHL - Beim Start eines Inhalts mit einem Offset werden falsche Heartbeat-Aufrufe gesendet.
* Wenn VPAID-Anzeigen wiedergegeben werden, VHL-Heartbeat-Aufrufe für -Ereignis:type:Abspielanzeige fehlt.
* Pre-Roll-Anzeige wird auch dann wiedergegeben, wenn die adBreakPolicy-SKIP ausgewählt ist.
* Nach dem Aufrufen des Complete-Status-Players kehrt mit SKIP adBreakPolicy für Post-Roll-Anzeigen zum Wiedergabestatus zurück.

Ohne Video gibt es keine Viewport-Dimension und ohne Viewport-Dimension können Sie keine Grafiken für Beschriftungen anzeigen.

## Hilfreiche Ressourcen {#helpful-resources}

* Die vollständige Hilfedokumentation finden Sie unter [Adobe Primetime - Lernen und Support](https://experienceleague.adobe.com/docs/primetime.html) Seite.
