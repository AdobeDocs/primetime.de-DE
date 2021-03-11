---
description: Die Definition der Video-Player-Ad-Serving-Schnittstelle (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Benutzern eine Rich-Media-Erfahrung und ermöglicht Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
title: VPAID 2.0-Anzeigenunterstützung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# VPAID 2.0-Anzeigenunterstützung {#vpaid-ad-support}

Die Definition der Video-Player-Ad-Serving-Schnittstelle (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Benutzern eine Rich-Media-Erfahrung und ermöglicht Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.

Die folgenden Funktionen werden unterstützt:

* Version 2.0 der VPAID-Spezifikation

   Weitere Informationen finden Sie unter [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Lineare VPAID-Anzeigen mit VOD-Inhalten (Video-on-Demand)
* JavaScript VPAID-Anzeigen

   VPAID-Anzeigen müssen JavaScript-basiert sein, und die Anzeigenantwort muss den Medientyp der VPAID-Anzeige als `application/javascript` identifizieren.

Die folgenden Funktionen werden nicht unterstützt:

* Version 1.0 der VPAID-Spezifikation
* Übersprungene Anzeigen
* Nicht-lineare Anzeigen wie Überlagerungsanzeigen, dynamische Begleithandanzeigen, minimierbare Anzeigen, reduzierbare Anzeigen und erweiterbare Anzeigen
* Vorabladen von VPAID-Anzeigen
* VPAID-Anzeigen in Live-Inhalten
* Flash-VPAID-Anzeigen

## API

Die folgenden API-Elemente unterstützen VPAID 2.0-Anzeigen:

* Die `getCustomAdView`-Methode von `MediaPlayer` gibt ein `CustomAdView`-Objekt zurück, das die Web-Ansicht darstellt, die die VPAID-Anzeige rendert (siehe [API-Referenzen](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html)).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` legt den Timeout beim VPAID-Ladevorgang fest. Der Standardwert für das Timeout beträgt 10 Sekunden.

Während die VPAID-Anzeige abgespielt wird:

* Die VPAID-Anzeige wird in einem Ansicht-Container über der Player-Ansicht angezeigt, sodass Code, der auf Tippen von Benutzern auf der Player-Ansicht basiert, nicht funktioniert.
* Aufrufe von `pause` und `play` in der Player-Instanz halten die VPAID-Anzeige an und setzen sie fort.

* VPAID-Anzeigen haben keine vordefinierte Dauer, da die Anzeige interaktiv sein kann.

   Die Anzeigendauer und die Gesamtdauer der Werbeunterbrechung, die in der Antwort auf den Anzeigen-Server angegeben sind, sind möglicherweise nicht korrekt.