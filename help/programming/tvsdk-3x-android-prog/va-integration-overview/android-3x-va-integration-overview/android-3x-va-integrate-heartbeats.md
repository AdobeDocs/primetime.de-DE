---
description: 'null'
seo-description: 'null'
seo-title: Videoanalyse initialisieren und konfigurieren
title: Videoanalyse initialisieren und konfigurieren
uuid: c49c77d9-66b9-4586-9d70-b139b4a97a7a
translation-type: tm+mt
source-git-commit: 1985694f99c548284aad6e6b4e070bece230bdf4
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---


# Videoanalyse initialisieren und konfigurieren {#initialize-and-configure-video-analytics}

Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.
Bevor Sie die Videoverfolgung aktivieren (Video Heartbeats), stellen Sie sicher, dass Sie über Folgendes verfügen:

* TVSDK 3.0 für Android.
* Konfigurations-/Initialisierungsinformationen

   Wenden Sie sich an Ihren Kundenbetreuer, um Informationen zu Ihrem spezifischen Videoverfolgungskonto zu erhalten:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json </span> </td> 
   <td colname="col2"> <p>Wichtig:  Dieser JSON-Konfigurationsdateiname muss <span class="filepath"> ADBMobileConfig.json bleiben </span>. Der Name und der Pfad dieser Konfigurationsdatei können nicht geändert werden. Der Pfad zu dieser Datei muss <span class="filepath"> &lt;Quellstamm&gt;/assets lauten </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Endpunkt des AppMeasurement-Tracking-Servers </td> 
   <td colname="col2"> Die URL des Back-End-Erfassungsendpunkts Adobe Analytics (früher SiteCatalyst). </td> 
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
   <td colname="col1"> Organisations-ID des Marketing Cloud </td> 
   <td colname="col2"> Ein Zeichenfolgenwert, der zum Instanziieren der Besucher-Komponente erforderlich ist. </td> 
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


   1. Vergewissern Sie sich, dass die `ADBMobileConfig.json` Datei die entsprechenden Werte enthält (von der Adobe bereitgestellt).
   1. Vergewissern Sie sich, dass sich diese Datei im `assets/` Ordner befindet.

      Dieser Ordner muss sich im Stammverzeichnis der Anwendungsquelle befinden.

   1. Kompilieren und erstellen Sie Ihre Anwendung.
   1. Stellen Sie die gebündelte Anwendung bereit und führen Sie sie aus.

      Weitere Informationen zu diesen AppMeasurement-Einstellungen finden Sie unter [Videomessung in Adobe Analytics](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/).

1. Initialisieren und Konfigurieren von Video Heartbeat-Verfolgungsmetadaten.

   >[!IMPORTANT]
   >
   >Sie können den Midstream des Videoanalysemoduls stoppen und ihn bei Bedarf erneut initialisieren. Bevor das Modul neu initialisiert wird, stellen Sie sicher, dass die Videoanalysemetadaten auch auf die richtigen Inhaltsmetadaten aktualisiert werden. Um die Metadaten neu zu erstellen, wiederholen Sie die ersten beiden Schritte unten (Unterschritte **a** und **b**).

   1. Erstellen Sie eine Instanz der Videoanalysemetadaten.

      Diese Instanz enthält alle Konfigurationsinformationen, die zur Aktivierung der Video Heartbeat-Verfolgung erforderlich sind. Beispiel:

      ```java
      private VideoAnalyticsMetadata getVideoAnalyticsTrackingMetadata() { 
          VideoAnalyticsMetadata vaMetadata = new VideoAnalyticsMetadata(); 
      
          vaMetadata.setTrackingServer("example.com"); 
          vaMetadata.setChannel("test-channel"); 
          vaMetadata.setVideoName("myvideo"); 
          vaMetadata.setVideoId("myvideoid"); 
          vaMetadata.setPlayerName("PSDK Player"); 
          vaMetadata.setUseSSL(false); 
          vaMetadata.debugLogging = true; // Set to NO for production deployment. 
          vaMetadata.setEnableChapterTracking(true); 
          // use this API to override the default asset length -1 for live streams 
          vaMetadata.setAssetDuration(SAMPLE_ASSET_DURATION); 
      
          return vaMetadata; 
      }
      ```

   1. Initialisieren Sie den Videoanalyseanbieter.

      Nachdem Sie eine Medienplayer-Instanz erstellt haben, müssen Sie eine Video Analytics-Provider-Instanz erstellen und den Anwendungskontext angeben.

      >[!TIP]
      >
      >Erstellen Sie immer eine neue Anbieterinstanz für jede Inhaltswiedergabesitzung und entfernen Sie den vorherigen Verweis, nachdem Sie die Medienplayer-Instanz entfernt haben.

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider = new VideoAnalyticsProvider(appContext); 
      ```

   1. Legen Sie die Video Analytics-Metadaten für die `videoAnalyticsProvider` Instanz fest.

      ```java
      videoAnalyticsProvider.setVideoAnalyticsMetadata(vaMetadata);
      ```

   1. Hängen Sie die Medienplayer-Instanz an die `videoAnalyticsProvider` Instanz an:

      ```java
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. Zerstören Sie den Videoanalyseanbieter.

      Bevor Sie eine neue Sitzung zur Inhaltswiedergabe starten, müssen Sie die vorherige Instanz des Videoanbieters zerstören. Nachdem Sie das Inhaltsbeendigungsereignis (oder die Benachrichtigung) erhalten haben, warten Sie einige Minuten, bevor Sie die Videoanalyseanbieterinstanz zerstören. Das sofortige Zerstören der Instanz kann die Fähigkeit des Videoanalyseanbieters beeinträchtigen, einen Ping zur Videobeendigung zu senden.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.detachMediaPlayer(); 
          videoAnalyticsProvider = null; 
      }
      ```

   1. Markieren Sie den Live/Linear-Stream manuell als abgeschlossen.

      Wenn Sie verschiedene Folgen für einen Live-Stream haben, können Sie eine Folge manuell mit der vollständigen API als abgeschlossen kennzeichnen. Dadurch wird die Videoverfolgungssitzung für die aktuelle Videoepisode beendet, und Sie können für die nächste Folge eine neue Verfolgungssitzung Beginn geben.

      >[!TIP]
      >
      >Diese API ist optional und funktioniert nicht bei der VOD-Videoverfolgung.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.trackVideoComplete();    
      }
      ```
