---
description: Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, muss Ihre Anwendung reagieren. TVSDK liefert Informationen zur Ziel-URL für den Klick.
title: Antworten auf Klicks auf Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Antworten auf Klicks auf Anzeigen{#respond-to-clicks-on-ads}

Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, muss Ihre Anwendung reagieren. TVSDK liefert Informationen zur Ziel-URL für den Klick.

1. Um einen Ereignis-Listener für TVSDK einzurichten und die Clickthrough-Informationen bereitzustellen, registrieren Sie eine `AdClickedEventListener.onAdClicked`.

   Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, sendet TVSDK diese Benachrichtigung, einschließlich Informationen zum Ziel des Klicks.
1. Überwachen Sie Benutzerinteraktionen auf anklickbaren Anzeigen.
1. Wenn der Benutzer die Anzeige oder Schaltfläche berührt oder klickt, rufen Sie `notifyClick` auf `MediaPlayerView`.
1. Suchen Sie nach `onAdClick(AdClickEvent event)` -Ereignis von TVSDK.
1. Verwenden Sie zum Abrufen der Clickthrough-URL und der zugehörigen Informationen die Getter-Methoden für die `AdClickEvent` -Instanz.
1. Anhalten des Videos

   Weitere Informationen zum Anhalten des Videos finden Sie unter [Wiedergabe anhalten und fortsetzen.](../../ad-insertion/clickable-ads/android-1.4-pausing-resuming-playback.md).
1. Verwenden Sie die Clickthrough-Informationen, um die Anzeigen-Clickthrough-URL und die zugehörigen Informationen anzuzeigen.

       Sie können die Informationen beispielsweise auf eine der folgenden Arten anzeigen:
   
   * Öffnen Sie in Ihrer Anwendung die Clickthrough-URL in einem Browser.

     Auf Desktop-Plattformen wird der Bereich für die Videoanzeige verwendet, um Clickthrough-URLs bei Benutzerklicks aufzurufen.
   * Leiten Sie Benutzer zu ihrem externen mobilen Webbrowser um.

     Auf Mobilgeräten wird der Bereich für die Videoanzeige für andere Funktionen verwendet, z. B. zum Ausblenden und Anzeigen von Steuerelementen, zum Anhalten der Wiedergabe, zum Erweitern auf den Vollbildmodus usw. Auf diesen Geräten wird eine separate Ansicht, z. B. eine Sponsorschaltfläche, verwendet, um die Clickthrough-URL zu starten.

1. Schließen Sie das Browser-Fenster, in dem die Clickthrough-Informationen angezeigt werden, und setzen Sie die Wiedergabe des Videos fort.

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
