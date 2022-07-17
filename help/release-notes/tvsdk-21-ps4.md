---
title: TVSDK 2.1 PlayStation 4 - Versionshinweise
description: TVSDK 2.1 for PlayStation 4 - Versionshinweise beschreiben die unterstützten Funktionen und bekannten Probleme in TVSDK 2.1 PlayStation 4 .
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
exl-id: 32af3fe4-c730-41f6-a558-987bd14c9bae
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# TVSDK 2.1 PlayStation 4 - Versionshinweise {#tvsdk-playstation-release-notes}

TVSDK 2.1 for PlayStation 4 - Versionshinweise beschreiben die unterstützten Funktionen und bekannten Probleme in TVSDK 2.1 PlayStation 4 .

## Gelöste Probleme {#resolved-issues}

Hier finden Sie die gelösten Probleme für TVSDK 2.1 für PlayStation 4:

**Version 2.1.0.638**

* **PTPLAY-10439:**
Als der VMAP-Wrapper-Anzeigenlink beschädigt wurde, blieb der Player im Vorbereitungsstatus stecken (er sendete nicht) 
`onComplete` zum Anrufer).

* **PTPLAY-10179:**

   `creativeRepackaging` und `fallbackOnInvalidCreative` -Werte sind jetzt standardmäßig deaktiviert. Wenn die Variable `creativeRepackaging` Markierung gesetzt, aber keine `creativeRepackaging` das Format angegeben wurde, die `onRepackagingComplete` wurde so oft aufgerufen, wie Anzeigen in der Werbeunterbrechung vorhanden waren, wodurch Anzeigen mehrmals erstellt wurden.

* **Zendesk #10304**: Die Variable für den Anzeigenverfall &quot;ein/aus&quot;wurde nicht initialisiert. Wir initialisieren jetzt die Variable aus `DataSetEntry's` ctor.

* **PTPLAY-10318:**
Unterstützung für den Hintergrundmodus wurde eingeführt.
* **Zendesk # 17409:**
Wenn Sie in den Modus &quot;Trick Play&quot;wechseln, dann zurück in den normalen Wiedergabemodus und dann wieder in den Modus &quot;Trick Play&quot;wechseln, springt die Wiedergabequalität.
* **PTPLAY-9552:**
Nach dem Parsen der XML-Antwortdateien wird jetzt der Fehlercode 1108 gepingt, sobald keine Anzeigen vorhanden sind.
* **PTPLAY-9551:**
Wenn nach der Auditude-Verarbeitung keine Werbeunterbrechung erfolgt, ruft das CRS auf 
**onPrefetchComplete** , wodurch groupCount verringert wird. Da es keine Werbeunterbrechung gibt, wird die **groupCount** ist 0 und wird durch 1 verringert. Zuvor wurde die **groupCount** was **uint32_t** , wodurch sie zum Maximalwert geändert wurde. Dies ist jetzt **int32_t**.

**Version 2.1.0.621**

* **Zendesk #4555**
Sofort bei Problemen mit dem Speicher, die beim Laden auftreten - 
`MediaItemLoader` Fehlerbehebung für Absturz beim Freigeben `mediaitemloader`

* **Zendesk #17223**
2.x CSAI: Nicht alle Anzeigen-Tracking-URLs werden ausgelöst
   * Einige VAST-Anzeigen, die wiederum auf eine Inline-Anzeige verweisen, fehlten Tracking-URLs.
   * Wenn eine Anzeige in VAST XML mehrere Impression-Tags enthält, wurde nur die erste Impression-URL gespeichert und der Rest wurde ignoriert. Jetzt werden alle Impression-URLs gespeichert und später gepingt.
* **Zendesk #17224**
PS4-Benutzeragent verschiebt Primetime-Informationen an das Ende von UAString
* **Zendesk #17226**
2.x CSAI: Nicht alle Anzeigen wurden zugeordnet.
\
   Die Fehlerbehebung zeigt an, dass sich die Timeline aufgrund der Vorgänge insertBy oder deleteBy geändert hat, und ändert den Zeitraum entsprechend.

* **Zendesk #17284**
   [Alle Plattformen] Geschlossene Untertitel werden nicht angezeigt.\
   HLS - Unterstützung für `EXT-X-MEDIA-TIME` Tag für VTT-Untertiteldateien.

* **Zendesk #17889**
Wiedergabe von &quot;Milchprodukten&quot;auf PS4
\
   Angewandter korrekter YOffset (für Farbkonvertierung)

