---
description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 bietet eine gemeinsame Oberfläche zum Abspielen von Videoanzeigen. Es bietet Benutzern eine Rich-Media-Erfahrung und ermöglicht Herausgebern, Anzeigen besser zu Zielgruppen, Anzeigenimpressionen zu verfolgen und Videoinhalte zu monetarisieren.
title: VPAID 2.0-Anzeigenunterstützung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '323'
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
* VPAID-Anzeige nach dem Roll

## API-Änderungen {#section_D62F3E059C6C493592D34534B0BFC150}

Die folgenden Änderungen wurden an der API vorgenommen:

* `PTAuditudeMetadata` hat eine  `customAdLoadTimeout` Eigenschaft, um den Standard-Timeout beim Laden von VPAID zu ändern.

   Der Standardwert für das Timeout beträgt 10 Sekunden.

* `PTMediaPlayerCustomAdNotification` wird von der  `PTMediaPlayer` Instanz ausgelöst

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Während die VPAID-Anzeige abgespielt wird:

* Die VPAID-Anzeige wird in einem Ansicht-Container über der Player-Ansicht angezeigt, sodass der Code, der auf dem Tippen von Benutzern auf der Player-Ansicht basiert, nicht funktioniert.
* Der Hauptinhalt-Player wird angehalten, und Aufrufe von `pause` und `play` auf der Player-Instanz werden verwendet, um die VPAID-Anzeige anzuhalten und fortzusetzen.

* VPAID-Anzeigen haben keine vordefinierte Dauer, da die Anzeige interaktiv sein kann.

   Die Anzeigendauer und die Gesamtdauer der Werbeunterbrechung, die durch die Anzeigenserverantwort definiert werden, sind möglicherweise nicht genau.

## Implementierung der VPAID 2.0-Integration {#section_63C9C737367C4A0AB4D62E0DC2084141}

So fügen Sie VPAID 2.0-Unterstützung in Ihrer iOS-Anwendung hinzu:

1. (Optional) Hinzufügen einen Listener für benutzerdefinierte Anzeigen-Ereignis.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerCustomAdNotification:) name:PTMediaPlayerCustomAdNotification object:self.player];
   ```

1. (Optional) Zeigen Sie die Benachrichtigung an.

   ```
   -(void)onMediaPlayerCustomAdNotification:(NSNotification *)notification{    PTCustomAdNotificationObject *notificationObject = [notification.userInfo objectForKey:PTCustomAdNotificationObjectKey];    if (notificationObject)    
   {        NSLog(@"ViewController:: Custom Ad Notification Received: %ld", notificationObject.type);    } 
   
   }
   ```
