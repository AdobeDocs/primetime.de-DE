---
description: Die Definition der Video-Player-Ad-Serving-Schnittstelle (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Benutzern eine Rich-Media-Erfahrung und ermöglicht Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
title: VPAID 2.0-Anzeigenunterstützung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# VPAID 2.0-Anzeigenunterstützung {#vpaid-ad-support}

Die Definition der Video-Player-Ad-Serving-Schnittstelle (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Benutzern eine Rich-Media-Erfahrung und ermöglicht Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.

Die folgenden Funktionen werden unterstützt:

* Version 2.0 der VPAID-Spezifikation

   Weitere Informationen finden Sie unter [IAB VPAID 2.0](https://www.iab.com/guidelines/digital-video-player-ad-interface-definition-vpaid-2-0/).
* Lineare VPAID-Anzeigen mit VOD-Inhalten (Video-on-Demand)
* In Live-Inhalten unterstützt Browser TVSDK Pre-Roll JavaScript VPAID-Anzeigen.
* Im Flash-Ausweichmodus unterstützt Browser TVSDK nur Flash-basierte VPAID-Anzeigen.
* Lineare JavaScript-VPAID-Anzeigen

   VPAID-Anzeigen müssen JavaScript-basiert sein, und die Anzeigenantwort muss den Medientyp der VPAID-Anzeige als `application/javascript` identifizieren.

Die folgenden Funktionen werden nicht unterstützt:

* Version 1.0 der VPAID-Spezifikation
* Übersprungene Anzeigen
* Nichtlineare Anzeigen, wie Überlagerungsanzeigen, dynamische Begleithandanzeigen, minimierbare Anzeigen, reduzierbare Anzeigen und erweiterbare Anzeigen.
* Vorabladen von VPAID-Anzeigen
* VPAID-Anzeigen in Live-Inhalten
* Flash-VPAID-Anzeigen

## API {#section_0DB1D383CA5047B281BC808BC082C69B}

Die folgenden API-Elemente unterstützen VPAID 2.0-Anzeigen:

* Die `getCustomAdView`-Methode von `MediaPlayer` gibt ein `CustomAdView`-Objekt zurück, das die Web-Ansicht darstellt, die die VPAID-Anzeige rendert.

   Weitere Informationen zur `getCustomAdView`-Methode finden Sie unter [MediaPlayer-API-Dokumentation](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.MediaPlayer.html).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` legt den Timeout beim VPAID-Ladevorgang fest.

   Der Standardwert für das Timeout beträgt 10 Sekunden.

* Mit der API `auditudeSettings.ignoreVPAIDAds` können Sie VPAID-Anzeigen ignorieren, die vom Auditude-Server empfangen wurden. Die API funktioniert nicht bei Flash Fallback.

Während die VPAID-Anzeige abgespielt wird:

* Die VPAID-Anzeige wird in einem Ansicht-Container über der Player-Ansicht angezeigt, sodass Code, der auf Tippen von Benutzern auf der Player-Ansicht basiert, nicht funktioniert.
* Aufrufe zum Anhalten und Abspielen der Player-Instanz halten die VPAID-Anzeige an und nehmen sie wieder auf.
* VPAID-Anzeigen haben keine vordefinierte Dauer, da die Anzeige interaktiv sein kann.

   Die Anzeigendauer und die Gesamtdauer der Werbeunterbrechung, die in der Antwort auf den Anzeigen-Server angegeben sind, sind möglicherweise nicht korrekt.