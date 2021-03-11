---
description: TVSDK stellt Informationen bereit, damit Sie Clickthrough-Anzeigen bearbeiten können. Beim Erstellen der Player-Benutzeroberfläche müssen Sie entscheiden, wie Sie reagieren, wenn ein Benutzer auf eine anklickbare Anzeige klickt.
title: Klickbare Anzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Klickbare Anzeigen {#clickable-ads}

TVSDK stellt Informationen bereit, damit Sie Clickthrough-Anzeigen bearbeiten können. Beim Erstellen der Player-Benutzeroberfläche müssen Sie entscheiden, wie Sie reagieren, wenn ein Benutzer auf eine anklickbare Anzeige klickt.

In TVSDK für iOS können nur lineare Anzeigen angeklickt werden.

## Antworten Sie auf Klicks auf Anzeigen {#section_537AF2593FDB4257B81AAE2103B0C719}

Wenn ein Benutzer auf eine Anzeige, eine begleitende Banneranzeige oder eine zugehörige Schaltfläche klickt, muss Ihre Anwendung reagieren. TVSDK liefert Informationen zur Ziel-URL für den Klick.

1. Um einen Ereignis-Listener für TVSDK einzurichten und die Clickthrough-Informationen bereitzustellen, fügen Sie einen Beobachter für `PTMediaPlayerAdClickNotification` hinzu.

   >[!NOTE]
   >
   >Wenn ein Benutzer auf eine Anzeige, eine begleitende Banneranzeige oder eine zugehörige Schaltfläche klickt, sendet TVSDK diese Benachrichtigung einschließlich Informationen zum Ziel des Klicks.

1. Überwachen Sie Benutzerinteraktionen auf klickbaren Anzeigen.
1. Wenn der Benutzer die Anzeige oder Schaltfläche berührt oder klickt, um TVSDK zu benachrichtigen, verwenden Sie `[_player notifyClick:_currentAd.primaryAsset];`.
1. Suchen Sie nach dem Ereignis `PTMediaPlayerAdClickNotification` von TVSDK.
1. Verwenden Sie das `PTMediaPlayerAdClickURLKey`-Objekt, um die Clickthrough-URL und zugehörige Informationen abzurufen.
1. Halten Sie das Video an.
1. Verwenden Sie die Clickthrough-Informationen, um die Anzeigen-Clickthrough-URL und die zugehörigen Informationen anzuzeigen.

   >[!NOTE]
   >
   >Sie können die Informationen beispielsweise auf eine der folgenden Arten anzeigen:

   * Öffnen Sie in Ihrer Anwendung die Clickthrough-URL in einem Browser.

      Auf Desktop-Plattformen wird der Videoanzeigenwiedergabebereich zum Aufrufen von Clickthrough-URLs bei Benutzerklicks verwendet.
   * Leiten Sie Benutzer zu ihrem externen mobilen Webbrowser um.

      Auf Mobilgeräten wird der Bereich für Video- und Wiedergabe für andere Funktionen verwendet, z. B. zum Ausblenden und Anzeigen von Steuerelementen, zum Anhalten der Wiedergabe, zum Erweitern auf den Vollbildmodus usw. Auf diesen Geräten wird eine separate Ansicht, z. B. eine Sponsorschaltfläche, zum Starten der Clickthrough-URL verwendet.

1. Schließen Sie das Browserfenster, in dem die Clickthrough-Informationen angezeigt werden, und nehmen Sie die Wiedergabe des Videos wieder auf.

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
