---
description: Mit der Anzeigeneinfügung werden Anzeigen für Video-on-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigenverfolgung und Anzeigenwiedergabe aufgelöst. TVSDK stellt die erforderlichen Anforderungen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in den Inhalten in Phasen.
seo-description: Mit der Anzeigeneinfügung werden Anzeigen für Video-on-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigenverfolgung und Anzeigenwiedergabe aufgelöst. TVSDK stellt die erforderlichen Anforderungen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in den Inhalten in Phasen.
seo-title: Anzeigen einfügen
title: Anzeigen einfügen
uuid: 6fffb340-65ea-4c47-a55b-c0ec4917d37c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Anzeigen einfügen{#insert-ads}

Mit der Anzeigeneinfügung werden Anzeigen für Video-on-Demand (VOD), für Live-Streaming und für lineares Streaming mit Anzeigenverfolgung und Anzeigenwiedergabe aufgelöst. TVSDK stellt die erforderlichen Anforderungen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in den Inhalten in Phasen.

Eine *`ad break`* enthält eine oder mehrere Anzeigen, die nacheinander abgespielt werden. TVSDK fügt Anzeigen in den Hauptinhalt als Mitglieder einer oder mehrerer Werbeunterbrechungen ein.

>[!TIP]
>
>Wenn die Anzeige Fehler aufweist, ignoriert TVSDK die Anzeige.

## Auflösen und Einfügen von VOD-Anzeigen {#section_157344F857C64F36B48AD441F6E7FABA}

TVSDK unterstützt mehrere Anwendungsfälle für VOD-Anzeigenauflösung und -einfügung.

* Einfügen von Pre-Roll-Anzeigen, wobei Anzeigen am Anfang des Inhalts eingefügt werden.
* Einfügen von Mid-Roll-Anzeigen, wobei mindestens eine Anzeige in der Mitte des Inhalts eingefügt wird.
* Einfügen von Post-Roll-Anzeigen, wobei mindestens eine Anzeige am Ende des Inhalts angehängt wird.

TVSDK löst die Anzeigen, fügt die Anzeigen an den vom Anzeigen-Server definierten Orten ein und berechnet die virtuelle Zeitleiste vor dem Beginn der Wiedergabe. Nach der Wiedergabe können keine Beginn mehr auftreten, wie z. B. eingefügte oder eingefügte Anzeigen, die entfernt werden.

## Auflösen und Einfügen einer Live- und linearen Anzeige {#section_A6A1BB262D084462A1D134083556B7CC}

TVSDK unterstützt mehrere Anwendungsfälle zum Auflösen und Einfügen von Live- und linearen Anzeigen.

* Einfügen von Pre-Roll-Anzeigen, wobei mindestens eine Anzeige am Anfang des Inhalts eingefügt wird.
* Einfügen von Mid-Roll-Anzeigen, wobei mindestens eine Anzeige in der Mitte des Inhalts eingefügt wird.

TVSDK löst die Anzeigen und fügt sie ein, wenn ein Cue-Point im Live- oder linearen Stream gefunden wird. TVSDK unterstützt standardmäßig die folgenden Hinweise als gültige Anzeigenmarkierungen beim Auflösen und Platzieren von Anzeigen:

* # EXT-X-CUEPOINT
* # EXT-X-AD
* # EXT-X-CUE
* # EXT-X-CUE-OUT

Diese Markierungen erfordern die eindeutige ID des Metadatenfelds `DURATION` in Sekunden. Beispiel:

```
#EXT-X-CUE DURATION=27 ID=identiferForThisCue ... 
```

Weitere Informationen zu zusätzlichen Hinweisen finden Sie unter [Abonnieren von benutzerdefinierten Tags](../ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-custom-tags-subscribe.md).

## Client-Anzeige verfolgen {#section_12355C7A35F14C15A2A18AAC90FEC2F5}

TVSDK verfolgt automatisch Anzeigen für VOD und live/linear Streaming.

Benachrichtigungen werden verwendet, um Ihre Anwendung über den Fortschritt einer Anzeige zu informieren, einschließlich Informationen darüber, wann eine Anzeige beginnt und wann sie endet.

## Implementieren einer Rückgabe einer frühen Werbeunterbrechung {#section_EEB9FE62CA7E4790B58D3CA906F43DCF}

Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.

Im Folgenden finden Sie einige Beispiele für eine Rückkehr zu einer frühen Werbeunterbrechung:

* Die Dauer der Werbeunterbrechung in bestimmten Ereignissen.

   Obwohl eine Standarddauer angegeben ist, muss die Werbeunterbrechung beendet werden, wenn das Spiel wieder aufgenommen wird, bevor die Pause abgeschlossen ist.
* Ein Notsignal während einer Werbeunterbrechung in einem Live-Stream.

Die Möglichkeit, eine Werbeunterbrechung frühzeitig zu beenden, wird durch ein benutzerdefiniertes Tag im Manifest, das als SLICE-In- oder Cue-In-Tag bezeichnet wird, identifiziert. TVSDK ermöglicht es der Anwendung, diese SLICE-in-Tags zu abonnieren, um eine SLICE-Gelegenheit zu bieten.

* So verwenden Sie das `#EXT-X-CUE-IN` -Tag als Gelegenheit zum Einspalten und implementieren eine Zeilenumbruchrückgabe für eine frühe Werbeunterbrechung:

   1. Abonnieren Sie das Tag.

      ```
      [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:@"#EXT-X-CUE-IN"]];
      ```

   1. Hinzufügen den Cue-in-Opportunitätsauflöser.

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Set cue in opportunity resolver 
      [clientFactory registerOpportunityResolver:[PTDefaultAdSpliceInOpportunityResolver adSpliceInOpportunityResolverWithTag:@"#EXT-X-CUE-IN"]];
      ```

* So geben Sie das gleiche Tag für das Splice-out und das Splice-In frei:

   1. Wenn die Anwendung denselben Cue-Point verwendet, um Cue-out/SLICout und Cue-In/SLICE-In anzugeben, erweitern `PTDefaultAdOpportunityResolver` und implementieren Sie die `preparePlacementOpportunity` Methode.

      >[!TIP]
      >
      >Im folgenden Code wird davon ausgegangen, dass die App über eine Implementierung für die `isCueInOpportunity` Methode verfügt.
      >
      >
      >
      >
      >
      ```>
      >- (PTPlacementOpportunity *)preparePlacementOpportunity:(PTTimedMetadata *)timedMetadata 
      >{ 
      >       if ([self isCueInOpportunity:timedMetadata]) 
      >       { 
      >               return [PTPlacementOpportunity advertisementSpliceInOpportunityWithTimedMetadata:timedMetadata]; 
      >       } 
      >       else 
      >       { 
      >               return [super preparePlacementOpportunity:timedMetadata]; 
      >       } 
      >}
      >```       >
      >



   1. Registrieren Sie den Resolver für erweiterte Möglichkeiten auf der `PTDefaultMediaPlayerClientFactory` Instanz.

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Clear existing resolver and register the new opportunity resolver 
      [clientFactory clearOpportunityResolvers]; 
      [clientFactory registerOpportunityResolver:[[PTDefaultExtendedAdOpportunityResolver new] autorelease]];
      ```

