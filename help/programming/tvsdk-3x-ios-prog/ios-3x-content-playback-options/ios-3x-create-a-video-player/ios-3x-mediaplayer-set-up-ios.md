---
description: Die PTMediaPlayer-Schnittstelle kapselt die Funktionalität und das Verhalten eines Medienplayer-Objekts.
seo-description: Die PTMediaPlayer-Schnittstelle kapselt die Funktionalität und das Verhalten eines Medienplayer-Objekts.
seo-title: Einrichten des PTMediaPlayer
title: Einrichten des PTMediaPlayer
uuid: 698034d3-1260-416f-83b0-6b7d058750a0
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Einrichten des PTMediaPlayer {#set-up-the-ptmediaplayer}

TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.

Verwenden Sie die Tools Ihrer Plattform, um einen Player zu erstellen und ihn mit der Media Player-Ansicht in TVSDK zu verbinden, die über Methoden zum Abspielen und Verwalten von Videos verfügt. TVSDK bietet beispielsweise Methoden zum Abspielen und Anhalten. Sie können auf Ihrer Plattform Schaltflächen für die Benutzeroberfläche erstellen und die Schaltflächen einstellen, um diese TVSDK-Methoden aufzurufen.

Die PTMediaPlayer-Schnittstelle kapselt die Funktionalität und das Verhalten eines Medienplayer-Objekts.

So richten Sie Ihre `PTMediaPlayer`:

1. Rufen Sie beispielsweise die URL des Mediums von Ihrer Benutzeroberfläche in ein Textfeld ab.

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. Erstellen `PTMetadata`.

   Angenommen, Ihre Methode `createMetada` bereitet Metadaten vor (siehe [Werbung](../../ios-3x-advertising/ios-3x-advertising-requirements.md)).

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. Erstellen Sie `PTMediaPlayerItem` mithilfe Ihrer `PTMetadata` Instanz.

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. Hinzufügen Beobachter zu Benachrichtigungen, die TVSDK sendet.

   ```
   [self addObservers]
   ```

1. Erstellen Sie `PTMediaPlayer` mit Ihrem neuen `PTMediaPlayerItem`.

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. Legen Sie Eigenschaften für Ihren Player fest.

   Nachfolgend sind einige der verfügbaren `PTMediaPlayer` Eigenschaften aufgeführt:

   ```
   player.autoPlay                    = YES;  
   player.closedCaptionDisplayEnabled = YES; 
   player.videoGravity                = PTMediaPlayerVideoGravityResizeAspect;  
   player.allowsAirPlayVideo          = YES;
   ```

1. Legen Sie die Eigenschaft &quot;Ansicht&quot;des Players fest.

   ```
   CGRect playerRect = self.adPlayerView.frame;  
   playerRect.origin = CGPointMake(0, 0); 
   playerRect.size = CGSizeMake(self.adPlayerView.frame.size.width,  
                                self.adPlayerView.frame.size.height); 
   
   [player.view setFrame:playerRect]; 
   [player.view setAutoresizingMask:  
         ( UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight )];
   ```

1. Hinzufügen der Ansicht des Spielers in der Unteransicht der aktuellen Ansicht.

   ```
   [self.adPlayerView  setAutoresizesSubviews:YES];  
   [self.adPlayerView addSubview:(UIView *)player.view];
   ```

1. Aufruf `play` der Medienwiedergabe im Beginn.

   ```
   [player play];
   ```
