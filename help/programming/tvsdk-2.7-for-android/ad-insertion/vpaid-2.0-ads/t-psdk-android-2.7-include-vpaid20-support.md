---
description: Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.
seo-description: Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.
seo-title: Implementierung der VPAID 2.0-Integration
title: Implementierung der VPAID 2.0-Integration
uuid: fa5b9cdd-e684-4656-91b7-50781dc59e23
translation-type: tm+mt
source-git-commit: 25f97c8d296f71deddc8f9d12b97007ddf73f603
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 2%

---


# Implementierung der VPAID 2.0-Integration {#implement-vpaid-integration}

Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.

So fügen Sie VPAID 2.0-Unterstützung hinzu:

1. hinzufügen Sie die benutzerdefinierte Anzeigenschnittstelle auf die Player-Oberfläche, wenn der Player den Status &quot;VORBEREITT&quot;aufweist.

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

1. Erstellen Sie Listener und verarbeiten Sie die Ereignis, die unter Ereignis-Listener beschrieben werden.

   >[!IMPORTANT]
   >
   >In einem VPAID 2.0-Arbeitsablauf ist es bei Ansichten mit benutzerdefinierten Anzeigen sehr wichtig, die `CustomAdView`-Instanz über `AdBreak`-Beginn (Ereignis `AD_BREAK_START`) und `AdBreak`-Abschlüsse (Ereignis `AD_BREAK_COMPLETE`) zu verwalten, vom Zeitpunkt der Erstellung der Ansicht der benutzerdefinierten Anzeige bis zum Zeitpunkt der Entsorgung. Erstellen Sie also nicht bei jedem Werbeunterbrechungs-Beginn eine benutzerdefinierte Ansicht und löschen Sie sie bei jedem Werbeunterbrechungsvorgang.
   >
   >
   >Darüber hinaus sollten Sie Ihre benutzerdefinierte AnzeigenAnsicht nur erstellen, wenn Ihr Player den Status &quot;VORBEREITT&quot;aufweist.
   >
   >
   >Entsorgen Sie die Ansicht der benutzerdefinierten Anzeige nur bei Aufruf des Zurücksetzens. Beispiel:
   >
   >
   ```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >```
   >
   >Bevor Sie Ihre benutzerspezifische Anzeigendatei löschen, müssen Sie sie schließlich aus der Ansicht `FrameLayout` entfernen. Beispiel:
   >
   >
   ```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
