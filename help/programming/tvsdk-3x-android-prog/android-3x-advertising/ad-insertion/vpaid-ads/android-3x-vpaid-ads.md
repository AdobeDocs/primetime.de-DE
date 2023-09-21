---
description: Die Definition der Video Player-Adserving-Benutzeroberfläche (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Anwendern ein Rich-Media-Erlebnis und ermöglicht es Herausgebern, Anzeigen besser auszurichten, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
title: VPAID 2.0-Anzeigenunterstützung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Übersicht {#vpaid-ad-support-overview}

Die Definition der Video Player-Adserving-Benutzeroberfläche (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Anwendern ein Rich-Media-Erlebnis und ermöglicht es Herausgebern, Anzeigen besser auszurichten, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.

Die folgenden Funktionen werden unterstützt:

* Version 2.0 der VPAID-Spezifikation

  Weitere Informationen finden Sie unter [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Lineare VPAID-Anzeigen mit Video-on-Demand (VOD)-Inhalten
* JavaScript-VPAID-Anzeigen

  VPAID-Anzeigen müssen JavaScript-basiert sein und die Anzeigenantwort muss den Medientyp der VPAID-Anzeige als `application/javascript`.

Die folgenden Funktionen werden nicht unterstützt:

* Version 1.0 der VPAID-Spezifikation
* Übersprungene Anzeigen
* Nichtlineare Anzeigen, wie Überlagerungsanzeigen, dynamische begleitende Anzeigen, minimierbare Anzeigen, ausblendbare Anzeigen und erweiterbare Anzeigen
* Vorabladen von VPAID-Anzeigen
* VPAID-Anzeigen in Live-Inhalten
* Flash VPAID-Anzeigen

## API

Die folgenden API-Elemente unterstützen VPAID 2.0-Anzeigen:

* Die `getCustomAdView` Methode `MediaPlayer` gibt eine `CustomAdView` -Objekt, das die Webansicht darstellt, die die VPAID-Anzeige rendert (siehe [API-Referenzen](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html)).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` legt die Zeitüberschreitung beim VPAID-Ladevorgang fest. Der Standardwert für die Zeitüberschreitung beträgt 10 Sekunden.

Während die VPAID-Anzeige wiedergegeben wird:

* Die VPAID-Anzeige wird in einem Ansichtsbehälter über der Player-Ansicht angezeigt, sodass Code, der auf Tippen von Benutzern in der Player-Ansicht beruht, nicht funktioniert.
* Aufrufe an `pause` und `play` Pause auf der Player-Instanz und Fortsetzen der VPAID-Anzeige.

* VPAID-Anzeigen haben keine vordefinierte Dauer, da die Anzeige interaktiv sein kann.

  Die Anzeigendauer und die Gesamtdauer der Werbeunterbrechung, die in der Antwort des Anzeigen-Servers angegeben sind, sind möglicherweise nicht präzise.
