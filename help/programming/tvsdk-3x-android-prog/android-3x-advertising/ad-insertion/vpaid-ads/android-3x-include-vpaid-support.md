---
description: Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenansicht und entsprechende Listener hinzu.
title: Implementieren der VPAID 2.0-Integration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Implementieren der VPAID 2.0-Integration {#implement-vpaid-integration}

Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenansicht und entsprechende Listener hinzu.

1. Fügen Sie die benutzerdefinierte Anzeigenansicht zur Player-Oberfläche hinzu, wenn der Player den Status VORBEREITET aufweist.

   ```java
   ... 
   private FrameLayout _playerFrame; 
       ... 
       case PREPARED: 
           ... 
           addCustomView(); 
   ... 
   private void addCustomView() { 
       ... 
       WebView view = (WebView)_mediaPlayer.getCustomAdView(); 
       ... 
       _playerFrame.addView(view);
   ```

1. Erstellen Sie Listener und verarbeiten Sie die Ereignisse, die unter [Veranstaltungen](../../../../tvsdk-3x-android-prog/android-3x-events-notifications/events-summary/android-3x-events-summary.md).

   >[!IMPORTANT]
   >
   >In einem VPAID 2.0-Workflow ist es bei benutzerdefinierten Anzeigen sehr wichtig, Ihre `CustomAdView` Instanz über `AdBreak` starts (event `AD_BREAK_START`) und `AdBreak` completes (event `AD_BREAK_COMPLETE`), vom Zeitpunkt der Erstellung der benutzerdefinierten Anzeigenansicht bis zum Zeitpunkt der Anzeige. Erstellen Sie also nicht bei jedem Start einer Werbeunterbrechung eine benutzerdefinierte Anzeigenansicht und deaktivieren Sie sie bei jedem Abschluss einer Werbeunterbrechung.
   >
   >
   >Darüber hinaus sollten Sie Ihre benutzerdefinierte Anzeigenansicht nur erstellen, wenn Ihr Player den Status VORBEREITT aufweist.
   >
   >
   >Die benutzerdefinierte Anzeigenansicht wird nur beim Zurücksetzen angezeigt. Beispiel:
   >
   >```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >```
   >
   >Bevor Sie Ihre benutzerdefinierte Anzeigenansicht anzeigen, müssen Sie sie schließlich aus dem `FrameLayout`. Beispiel:
   >
   >```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
