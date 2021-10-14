---
description: Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.
title: Videoanalyse initialisieren und konfigurieren
exl-id: 3f108ca4-2562-4400-b4e2-10933bde3254
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Videoanalyse initialisieren und konfigurieren {#initialize-and-configure-video-analytics}

Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.

Stellen Sie vor der Aktivierung der Videoverfolgung (Video Heartbeats) sicher, dass Sie über Folgendes verfügen:

* TVSDK für iOS
* Konfiguration/Initialisierungsinformationen - Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um Informationen zu Ihrem spezifischen Video-Tracking-Konto zu erhalten:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>Wichtig:  Dieser JSON-Konfigurationsdateiname muss <span class="codeph"> ADBMobileConfig.json </span> bleiben. Der Name und der Pfad dieser Konfigurationsdatei können nicht geändert werden. Der Pfad zu dieser Datei muss <span class="codeph"> &lt;source root&gt;/AdobeMobile </span> lauten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> Endpunkt des AppMeasurement- </span> Tracking-Servers </td> 
   <td colname="col2"> Die URL des Back-End-Erfassungsendpunkts der Adobe Analytics (ehemals SiteCatalyst). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Video Analytics-Tracking-Server-Endpunkt </td> 
   <td colname="col2"> Die URL des Back-End-Erfassungsendpunkts für die Videoanalyse. Hier werden alle Video Heartbeat-Tracking-Aufrufe gesendet. <p>Tipp:  Die URL des Besucher-Tracking-Servers entspricht der URL des Analytics-Tracking-Servers. Informationen zur Implementierung des Besucher-ID-Diensts finden Sie unter <a href="https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-target.html?lang=en" format="html" scope="external"> Implementieren des ID-Diensts </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Kontoname </td> 
   <td colname="col2"> Wird auch als Report Suite-ID (RSID) bezeichnet. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Organisations-ID des Marketing Cloud </td> 
   <td colname="col2"> Ein string -Wert, der für die Instanziierung der Besucherkomponente erforderlich ist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Herausgeber </td> 
   <td colname="col2"> Dies ist die Herausgeber-ID, die Kunden von ihrem Adobe-Support-Mitarbeiter bereitgestellt wird. <p>Tipp:  Diese ID ist nicht nur eine Zeichenfolge mit dem Namen der Marke/des Fernsehgeräts. </p> </td> 
  </tr> 
 </tbody> 
</table>

So konfigurieren Sie das Video-Tracking in Ihrem Player:

1. Überprüfen Sie, ob die Ladezeitoptionen in der Ressourcendatei `ADBMobileConfig.json` korrekt sind.

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

   Diese JSON-formatierte Konfigurationsdatei ist als Ressource mit TVSDK gebündelt. Ihr Player liest diese Werte nur während des Ladevorgangs und die Werte bleiben konstant, während Ihre Anwendung ausgeführt wird.

   So konfigurieren Sie Ladezeitoptionen:

   1. Vergewissern Sie sich, dass die `ADBMobileConfig.json`-Datei die entsprechenden Werte enthält, die von Adobe bereitgestellt werden.
   1. Vergewissern Sie sich, dass sich diese Datei im Ordner `AdobeMobile` befindet.

      Dieser Ordner muss sich im Stammverzeichnis der Quellstruktur der Anwendung befinden.
   1. Kompilieren und erstellen Sie Ihre Anwendung.
   1. Stellen Sie die gebündelte Anwendung bereit und führen Sie sie aus.

      Weitere Informationen zu diesen AppMeasurement-Einstellungen finden Sie unter [Videomessung in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=en).
1. Initialisieren und Konfigurieren von Video Heartbeat-Tracking-Metadaten.

   >[!IMPORTANT]
   >
   >Sie können das Video Analytics-Modul Midstream anhalten und es bei Bedarf erneut initialisieren. Bevor das Modul neu initialisiert wird, stellen Sie sicher, dass die Metadaten für die Videoanalyse auch auf die richtigen Inhaltsmetadaten aktualisiert werden. Wiederholen Sie die Unterschritte 1 und 2, um die Metadaten neu zu erstellen.

   1. Erstellen Sie eine Instanz der Video Analytics-Metadaten.

      Diese Instanz enthält alle Konfigurationsinformationen, die zum Aktivieren der Video Heartbeat-Verfolgung erforderlich sind. Beispiel:

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

   1. Fügen Sie die Video Analytics-Metadaten zur globalen Metadateninstanz hinzu.

      Wenn Sie bereit sind, legen Sie die globale Metadateninstanz für die Medienressource oder das Medienplayer-Element fest:

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

      Nachdem Sie eine Medienplayer-Instanz erstellt haben, müssen Sie eine Video Analytics-Tracker-Instanz erstellen und einen Verweis auf die Medienplayer-Instanz angeben.

      >[!TIP]
      >
      >Erstellen Sie immer eine neue Tracker-Instanz für jede Inhaltswiedergabesitzung und entfernen Sie die vorherige Referenz, nachdem Sie die Medienplayer-Instanz getrennt haben.

      ```
      self.videoAnalyticsTracker =  
        [[[PTVideoAnalyticsTracker alloc] initWithMediaPlayer:self.player] autorelease];
      ```

   1. Zerstören Sie den Video Analytics-Tracker.

      Bevor Sie eine neue Inhaltswiedergabesitzung starten, zerstören Sie die vorherige Instanz des Video-Trackers. Warten Sie einige Minuten, nachdem Sie das Ereignis zum Abschluss des Inhalts (oder die Benachrichtigung) erhalten haben, bevor Sie die Video-Tracker-Instanz zerstören. Das sofortige Zerstören der Instanz kann die Fähigkeit des Video Analytics-Trackers beeinträchtigen, einen Video-complete-Ping zu senden.

      ```
      self.videoAnalyticsTracker = nil;
      ```

   1. Markieren Sie den Live-/Linear-Stream manuell als abgeschlossen.

      Wenn sich in einem Live-Stream mehrere Folgen befinden, können Sie eine Folge mithilfe der vollständigen API manuell als abgeschlossen markieren. Dadurch wird die Video-Tracking-Sitzung für die aktuelle Videoepisode beendet. Sie können für die nächste Folge eine neue Tracking-Sitzung starten.

      >[!TIP]
      >
      >Diese API ist optional und für das VOD-Video-Tracking nicht erforderlich.

      ```
      if (self.videoAnalyticsTracker) 
      { 
         [self.videoAnalyticsTracker trackVideoComplete];   
      }
      ```
