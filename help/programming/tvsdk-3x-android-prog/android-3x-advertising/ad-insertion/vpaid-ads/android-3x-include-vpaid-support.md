---
description: Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.
seo-description: Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.
seo-title: Implementierung der VPAID 2.0-Integration
title: Implementierung der VPAID 2.0-Integration
uuid: d512fb5b-001c-4a7a-a553-d5962002bb30
translation-type: tm+mt
source-git-commit: 1034a0520590777cc0930d2f732741202bc3bc04

---


# Implementierung der VPAID 2.0-Integration {#implement-vpaid-integration}

Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.

1. Hinzufügen Sie die benutzerdefinierte Anzeigenschnittstelle auf die Player-Oberfläche, wenn der Player den Status &quot;VORBEREITT&quot;aufweist.

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

1. Erstellen Sie Listener und verarbeiten Sie die in den [Ereignissen](../../../../tvsdk-3x-android-prog/android-3x-events-notifications/events-summary/android-3x-events-summary.md)beschriebenen Ereignis.

   >[!IMPORTANT]
   >
   >In einem VPAID 2.0-Arbeitsablauf ist es bei Ansichten mit benutzerdefinierten Anzeigen sehr wichtig, Ihre `CustomAdView` Instanz über `AdBreak` Beginn (Ereignis `AD_BREAK_START`) und `AdBreak` Abschlüsse (Ereignis `AD_BREAK_COMPLETE`) hinweg zu verwalten, vom Zeitpunkt der Erstellung der Ansicht der benutzerdefinierten Anzeige bis zum Zeitpunkt der Entsorgung. Erstellen Sie also nicht bei jedem Werbeunterbrechungs-Beginn eine benutzerdefinierte Ansicht und löschen Sie sie bei jedem Werbeunterbrechungsvorgang.
   >
   >
   >Darüber hinaus sollten Sie Ihre benutzerdefinierte AnzeigenAnsicht nur erstellen, wenn Ihr Player den Status &quot;VORBEREITT&quot;aufweist.
   >
   >
   >Entsorgen Sie die Ansicht der benutzerdefinierten Anzeige nur bei Aufruf des Zurücksetzens. Beispiel:    >
   >
   >
   ```>
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >```

   Bevor Sie Ihre benutzerspezifische Anzeigendatei freigeben, müssen Sie sie schließlich aus der Ansicht `FrameLayout`entfernen. Beispiel:
   >```
   >if (_playerFrame != null) 
      _playerFrame.removeAllViews(); 
   ```
