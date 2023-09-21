---
description: Durch die Anzeigeneinfügung werden Anzeigen für Video-On-Demand (VOD) , für Live-Streaming und für lineares Streaming mit Anzeigen-Tracking und Anzeigenwiedergabe aufgelöst. TVSDK sendet die erforderlichen Anfragen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in Phasen.
title: Anzeigen einfügen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---

# Anzeigen einfügen {#insert-ads}

Durch die Anzeigeneinfügung werden Anzeigen für Video-On-Demand (VOD) , für Live-Streaming und für lineares Streaming mit Anzeigen-Tracking und Anzeigenwiedergabe aufgelöst. TVSDK sendet die erforderlichen Anfragen an den Anzeigen-Server, empfängt Informationen über Anzeigen für den angegebenen Inhalt und platziert die Anzeigen in Phasen.

Ein *`ad break`* enthält eine oder mehrere Anzeigen, die nacheinander abgespielt werden. TVSDK fügt Anzeigen im Hauptinhalt als Mitglieder einer oder mehrerer Werbeunterbrechungen ein.

>[!TIP]
>
>Wenn die Anzeige Fehler aufweist, ignoriert TVSDK die Anzeige.

## Auflösen und Einfügen von VOD-Anzeigen {#section_157344F857C64F36B48AD441F6E7FABA}

TVSDK unterstützt mehrere Anwendungsfälle für das Auflösen und Einfügen von VOD-Anzeigen.

* Einfügen einer Pre-Roll-Anzeige, wobei Anzeigen am Anfang des Inhalts eingefügt werden.
* Mid-Roll-Anzeigeneinfügung, wobei mindestens eine Anzeige in der Mitte des Inhalts eingefügt wird.
* Einfügen einer Post-Roll-Anzeige, wobei mindestens eine Anzeige am Ende des Inhalts angehängt wird.

TVSDK löst die Anzeigen auf, fügt die Anzeigen an vom Anzeigen-Server definierten Positionen ein und berechnet die virtuelle Timeline vor dem Start der Wiedergabe. Nach dem Start der Wiedergabe können keine Änderungen auftreten, z. B. beim Einfügen oder Entfernen von Anzeigen.

## Live- und lineare Anzeige auflösen und einfügen {#section_A6A1BB262D084462A1D134083556B7CC}

TVSDK unterstützt mehrere Anwendungsfälle für das Auflösen und Einfügen von Live- und linearen Anzeigen.

* Einfügen einer Pre-Roll-Anzeige, wobei mindestens eine Anzeige am Anfang des Inhalts eingefügt wird.
* Mid-Roll-Anzeigeneinfügung, wobei mindestens eine Anzeige in der Mitte des Inhalts eingefügt wird.

TVSDK löst die Anzeigen auf und fügt sie ein, wenn ein Cue-Punkt im Live- oder linearen Stream auftritt. TVSDK unterstützt standardmäßig die folgenden Hinweise als gültige Anzeigenmarkierungen bei der Auflösung und Platzierung von Anzeigen:

* #EXT-X-CUEPOINT
* #EXT-X-AD
* #EXT-X-CUE
* #EXT-X-CUE-OUT

Diese Markierungen erfordern die `DURATION` in Sekunden und der eindeutigen Kennung des Cue-Point. Beispiel:

```
#EXT-X-CUE DURATION=27 ID=identiferForThisCue ... 
```

Weitere Informationen zu zusätzlichen Hinweisen finden Sie unter [Benutzerdefinierte Tags abonnieren](../../tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-custom-tags-configure/ios-3x-custom-tags-subscribe.md).

## Tracking von Client-Anzeigen {#section_12355C7A35F14C15A2A18AAC90FEC2F5}

TVSDK verfolgt automatisch Anzeigen für VOD und Live-/Lineares Streaming.

Benachrichtigungen informieren Ihre Anwendung über den Fortschritt einer Anzeige, einschließlich Informationen darüber, wann eine Anzeige beginnt und wann sie endet.

## Implementieren einer frühen Werbeunterbrechung {#section_EEB9FE62CA7E4790B58D3CA906F43DCF}

Für das Einfügen von Live-Stream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.

Im Folgenden finden Sie einige Beispiele für die Rückgabe einer frühzeitigen Werbeunterbrechung:

* Die Dauer der Werbeunterbrechung bei bestimmten Sportveranstaltungen.

  Obwohl eine Standarddauer angegeben ist, muss die Werbeunterbrechung beendet werden, wenn das Spiel wieder aufgenommen wird, bevor die Pause beendet wird.
* Ein Notsignal während einer Werbeunterbrechung in einem Live-Stream.

Die Möglichkeit, eine Werbeunterbrechung frühzeitig zu beenden, wird durch ein benutzerdefiniertes Tag im Manifest identifiziert, das als Splink-in- oder Cue-in-Tag bezeichnet wird. TVSDK ermöglicht es der Anwendung, diese Splink-in-Tags zu abonnieren, um eine Splink-in-Möglichkeit zu bieten.

* So verwenden Sie die `#EXT-X-CUE-IN` -Tag als Spleice-in-Gelegenheit markieren und eine frühe Werbeunterbrechung implementieren:

   1. Abonnieren Sie das -Tag.

      ```
      [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:@"#EXT-X-CUE-IN"]];
      ```

   1. Fügen Sie den Cue-in-Opportunity-Resolver hinzu.

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Set cue in opportunity resolver 
      [clientFactory registerOpportunityResolver:[PTDefaultAdSpliceInOpportunityResolver adSpliceInOpportunityResolverWithTag:@"#EXT-X-CUE-IN"]];
      ```

* So geben Sie dasselbe Tag für die Aufteilung und die Aufteilung frei:

1. Wenn die Anwendung denselben Cue-Point verwendet, um Cue-out/Spllice-out und Cue-in/Spleice-in anzugeben, erweitern Sie `PTDefaultAdOpportunityResolver` und implementieren `preparePlacementOpportunity` -Methode.

   >[!TIP]
   >
   >Im folgenden Code wird davon ausgegangen, dass die App über eine Implementierung für die `isCueInOpportunity` -Methode.

   ```
   - (PTPlacementOpportunity *)preparePlacementOpportunity:(PTTimedMetadata *)timedMetadata 
   { 
         if ([self isCueInOpportunity:timedMetadata]) 
         { 
               return [PTPlacementOpportunity advertisementSpliceInOpportunityWithTimedMetadata:timedMetadata]; 
           } 
           else 
           { 
               return [super preparePlacementOpportunity:timedMetadata]; 
         } 
   }
   ```

1. Registrieren Sie den Resolver für erweiterte Möglichkeiten auf der `PTDefaultMediaPlayerClientFactory` -Instanz.

```
   // self.player is the PTMediaPlayer instance created for content and ad playback 
       PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
             
   // Clear existing resolver and register the new opportunity resolver 
   [clientFactory clearOpportunityResolvers]; 
   [clientFactory registerOpportunityResolver:[[PTDefaultExtendedAdOpportunityResolver new] autorelease]];
```
