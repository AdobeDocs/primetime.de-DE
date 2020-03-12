---
description: Die Definition der Video Player Ad-Serving Interface (VPAID) bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. VPAID bietet eine Rich-Media-Erfahrung für Benutzer und ermöglicht es Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
seo-description: Die Definition der Video Player Ad-Serving Interface (VPAID) bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. VPAID bietet eine Rich-Media-Erfahrung für Benutzer und ermöglicht es Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
seo-title: Benutzerdefinierte Anzeigenanforderungen
title: Benutzerdefinierte Anzeigenanforderungen
uuid: 6d4ba87b-ffe5-467d-8ab5-9795928c2f69
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Benutzerdefinierte Anzeigenanforderungen {#custom-ad-requirements}

Der TVSDK-Player kann Anzeigen mit digitaler Video Player Ad-Interface Definition (VPAID) abspielen und den Anzeigenladestatus anzeigen. Wenn die Anzeige Fehler enthält oder die Anzeige zu lange lädt, ignoriert TVSDK diese Anzeigen.

Die Definition der Video Player Ad-Serving Interface (VPAID) bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. VPAID bietet eine Rich-Media-Erfahrung für Benutzer und ermöglicht es Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.

<!--<a id="section_9A358902CBC24999BA34206EE2029616"></a>-->

TVSDK unterstützt die folgenden Funktionen:

* Version 1.0 und 2.0 der VPAID-Spezifikation
* Lineare VPAID-Anzeigen auf Video-on-Demand (VOD)-Inhalten
* Flash VPAID-Anzeigen

   VPAID-Anzeigen müssen Flash-basiert sein, und die Anzeigenantwort muss den Medientyp der VPAID-Anzeige als `application/x-shockwave-flash`.

Die folgenden Funktionen werden nicht unterstützt:

* Nichtlineare Anzeigen wie Überlagerungsanzeigen und dynamische Begleitanzeigen
* Vorabladen von VPAID-Anzeigen
* VPAID-Anzeigen in Live-Inhalten
* JavaScript VPAID-Anzeigen

## Ladestatus {#section_5F55C0101CD44A65BCFE1D124CBDF239}

Das TVSDK sendet die folgenden Ereignis:

* `AdLoading`
* `AdLoaded`
* `AdStarted`
* `AdPlaying`
* `AdStopped`

Nach dem `AdStopped` Ereignis setzt das TVSDK den Videoinhalt fort.

>[!TIP]
>
>Wenn Sie den Wert Null angeben, versucht TVSDK, die Anzeige zu laden, bis sie geladen wird, oder es ist ein Fehler aufgetreten.

## Ignorierende Anzeigen {#section_3EA452F420884335AE90DF23C17E416A}

Wenn das Laden der Anzeige zu lange dauert oder Fehler in der Anzeige auftreten, kann die TVSDK die Anzeige ignorieren und die nächste Anzeige im Werbeunterbrechung wird automatisch wiedergegeben.

Wenn die `AuditudeSettings.customAdLoadTimeout` Einstellung eine Anzahl von Sekunden größer als null angibt, versucht TVSDK, die Anzeige auf die angegebene Dauer zu laden. Wenn die Anzeige nicht geladen werden kann, wird sie übersprungen. Wenn Sie beispielsweise konfigurieren, `AuditudeSettings.customAdLoadTimeout:5`versucht TVSDK, die Anzeige für maximal 5 Sekunden zu laden. Wenn die Anzeige trotzdem nicht geladen wird, wird sie ignoriert.
