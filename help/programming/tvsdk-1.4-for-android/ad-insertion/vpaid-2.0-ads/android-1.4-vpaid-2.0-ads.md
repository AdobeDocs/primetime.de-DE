---
description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Benutzern eine Rich-Media-Erfahrung und ermöglicht Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
seo-description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Benutzern eine Rich-Media-Erfahrung und ermöglicht Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
seo-title: VPAID 2.0-Anzeigenunterstützung
title: VPAID 2.0-Anzeigenunterstützung
uuid: 7168a6e4-9c5e-4d3a-8710-867cf98e4445
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# VPAID 2.0-Anzeigenunterstützung {#vpaid-ad-support}

Video Player Ad-Serving Interface Definition (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Benutzern eine Rich-Media-Erfahrung und ermöglicht Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.

Die folgenden Funktionen werden unterstützt:

* Version 2.0 der VPAID-Spezifikation

   Weitere Informationen finden Sie unter [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Lineare VPAID-Anzeigen auf Video-on-Demand (VOD)-Inhalten
* JavaScript VPAID-Anzeigen

   VPAID-Anzeigen müssen JavaScript-basiert sein, und die Anzeigenantwort muss den Medientyp der VPAID-Anzeige als `application/javascript` identifizieren.

Die folgenden Funktionen werden nicht unterstützt:

* Version 1.0 der VPAID-Spezifikation
* Übersprungene Anzeigen
* Nicht-lineare Anzeigen wie Überlagerungsanzeigen, dynamische begleitende Anzeigen, minimierbare Anzeigen, reduzierbare Anzeigen und erweiterbare Anzeigen
* Vorabladen von VPAID-Anzeigen
* VPAID-Anzeigen in Live-Inhalten
* Flash-VPAID-Anzeigen

## API-Änderungen {#section_D62F3E059C6C493592D34534B0BFC150}

Die folgenden Änderungen wurden an der API vorgenommen:

* Eine `getCustomAdView`-Funktion wurde in `MediaPlayer` hinzugefügt und gibt die Web-Ansicht zurück, die die VPAID-Anzeige rendert.

   Weitere Informationen zum `CustomAdView`-Objekt, das von dieser Funktion zurückgegeben wird, finden Sie unter [API-Referenzen](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/index.html).

* Ein `CUSTOM_AD`-Ereignis wird von der Medienplayer-Instanz gesendet.

   Die Anwendung kann einen Ereignis-Rückruf registrieren, indem sie `CustomAdEventListener` implementiert.

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` ermöglicht es Ihnen, den Standard-Timeout beim Laden von VPAID zu ändern.

   Der Standardwert für das Timeout beträgt 10 Sekunden.

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Während die VPAID-Anzeige abgespielt wird:

* Die VPAID-Anzeige wird in einem Ansicht-Container über der Player-Ansicht angezeigt, sodass der Code, der auf dem Tippen von Benutzern auf der Player-Ansicht basiert, nicht funktioniert.
* Der Hauptinhalt-Player wird angehalten, und Aufrufe von `pause` und `play` auf der Player-Instanz werden verwendet, um die VPAID-Anzeige anzuhalten und fortzusetzen.

* VPAID-Anzeigen haben keine vordefinierte Dauer, da die Anzeige interaktiv sein kann.

   Die Anzeigendauer und die Gesamtdauer der Werbeunterbrechung, die durch die Anzeigenserverantwort definiert werden, sind möglicherweise nicht genau.

## Implementierung der VPAID 2.0-Integration {#implement-vpaid-integration}

Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.

So fügen Sie VPAID 2.0-Unterstützung hinzu:

1. hinzufügen der benutzerdefinierten Anzeigen-Ansicht auf die Player-Oberfläche.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. hinzufügen eines Listeners für benutzerdefinierte Anzeigen-Ereignis.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```
