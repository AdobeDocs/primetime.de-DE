---
description: Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, muss Ihre Anwendung reagieren. TVSDK liefert Informationen zur Ziel-URL für den Klick.
seo-description: Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, muss Ihre Anwendung reagieren. TVSDK liefert Informationen zur Ziel-URL für den Klick.
seo-title: Antworten auf Klicks auf Anzeigen
title: Antworten auf Klicks auf Anzeigen
uuid: 31852f01-c900-48e3-ae23-7fb131c22594
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Antworten auf Klicks auf Anzeigen{#respond-to-clicks-on-ads}

Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, muss Ihre Anwendung reagieren. TVSDK liefert Informationen zur Ziel-URL für den Klick.

1. Um einen Ereignis-Listener für TVSDK einzurichten und die Clickthrough-Informationen bereitzustellen, registrieren Sie einen `AdClickedEventListener.onAdClicked`.

   Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, sendet TVSDK diese Benachrichtigung, einschließlich Informationen zum Ziel des Klicks.
1. Überwachen Sie Benutzerinteraktionen auf klickbaren Anzeigen.
1. Wenn der Benutzer die Anzeige oder Schaltfläche berührt oder anklickt, um TVSDK zu benachrichtigen, rufen Sie `notifyClick` die `MediaPlayerView`.
1. Hören Sie auf das `onAdClick(AdClickEvent event)` Ereignis von TVSDK.
1. Verwenden Sie zum Abrufen der Clickthrough-URL und der zugehörigen Informationen die Getter-Methoden für die `AdClickEvent` Instanz.
1. Halten Sie das Video an.

   Weitere Informationen zum Anhalten des Videos finden Sie unter [Anhalten und Wiederaufnehmen der Wiedergabe.](../../ad-insertion/clickable-ads/android-1.4-pausing-resuming-playback.md).
1. Verwenden Sie die Clickthrough-Informationen, um die Anzeigen-Clickthrough-URL und die zugehörigen Informationen anzuzeigen.

       Sie können die Informationen beispielsweise auf eine der folgenden Arten anzeigen:
   
   * Öffnen Sie in Ihrer Anwendung die Clickthrough-URL in einem Browser.

      Auf Desktop-Plattformen wird der Videoanzeigenwiedergabebereich zum Aufrufen von Clickthrough-URLs bei Benutzerklicks verwendet.
   * Leiten Sie Benutzer zu ihrem externen mobilen Webbrowser um.

      Auf Mobilgeräten wird der Bereich für Video- und Wiedergabe für andere Funktionen verwendet, z. B. zum Ausblenden und Anzeigen von Steuerelementen, zum Anhalten der Wiedergabe, zum Erweitern auf den Vollbildmodus usw. Auf diesen Geräten wird eine separate Ansicht, z. B. eine Sponsorschaltfläche, zum Starten der Clickthrough-URL verwendet.

1. Schließen Sie das Browserfenster, in dem die Clickthrough-Informationen angezeigt werden, und nehmen Sie die Wiedergabe des Videos wieder auf.

<!--<a id="example_2D93228E510D438C8AB5559897817A47"></a>-->

Beispiel:

```java
private AdStartedEventListener adStartedEventListener = new AdStartedEventListener() { 
    @Override 
    public void onAdStarted(AdPlaybackEvent adPlaybackEvent) { 
        Ad ad = adPlaybackEvent.getAd(); 
        if (ad == null) { 
            return; 
        } 
 
        _pubOverlay.startAd(adPlaybackEvent.getAdBreak(), ad); 
 
        if (areClickableAdsEnabled() && ad.isClickable()) { 
            _isClickableAdPlaying = true; 
            _playerClickableAdFragment.show(); 
        } 
 
    } 
}; 
 
private AdCompletedEventListener adCompletedEventListener = new AdCompletedEventListener() { 
    @Override 
    public void onAdCompleted(AdPlaybackEvent adPlaybackEvent) { 
        Ad ad = adPlaybackEvent.getAd(); 
        _pubOverlay.stopAd(adPlaybackEvent.getAdBreak(), ad); 
 
        _isClickableAdPlaying = false; 
        if (ad.isClickable()) { 
            _playerClickableAdFragment.hide(); 
        } 
    } 
}; 
 
private AdClickedEventListener adClickedEventListener = new AdClickedEventListener() { 
    @Override 
    public void onAdClicked(AdClickEvent adClickEvent) { 
        AdClick adClick = adClickEvent.getAdClick(); 
        Ad ad = adClickEvent.getAd(); 
 
        String url = adClick.getUrl(); 
        if (url == null || url.trim().equals("")) { 
        } else { 
            Uri uri = Uri.parse(url); 
            Intent intent = new Intent(ACTION_VIEW, uri); 
            try { 
                startActivity(intent); 
            } catch (Exception e) { 
            } 
        } 
 
    } 
}; 
```

