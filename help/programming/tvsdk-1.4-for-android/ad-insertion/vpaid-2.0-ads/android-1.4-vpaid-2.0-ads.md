---
description: Die Definition der Video Player Ad-Serving Interface (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Anwendern ein Rich-Media-Erlebnis und ermöglicht es Herausgebern, Anzeigen besser auszurichten, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
title: VPAID 2.0-Anzeigenunterstützung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# VPAID 2.0-Anzeigenunterstützung {#vpaid-ad-support}

Die Definition der Video Player Ad-Serving Interface (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Anwendern ein Rich-Media-Erlebnis und ermöglicht es Herausgebern, Anzeigen besser auszurichten, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.

Die folgenden Funktionen werden unterstützt:

* Version 2.0 der VPAID-Spezifikation

  Weitere Informationen finden Sie unter [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Lineare VPAID-Anzeigen für Video-On-Demand (VOD)-Inhalte
* JavaScript-VPAID-Anzeigen

  VPAID-Anzeigen müssen JavaScript-basiert sein und die Anzeigenantwort muss den Medientyp der VPAID-Anzeige als `application/javascript`.

Die folgenden Funktionen werden nicht unterstützt:

* Version 1.0 der VPAID-Spezifikation
* Übersprungene Anzeigen
* Nichtlineare Anzeigen wie Überlagerungsanzeigen, dynamische begleitende Anzeigen, minimierbare Anzeigen, ausblendbare Anzeigen und erweiterbare Anzeigen
* Vorabladen von VPAID-Anzeigen
* VPAID-Anzeigen in Live-Inhalten
* Flash VPAID-Anzeigen

## API-Änderungen {#section_D62F3E059C6C493592D34534B0BFC150}

Die folgenden Änderungen wurden an der API vorgenommen:

* A `getCustomAdView` -Funktion wurde hinzugefügt in `MediaPlayer` und gibt die Webansicht zurück, die die VPAID-Anzeige rendert.

  Weitere Informationen zum `CustomAdView` -Objekt, das von dieser Funktion zurückgegeben wird, siehe [API-Referenzen](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/index.html).

* A `CUSTOM_AD` -Ereignis von der Medienplayer-Instanz gesendet.

  Die Anwendung kann einen Ereignisrückruf durch Implementierung von `CustomAdEventListener`.

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` ermöglicht es Ihnen, die standardmäßige Zeitüberschreitung beim VPAID-Ladevorgang zu ändern.

  Der Standardwert für die Zeitüberschreitung beträgt 10 Sekunden.

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Während die VPAID-Anzeige wiedergegeben wird:

* Die VPAID-Anzeige wird in einem Ansichtsbehälter über der Player-Ansicht angezeigt, sodass der Code, der von Benutzern auf die Player-Ansicht angeklickt wird, nicht funktioniert.
* Der Hauptinhaltsplayer wird angehalten und ruft `pause` und `play` auf der Player-Instanz verwendet werden, um die VPAID-Anzeige anzuhalten und wieder aufzunehmen.

* VPAID-Anzeigen haben keine vordefinierte Dauer, da die Anzeige interaktiv sein kann.

  Die Anzeigendauer und die Gesamtdauer der Werbeunterbrechung, die durch die Antwort des Anzeigen-Servers definiert werden, sind möglicherweise nicht präzise.

## Implementieren der VPAID 2.0-Integration {#implement-vpaid-integration}

Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenansicht und entsprechende Listener hinzu.

Hinzufügen der VPAID 2.0-Unterstützung:

1. Fügen Sie die benutzerdefinierte Anzeigenansicht zur Player-Oberfläche hinzu.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. Fügen Sie einen Listener für benutzerdefinierte Anzeigenereignisse hinzu.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```
