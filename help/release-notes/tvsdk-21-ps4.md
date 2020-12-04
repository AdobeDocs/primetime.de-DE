---
title: TVSDK 2.1 PlayStation 4 - Versionshinweise
seo-title: TVSDK 2.1 PlayStation 4 - Versionshinweise
description: TVSDK 2.1 for PlayStation 4 - Versionshinweise beschreiben die unterstützten Funktionen und bekannten Probleme in TVSDK 2.1 PlayStation 4 .
seo-description: TVSDK 2.1 for PlayStation 4 - Versionshinweise beschreiben die unterstützten Funktionen und bekannten Probleme in TVSDK 2.1 PlayStation 4 .
uuid: 494569cf-07e2-476a-b88e-e46c9cca4cdc
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: ebfc8819-f5a9-47a2-b454-0e4e6f9e4640
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# TVSDK 2.1 PlayStation 4 - Versionshinweise {#tvsdk-playstation-release-notes}

TVSDK 2.1 for PlayStation 4 - Versionshinweise beschreiben die unterstützten Funktionen und bekannten Probleme in TVSDK 2.1 PlayStation 4 .

## Behobene Probleme {#resolved-issues}

Hier sind die gelösten Probleme für TVSDK 2.1 für PlayStation 4:

**Version 2.1.0.638**

* **PTPLAY-10439:**
Wenn der VMAP-Wrapper-Anzeigenlink beschädigt wurde, steckte der Player im Vorbereitungszustand fest (es wurde nicht gesendet) 
`onComplete` zu ihrem Anrufer).

* **PTPLAY-10179:**

   `creativeRepackaging` und  `fallbackOnInvalidCreative` Werte sind jetzt standardmäßig deaktiviert. Wenn das `creativeRepackaging`-Flag gesetzt wurde, aber kein `creativeRepackaging`-Format angegeben wurde, wurde `onRepackagingComplete` so oft aufgerufen, wie es Anzeigen in der Werbeunterbrechung gab, wodurch Anzeigenumbrüche mehrmals erstellt wurden.

* **Zendesk #10304**: Die Variable zum Ein-/Ausschalten der Anzeige wurde nicht initialisiert. Die Variable wird jetzt von `DataSetEntry's` ctor initialisiert.

* **PTPLAY-10318:**
Unterstützung für den Hintergrundmodus wurde eingeführt.
* **Zendesk # 17409:**
Wenn Sie in den Trick Play-Modus wechseln, dann zurück in den normalen Wiedergabemodus und dann wieder in den Trick Play-Modus, dann war die Wiedergabeposition springend.
* **PTPLAY-9552:**
Nach dem Analysieren der XML-Antwortdateien wird jetzt der Fehlercode 1108 gepingt, wenn keine Anzeigen vorhanden sind.
* **PTPLAY-9551:**
Wenn nach der Verarbeitung durch Auditude keine Werbeunterbrechung erfolgt, ruft das CRS 
**** onPrefetchComplete, das groupCount dekrementiert. Da kein Werbeunterbrechung vorliegt, ist **groupCount** 0 und wird um 1 verringert. Zuvor war **groupCount** **uint32_t**, wegen dessen es zu max. Wert wechselte. Dies ist nun **int32_t**.

**Version 2.1.0.621**

* **Zendesk #4555**
Instant bei Speicherproblemen beim Laden von Fehlern - 
`MediaItemLoader` Fehlerbehebung bei Abstürzen während der Veröffentlichung  `mediaitemloader`

* **Zendesk #17223**
2.x CSAI: Nicht alle Anzeigen-Tracking-URLs werden ausgelöst
   * Einige VAST-Anzeigen, die wiederum auf eine Inline-Anzeige verweisen, fehlten Tracking-URLs.
   * Wenn eine Anzeige in VAST XML mehrere Impressions-Tags enthält, wurde nur die erste Impressions-URL gespeichert und Rest wurde ignoriert. Jetzt werden alle Impressions-URLs gespeichert und später gepingelt.
* **Zendesk #17224**
PS4-Benutzeragent verschiebt Informationen über die Zeit bis zum Ende von UAString
* **Zendesk #17226**
2.x CSAI: Nicht alle Anzeigen wurden eingebunden.
\
   Korrektur, um anzuzeigen, dass die Zeitschiene aufgrund der Vorgänge &quot;insertBy&quot;oder &quot;deleteBy&quot;geändert wurde, und den Zeitraum entsprechend zu ändern.

* **Zendesk #17284**
   [Alle ] PlattformenUntertitel werden nicht angezeigt.\
   HLS - Unterstützung für das `EXT-X-MEDIA-TIME`-Tag für VTT-Untertiteldateien.