* **Zendesk #17954**
Ad-Fallback-Logik + Umgang mit leeren umfangreichen
\
   Es wurde ein Problem behoben, bei dem der Vast-Wrapper leer war. Der Vast-Parser verwendete ihn, um den Wrapper weiter zu verarbeiten.

* **Zendesk #17807**
Kann nicht vorbei an leeren weiten Teilen wie Zendesk #3103

* **Zendesk #17865**
Ausweichlogik für PS4 und XBox One
\
   Wie Zendesk #3103

**Version 2.1.0.591**

* **Zendesk #3767**
PS4-Code-Snippet, die Anzeigenauflösung schlägt bei der Verarbeitung von VMAP-Umleitungen fehl.
* **Zendesk #4096**
PS4-CSAI: Segmentierungsfehler Es wurde ein Absturz behoben, der auftrat, wenn TVSDK Segmentierungsfehler verursachte, wenn die Anzeigenbibliothek eine VMAP-Antwort verarbeitete.

* **Zendesk #4161**
Trickplay 16x am Ende des Films friert festes Deadlock bei der Rückkehr der Trickplay-Wiedergabe zur normalen Wiedergabe

* **Zendesk #4208**
Zufälliger Absturz bei aktivierten Geschlossenen Untertiteln Fester Speicherleck bei aktivierten Untertiteln

* **Zendesk #4213**
PS4-CSAI: Ändern Sie die standardmäßige Benutzeragenten-Zeichenfolge für alle anzeigenbezogenen Aufrufe Die Benutzeragenten-Zeichenfolge wird mit derselben UA-Zeichenfolge erstellt, die der Browser verwendet, und fügen Sie die Primetime-Zeichenfolge hinzu.

* **PTPLAY-7675** (intern) Transkodierte Anzeigen werden nicht wiedergegeben. Creative Repackaging schlug fehl, wenn es in einer VMAP- oder VAST-Antwort aufgerufen wurde. Die Fehlerbehebung besteht darin, bei riesigen Anzeigen nur die Mediendatei aus der Anzeige zu lesen, anstatt aus dem Asset zu lesen.

* **PTPLAY-7895** (intern) Wenn `allowMultipleAds=false`, keine Anzeigen werden wiedergegeben Es wurde ein Fehler behoben, durch den `allowMultipleAds` wurde nicht korrekt befolgt.

* **PTPLAY-7896** (intern) Anzeigen werden in PS4 nicht in der Sequenzreihenfolge abgespielt. Es wurde ein Problem behoben, bei dem Anzeigen nicht in der Reihenfolge waren, in der die Anzeigen in den XML-Antworten angezeigt wurden.

* PS4 TVSDK wurde in einer Mini-App statt in einem Spiel erneut getestet.

**Version 2.1.0.563**

* **Zendesk #3868**
Unterstützt TVSDK Playstation SDK 2.5. Das TVSDK ist jetzt mit dem 2.5 Playstation SDK erstellt.

* **Zendesk #4093**
targetingInfo -Schlüssel-Wert-Paare in der Pt Ads-Anfrage.
\
   Es wurde ein Zeilenumbruchzeichen hinzugefügt, das die Schlüssel-Wert-Paare trennt.

## Unterstützte Funktionen {#supported-features}

Die folgenden Funktionen werden in TVSDK 2.1 für PlayStation 4 unterstützt:

**Version 2.1.0.621**

* Ad Fallback, Daisy-Verkettung in der Anzeigenauswahllogik (Zendesk #3103) Für VAST-Anzeigen (Kreative) mit aktivierter Ausweichregel behandelt das TVSDK eine Anzeige mit einem ungültigen MIME-Typ als leere Anzeige und versucht, an ihrer Stelle Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren

**Version 2.1.0.538**

* HLS-VOD-Wiedergabe, einschließlich Wiedergabe, Pause, Suche
* Adaptives Bitratenstreaming
* Verschlüsselte Inhaltswiedergabe mit Primetime DRM und Vanilla AES-geschütztem Inhalt
* Client-seitige Anzeigeneinfügung mit standardmäßigem Anzeigenverhalten und Anzeigenverzicht
* Kreative Umverpackung
* WebVTT-Untertitel
* Sofort auf mit benutzerdefinierter Startposition
* Trickspiel mit schnellem Vorwärts und schnellem Rückwind
* 302-Umleitung

## Hilfreiche Ressourcen {#helpful-resources}

* Die vollständige Hilfedokumentation finden Sie unter [Adobe Primetime - Lernen und Support](https://experienceleague.adobe.com/docs/primetime.html) Seite.
