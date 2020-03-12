---
description: Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.
seo-description: Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.
seo-title: Videoanalyse initialisieren und konfigurieren
title: Videoanalyse initialisieren und konfigurieren
uuid: d1dc9425-e67c-4e13-aee7-302149352506
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Videoanalyse initialisieren und konfigurieren {#initialize-and-configure-video-analytics}

Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.

Bevor Sie die Videoverfolgung aktivieren (Video Heartbeats), stellen Sie sicher, dass Sie über Folgendes verfügen:

* TVSDK für iOS
* Konfigurations-/Initialisierungsinformationen - Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um Informationen zu Ihrem spezifischen Videoverfolgungskonto zu erhalten:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json </span> </td> 
   <td colname="col2"> <p>Wichtig:  Dieser JSON-Konfigurationsdateiname muss <span class="codeph"> ADBMobileConfig.json bleiben </span>. Der Name und der Pfad dieser Konfigurationsdatei können nicht geändert werden. Der Pfad zu dieser Datei muss <span class="codeph"> &lt;Quellstamm&gt;/AdobeMobile lauten </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AppMeasurement </span> Tracking-Server-Endpunkt </td> 
   <td colname="col2"> Die URL des Back-End-Erfassungsendpunkts von Adobe Analytics (ehemals SiteCatalyst). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Endpunkt des Video Analytics-Trackingservers </td> 
   <td colname="col2"> Die URL des Back-End-Erfassungsendpunkts für die Videoanalyse. Hier werden alle Video Heartbeat-Verfolgungsaufrufe gesendet. <p>Tipp:  Die URL des Besucher-Trackingservers ist identisch mit der URL des Analytics-Trackingservers. Informationen zur Implementierung des Besucher-ID-Diensts finden Sie unter <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external"> Implementieren des ID-Diensts </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Kontoname </td> 
   <td colname="col2"> Auch als Report Suite-ID (RSID) bezeichnet. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Marketing Cloud-Organisations-ID </td> 
   <td colname="col2"> Ein Zeichenfolgenwert, der zum Instanziieren der Besucher-Komponente erforderlich ist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Herausgeber </td> 
   <td colname="col2"> Dies ist die Herausgeber-ID, die Kunden von ihrem Adobe-Kundenbetreuer bereitgestellt wird. <p>Tipp:  Diese ID ist nicht nur eine Zeichenfolge mit dem Namen Marke/TV. </p> </td> 
  </tr> 
 </tbody> 
</table>

So konfigurieren Sie die Videoverfolgung im Player:

1. Vergewissern Sie sich, dass die Optionen für die Ladezeit in der `ADBMobileConfig.json` Ressourcendatei korrekt sind.

   ```
   { 
       "version" : "1.1", 
       "analytics" : { 
           "rsids" : "adobedevelopment", 
           "server" : "10.131.129.149:3000", 
           "charset" : "UTF-8", 
           "ssl" : false, 
           "offlineEnabled" : false, 
           "lifecycleTimeout" : 5, 
           "batchLimit" : 50, 
           "privacyDefault" : "optedin", 
           "poi" : [] 
       }, 
       "marketingCloud": { 
           "org": "ADOBE PROVIDED VALUE"  
       }, 
       "target" : { 
           "clientCode" : "", 
           "timeout" : 5 
       }, 
       "audienceManager" : { 
           "server" : "" 
       } 
   }
   ```

   Diese JSON-formatierte Konfigurationsdatei ist als Ressource mit TVSDK gebündelt. Ihr Player liest diese Werte nur zur Ladezeit und die Werte bleiben konstant, während Ihre Anwendung ausgeführt wird.

   So konfigurieren Sie die Optionen für die Ladezeit:

   1. Vergewissern Sie sich, dass die `ADBMobileConfig.json` Datei die entsprechenden Werte enthält, die von Adobe bereitgestellt werden.
   1. Vergewissern Sie sich, dass sich diese Datei im `AdobeMobile` Ordner befindet.

      Dieser Ordner muss sich im Stammverzeichnis der Anwendungsquelle befinden.
   1. Kompilieren und erstellen Sie Ihre Anwendung.
   1. Stellen Sie die gebündelte Anwendung bereit und führen Sie sie aus.

      Weitere Informationen zu diesen AppMeasurement-Einstellungen finden Sie unter [Videomessung in Adobe Analytics](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/).
1. Initialisieren und Konfigurieren von Video Heartbeat-Verfolgungsmetadaten.

   >[!IMPORTANT]
   >
   >Sie können den Midstream des Videoanalysemoduls stoppen und ihn bei Bedarf erneut initialisieren. Bevor das Modul neu initialisiert wird, stellen Sie sicher, dass die Videoanalysemetadaten auch auf die richtigen Inhaltsmetadaten aktualisiert werden. Wiederholen Sie die Unterschritte 1 und 2, um die Metadaten neu zu erstellen.

   1. Erstellen Sie eine Instanz der Videoanalysemetadaten.

      Diese Instanz enthält alle Konfigurationsinformationen, die zur Aktivierung der Video Heartbeat-Verfolgung erforderlich sind. Beispiel:

      ```
      - (PTVideoAnalyticsTrackingMetadata *)getVideoAnalyticsTrackingMetadata 
      { 
          PTVideoAnalyticsTrackingMetadata *vaTrackingMetadata =  
            [[[PTVideoAnalyticsTrackingMetadata alloc]  
                 initWithTrackingServer:@"example.com" 
                 publisher:@"sample-publisher"] autorelease]; 
      
          // Set these to NO for production deployment. 
          vaTrackingMetadata.debugLogging = YES;  
          vaTrackingMetadata.quietMode = NO; 
      
          vaTrackingMetadata.channel = @"test-channel"; 
          vaTrackingMetadata.videoName = @"myvideo"; 
          vaTrackingMetadata.videoId = @"myvideoid"; 
          vaTrackingMetadata.playerName = @"PSDK Player"; 
          vaTrackingMetadata.enableChapterTracking = YES; 
          vaTrackingMetadata.useSSL = NO; 
          // use this API to override the default asset length -1 for live streams 
          vaTrackingMetadata.assetDuration = SAMPLE_ASSET_DURATION; 
      
      }
      ```

   1. Hinzufügen Sie die Video Analytics-Metadaten zur globalen Metadateninstanz.

      Wenn Sie bereit sind, legen Sie die Instanz der globalen Metadaten auf der Medienressource oder dem Medienplayer-Element fest:

      ```
      - (PTMetadata *)createMetadata 
      { 
          PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
      
          [metadata setMetadata:[self getVideoAnalyticsTrackingMetadata]  
            forKey:PTVideoAnalyticsTrackingMetadataKey]; 
      
          return metadata; 
      } 
      
      PTMetadata *metadata = [self createMetadata]; 
      
      PTMediaPlayerItem *item =  
        [[[PTMediaPlayerItem alloc] initWithUrl:[[[NSURL alloc]  
          initWithString:@"media-url"] autorelease] 
          mediaId:@"media-id" metadata:metadata] autorelease];
      ```

   1. Initialisieren Sie den Video Analytics-Tracker.

      Nachdem Sie eine Medienplayer-Instanz erstellt haben, müssen Sie eine Video Analytics-Trackerinstanz erstellen und einen Verweis auf die Medienplayer-Instanz angeben.

      >[!TIP]
      >
      >Erstellen Sie immer eine neue Trackerinstanz für jede Inhaltswiedergabesitzung und entfernen Sie den vorherigen Verweis, nachdem Sie die Medienplayer-Instanz entfernt haben.

      ```
      self.videoAnalyticsTracker =  
        [[[PTVideoAnalyticsTracker alloc] initWithMediaPlayer:self.player] autorelease];
      ```

   1. Zerstören Sie den Video Analytics-Tracker.

      Bevor Sie eine neue Sitzung zur Inhaltswiedergabe starten, müssen Sie die vorherige Instanz des Videoverfolgers zerstören. Nachdem Sie das Inhaltsbeendigungsereignis (oder die Benachrichtigung) erhalten haben, warten Sie einige Minuten, bevor Sie die Videotrackerinstanz zerstören. Das sofortige Zerstören der Instanz kann die Fähigkeit des Video Analytics-Trackers beeinträchtigen, einen Ping für die Videobeendigung zu senden.

      ```
      self.videoAnalyticsTracker = nil;
      ```

   1. Markieren Sie den Live/Linear-Stream manuell als abgeschlossen.

      Wenn Sie verschiedene Folgen für einen Live-Stream haben, können Sie eine Folge manuell mit der vollständigen API als abgeschlossen kennzeichnen. Dadurch wird die Videoverfolgungssitzung für die aktuelle Videoepisode beendet, und Sie können eine neue Verfolgungssitzung für die nächste Folge Beginn haben.

      >[!TIP]
      >
      >Diese API ist optional und wird für die VOD-Videoverfolgung nicht benötigt.

      ```
      if (self.videoAnalyticsTracker) 
      { 
         [self.videoAnalyticsTracker trackVideoComplete];   
      }
      ```