* **Zendesk #17889**
Wiedergabe &quot;Milky&quot;auf PS4
\
   korrekter Yoffset (für Farbkonvertierung)

* **Zendesk #17954**
Ad-Fallback-Logik + Handhabung leerer riesiger
\
   Es wurde ein Fehler behoben, der dazu führte, dass der Vast-Parser den Wrapper weiter verarbeitete, wenn einer der Vast-Wrapper leer war.

* **Zendesk #17807**
Kann nicht über leeres Riesenmaß hinausgehen, genauso wie Zendesk #3103

* **Zendesk #17865**
Fallback Logic auf PS4 und XBox One
\
   Wie Zendesk #3103

**Version 2.1.0.591**

* **Zendesk #3767**
PS4-Anzeigencodefragment. Die Anzeigenauflösung schlägt bei der Verarbeitung von VMAP-Weiterleitungen fehl.
* **Zendesk #4096**
PS4 CSAI: Fehler bei der Segmentierung Es wurde ein Absturz behoben, der auftrat, wenn TVSDK einen Segmentierungsfehler verursachte, wenn die Anzeigenbibliothek eine VMAP-Antwort verarbeitete.

* **Zendesk #4161**
Trickplay 16x am Ende des Films friert ein festes Blockieren, wenn das Trickplay zur normalen Wiedergabe zurückkehrt

* **Zendesk #4208**
Zufälliger Absturz, wenn Untertitel aktiviert sind Korrektur des Speicherlecks, wenn Untertitel aktiviert wurden

* **Zendesk #4213**
PS4 CSAI: Ändern Sie die Standard-Benutzeragenten-Zeichenfolge für alle ad-bezogenen Aufrufe Die User-Agent-Zeichenfolge wird mit derselben UA-Zeichenfolge erstellt, die vom Browser verwendet wird + die Primetime-Zeichenfolge hinzufügen

* **PTPLAY-7675** (intern) Transkodierte Anzeigen werden nicht mit Creative Repackage wiedergegeben, wenn sie innerhalb einer VMAP- oder VAST-Antwort aufgerufen wurden. Die Fehlerbehebung besteht darin, bei umfangreichen Anzeigen nur die Mediendatei aus der Anzeige zu lesen, anstatt aus dem Asset zu lesen.

* **PTPLAY-7895** (intern) Wenn  `allowMultipleAds=false`keine Anzeigen abgespielt werden, wurde ein Fehler behoben, durch den der  `allowMultipleAds` Parameter nicht korrekt befolgt wurde.

* **PTPLAY-7896** (intern) Die Anzeige wird in der Reihenfolge der Sequenz bei PS4 abgespielt. Korrektur des Problems, bei dem Anzeigen nicht in der Reihenfolge angezeigt wurden, in der sie in den XML-Antworten angezeigt wurden.

* PS4 TVSDK erneut in einer Mini-App anstatt im Spiel getestet.

**Version 2.1.0.563**

* **Zendesk #3868**
Unterstützt TVSDK Playstation SDK 2.5 Das TVSDK wurde jetzt mit dem 2.5 Playstation SDK erstellt.

* **Zendesk #4093**
targetingInfo-Schlüssel-Wert-Paare in der App-Anfrage.
\
   Es wurde ein Zeilenumbruchzeichen hinzugefügt, das die Schlüssel/Wert-Paare trennt.

## Unterstützte Funktionen {#supported-features}

Die folgenden Funktionen werden in TVSDK 2.1 für PlayStation 4 unterstützt:

**Version 2.1.0.621**

* Ad Fallback, Dissy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103)
Bei VAST-Anzeigen (kreativen Elementen) mit aktivierter Ausweichregel behandelt das TVSDK eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht, an ihrer Stelle Ausweichanzeigen zu verwenden.Sie können einige Aspekte des Ausweichverhaltens konfigurieren

**Version 2.1.0.538**

* HLS VOD-Wiedergabe einschließlich Wiedergabe, Pause, Suche
* Adaptives Streaming mit Bitrate
* Wiedergabe verschlüsselter Inhalte mit Primetime DRM und Vanille AES-geschütztem Inhalt
* Einfügen clientseitiger Anzeigen mit standardmäßigem Anzeigenverhalten und Anzeigenverzeihung
* Kreative Umverpackung
* WebVTT-Untertitel
* Sofort bei benutzerdefinierter Position des Beginns
* Trick Play mit schnellem Vorwärts- und Rückspulen
* 302 Umleitung

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).