---
description: Die PTMediaPlayer-Schnittstelle kapselt die Funktionalität und das Verhalten eines Medienplayer-Objekts.
title: PTMediaPlayer einrichten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PTMediaPlayer einrichten {#set-up-the-ptmediaplayer}

TVSDK bietet Tools zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.

Verwenden Sie die Tools Ihrer Plattform, um einen Player zu erstellen und ihn mit der Medienplayer-Ansicht in TVSDK zu verbinden, die über Methoden zum Abspielen und Verwalten von Videos verfügt. TVSDK bietet beispielsweise Methoden zum Abspielen und Anhalten. Sie können auf Ihrer Plattform Schaltflächen für die Benutzeroberfläche erstellen und die Schaltflächen festlegen, um diese TVSDK-Methoden aufzurufen.

Die PTMediaPlayer-Schnittstelle kapselt die Funktionalität und das Verhalten eines Medienplayer-Objekts.

Um `PTMediaPlayer`:

1. Rufen Sie die URL des Mediums beispielsweise aus der Benutzeroberfläche in einem Textfeld ab.

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. Erstellen `PTMetadata`.

   Angenommen, Ihre Methode `createMetada` bereitet Metadaten vor (siehe [Werbung](../../ios-3x-advertising/ios-3x-advertising-requirements.md)).

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. Erstellen `PTMediaPlayerItem` durch Verwendung von `PTMetadata` -Instanz.

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. Fügen Sie Benachrichtigungen, die TVSDK sendet, Beobachter hinzu.

   ```
   [self addObservers]
   ```

1. Erstellen `PTMediaPlayer` mit dem neuen `PTMediaPlayerItem`.

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. Legen Sie Eigenschaften auf Ihrem Player fest.

   Hier sind einige der verfügbaren `PTMediaPlayer` properties:

   ```
   player.autoPlay                    = YES;  
   player.closedCaptionDisplayEnabled = YES; 
   player.videoGravity                = PTMediaPlayerVideoGravityResizeAspect;  
   player.allowsAirPlayVideo          = YES;
   ```

1. Legen Sie die Ansichtseigenschaft des Players fest.

   ```
   CGRect playerRect = self.adPlayerView.frame;  
   playerRect.origin = CGPointMake(0, 0); 
   playerRect.size = CGSizeMake(self.adPlayerView.frame.size.width,  
                                self.adPlayerView.frame.size.height); 
   
   [player.view setFrame:playerRect]; 
   [player.view setAutoresizingMask:  
         ( UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight )];
   ```

1. Fügen Sie die Ansicht des Players in der Unteransicht der aktuellen Ansicht hinzu.

   ```
   [self.adPlayerView  setAutoresizesSubviews:YES];  
   [self.adPlayerView addSubview:(UIView *)player.view];
   ```

1. Aufruf `play` , um die Medienwiedergabe zu starten.

   ```
   [player play];
   ```
