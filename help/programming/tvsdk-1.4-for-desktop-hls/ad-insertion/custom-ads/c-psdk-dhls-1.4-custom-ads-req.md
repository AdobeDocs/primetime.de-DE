---
description: Die Definition der Video Player Ad-Serving Interface (VPAID) bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. VPAID bietet Anwendern ein Rich-Media-Erlebnis und ermöglicht es Herausgebern, Anzeigen besser auszurichten, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
title: Benutzerdefinierte Anzeigenanforderungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Benutzerdefinierte Anzeigenanforderungen {#custom-ad-requirements}

Der TVSDK-Player kann digitale Video-Player-Ad-Interface-Definition-Anzeigen (VPAID) abspielen und den Anzeigenladestatus anzeigen. Wenn Fehler in der Anzeige auftreten oder das Laden von Anzeigen zu lange dauert, ignoriert TVSDK diese Anzeigen.

Die Definition der Video Player Ad-Serving Interface (VPAID) bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. VPAID bietet Anwendern ein Rich-Media-Erlebnis und ermöglicht es Herausgebern, Anzeigen besser auszurichten, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.

<!--<a id="section_9A358902CBC24999BA34206EE2029616"></a>-->

Das TVSDK unterstützt die folgenden Funktionen:

* Version 1.0 und 2.0 der VPAID-Spezifikation
* Lineare VPAID-Anzeigen für Video-On-Demand (VOD)-Inhalte
* Flash VPAID-Anzeigen

  VPAID-Anzeigen müssen auf Flash basieren und die Anzeigenantwort muss den Medientyp der VPAID-Anzeige als `application/x-shockwave-flash`.

Die folgenden Funktionen werden nicht unterstützt:

* Nichtlineare Anzeigen wie Überlagerungsanzeigen und dynamische begleitende Anzeigen
* Vorabladen von VPAID-Anzeigen
* VPAID-Anzeigen in Live-Inhalten
* JavaScript-VPAID-Anzeigen

## Ladestatus {#section_5F55C0101CD44A65BCFE1D124CBDF239}

Das TVSDK sendet die folgenden Ereignisse:

* `AdLoading`
* `AdLoaded`
* `AdStarted`
* `AdPlaying`
* `AdStopped`

Nach dem `AdStopped` -Ereignis, setzt das TVSDK den Videoinhalt fort.

>[!TIP]
>
>Wenn Sie den Wert null angeben, versucht TVSDK, die Anzeige zu laden, bis sie geladen wird, oder es ist ein Fehler aufgetreten.

## Ignorieren von Anzeigen {#section_3EA452F420884335AE90DF23C17E416A}

Wenn das Laden der Anzeige zu lange dauert oder Fehler in der Anzeige auftreten, kann TVSDK die Anzeige ignorieren und die nächste Anzeige im Anzeigen-Pod wird automatisch wiedergegeben.

Wenn die Variable `AuditudeSettings.customAdLoadTimeout` -Einstellung gibt eine Anzahl von Sekunden an, die größer als null ist. Das TVSDK versucht, die Anzeige auf die angegebene Dauer zu laden. Wenn die Anzeige nicht geladen werden kann, wird die Anzeige übersprungen. Wenn Sie beispielsweise `AuditudeSettings.customAdLoadTimeout:5`, versucht das TVSDK, die Anzeige für maximal 5 Sekunden zu laden. Wenn die Anzeige weiterhin nicht geladen wird, wird sie ignoriert.
