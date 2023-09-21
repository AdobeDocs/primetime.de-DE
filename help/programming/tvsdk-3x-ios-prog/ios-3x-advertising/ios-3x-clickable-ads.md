---
description: TVSDK stellt Ihnen Informationen bereit, damit Sie auf Clickthrough-Anzeigen reagieren können. Bei der Erstellung Ihrer Player-Benutzeroberfläche müssen Sie entscheiden, wie Sie reagieren, wenn ein Benutzer auf eine anklickbare Anzeige klickt.
title: Klickbare Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Klickbare Anzeigen {#clickable-ads}

TVSDK stellt Ihnen Informationen bereit, damit Sie auf Clickthrough-Anzeigen reagieren können. Bei der Erstellung Ihrer Player-Benutzeroberfläche müssen Sie entscheiden, wie Sie reagieren, wenn ein Benutzer auf eine anklickbare Anzeige klickt.

In TVSDK für iOS können nur lineare Anzeigen angeklickt werden.

## Antworten auf Klicks auf Anzeigen {#section_537AF2593FDB4257B81AAE2103B0C719}

Wenn ein Benutzer auf eine Anzeige, eine begleitende Banneranzeige oder eine zugehörige Schaltfläche klickt, muss Ihre Anwendung reagieren. TVSDK liefert Informationen zur Ziel-URL für den Klick.

1. Um einen Ereignis-Listener für TVSDK einzurichten und die Clickthrough-Informationen bereitzustellen, fügen Sie einen Beobachter für `PTMediaPlayerAdClickNotification`.

   >[!NOTE]
   >
   >Wenn ein Benutzer auf eine Anzeige, eine begleitende Banneranzeige oder eine zugehörige Schaltfläche klickt, sendet TVSDK diese Benachrichtigung, einschließlich Informationen zum Ziel des Klicks.

1. Überwachen Sie Benutzerinteraktionen auf anklickbaren Anzeigen.
1. Wenn der Benutzer die Anzeige oder Schaltfläche berührt oder klickt, verwenden Sie zur Benachrichtigung von TVSDK die Option `[_player notifyClick:_currentAd.primaryAsset];`.
1. Suchen Sie nach `PTMediaPlayerAdClickNotification` -Ereignis von TVSDK.
1. Verwenden Sie zum Abrufen der Clickthrough-URL und der zugehörigen Informationen die `PTMediaPlayerAdClickURLKey` -Objekt.
1. Anhalten des Videos
1. Verwenden Sie die Clickthrough-Informationen, um die Anzeigen-Clickthrough-URL und die zugehörigen Informationen anzuzeigen.

   >[!NOTE]
   >
   >Sie können die Informationen beispielsweise auf eine der folgenden Arten anzeigen:

   * Öffnen Sie in Ihrer Anwendung die Clickthrough-URL in einem Browser.

     Auf Desktop-Plattformen wird der Bereich für die Videoanzeige verwendet, um Clickthrough-URLs bei Benutzerklicks aufzurufen.
   * Leiten Sie Benutzer zu ihrem externen mobilen Webbrowser um.

     Auf Mobilgeräten wird der Bereich für die Videoanzeige für andere Funktionen verwendet, z. B. zum Ausblenden und Anzeigen von Steuerelementen, zum Anhalten der Wiedergabe, zum Erweitern auf den Vollbildmodus usw. Auf diesen Geräten wird eine separate Ansicht, z. B. eine Sponsorschaltfläche, verwendet, um die Clickthrough-URL zu starten.

1. Schließen Sie das Browser-Fenster, in dem die Clickthrough-Informationen angezeigt werden, und setzen Sie die Wiedergabe des Videos fort.

   Beispiel:

   ```
      // Listening for click notification  
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdClick:)  
    name:PTMediaPlayerAdClickNotification object:self.player]; 
   - (void) onMediaPlayerAdClick:(NSNotification *) notification { 
      NSString *url = [notification.userInfo objectForKey:PTMediaPlayerAdClickURLKey];  
      if (url != nil) { 
          [self openBrowser:[NSURL URLWithString:url]]; 
      } 
   } 
   ```
