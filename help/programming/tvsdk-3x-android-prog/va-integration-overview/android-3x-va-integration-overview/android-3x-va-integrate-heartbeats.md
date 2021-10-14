---
title: Videoanalyse initialisieren und konfigurieren
description: Videoanalyse initialisieren und konfigurieren
copied-description: true
exl-id: 26bdc11e-b8f6-414f-a3e9-53bc895d25ce
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Videoanalyse initialisieren und konfigurieren {#initialize-and-configure-video-analytics}

Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.
Stellen Sie vor der Aktivierung der Videoverfolgung (Video Heartbeats) sicher, dass Sie über Folgendes verfügen:

* TVSDK 3.0 für Android.
* Konfigurations-/Initialisierungsinformationen

   Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um Informationen zu Ihrem spezifischen Video-Tracking-Konto zu erhalten:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>Wichtig:  Dieser JSON-Konfigurationsdateiname muss <span class="filepath"> ADBMobileConfig.json </span> bleiben. Der Name und der Pfad dieser Konfigurationsdatei können nicht geändert werden. Der Pfad zu dieser Datei muss <span class="filepath"> &lt;source root&gt;/assets </span> lauten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Endpunkt des AppMeasurement-Tracking-Servers </td> 
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


   1. Vergewissern Sie sich, dass die `ADBMobileConfig.json`-Datei die entsprechenden Werte enthält (bereitgestellt von Adobe).
   1. Vergewissern Sie sich, dass sich diese Datei im Ordner `assets/` befindet.

      Dieser Ordner muss sich im Stammverzeichnis der Quellstruktur der Anwendung befinden.

   1. Kompilieren und erstellen Sie Ihre Anwendung.
   1. Stellen Sie die gebündelte Anwendung bereit und führen Sie sie aus.

      Weitere Informationen zu diesen AppMeasurement-Einstellungen finden Sie unter [Videomessung in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=en).

1. Initialisieren und Konfigurieren von Video Heartbeat-Tracking-Metadaten.

   >[!IMPORTANT]
   >
   >Sie können das Video Analytics-Modul Midstream anhalten und es bei Bedarf erneut initialisieren. Bevor das Modul neu initialisiert wird, stellen Sie sicher, dass die Metadaten für die Videoanalyse auch auf die richtigen Inhaltsmetadaten aktualisiert werden. Um die Metadaten neu zu erstellen, wiederholen Sie die ersten beiden Schritte unten (die Unterschritte **a** und **b**).

   1. Erstellen Sie eine Instanz der Video Analytics-Metadaten.

      Diese Instanz enthält alle Konfigurationsinformationen, die zum Aktivieren der Video Heartbeat-Verfolgung erforderlich sind. Beispiel:

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

   1. Initialisieren Sie den Video Analytics-Provider.

      Nachdem Sie eine Medienplayer-Instanz erstellt haben, müssen Sie eine Video Analytics-Anbieterinstanz erstellen und den Anwendungskontext angeben.

      >[!TIP]
      >
      >Erstellen Sie immer eine neue Anbieterinstanz für jede Inhaltswiedergabesitzung und entfernen Sie die vorherige Referenz, nachdem Sie die Medienplayer-Instanz getrennt haben.

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider = new VideoAnalyticsProvider(appContext); 
      ```

   1. Legen Sie die Video Analytics-Metadaten auf der `videoAnalyticsProvider`-Instanz fest.

      ```java
      videoAnalyticsProvider.setVideoAnalyticsMetadata(vaMetadata);
      ```

   1. Hängen Sie die Medienplayer-Instanz an die `videoAnalyticsProvider`-Instanz an:

      ```java
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. Zerstören Sie den Video Analytics-Anbieter.

      Bevor Sie eine neue Inhaltswiedergabesitzung starten, zerstören Sie die vorherige Instanz des Videoanbieters. Nachdem Sie das Ereignis zum Abschluss des Inhalts (oder die Benachrichtigung) erhalten haben, warten Sie einige Minuten, bis Sie die Provider-Instanz für die Videoanalyse zerstören. Die sofortige Zerstörung der Instanz kann die Fähigkeit des Video Analytics-Anbieters beeinträchtigen, einen &quot;Video complete&quot;-Ping zu senden.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.detachMediaPlayer(); 
          videoAnalyticsProvider = null; 
      }
      ```

   1. Markieren Sie den Live-/Linear-Stream manuell als abgeschlossen.

      Wenn sich in einem Live-Stream mehrere Folgen befinden, können Sie eine Folge mithilfe der vollständigen API manuell als abgeschlossen markieren. Dadurch wird die Video-Tracking-Sitzung für die aktuelle Videoepisode beendet. Sie können für die nächste Folge eine neue Tracking-Sitzung starten.

      >[!TIP]
      >
      >Diese API ist optional und funktioniert nicht für das VOD-Video-Tracking.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.trackVideoComplete();    
      }
      ```
