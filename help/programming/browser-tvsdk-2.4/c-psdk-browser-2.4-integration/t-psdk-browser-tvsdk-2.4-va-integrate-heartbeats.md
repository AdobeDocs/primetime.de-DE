---
description: Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.
title: Videoanalyse initialisieren und konfigurieren
exl-id: e0bf461b-a431-4fba-bd3d-c38be307a92f
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---

# Videoanalyse initialisieren und konfigurieren {#initialize-and-configure-video-analytics}

Sie können Ihren Player so konfigurieren, dass die Videonutzung verfolgt und analysiert wird.

Stellen Sie vor der Aktivierung der Videoverfolgung (Video Heartbeats) sicher, dass Sie über Folgendes verfügen:

* Konfiguration/Browser TVSDK-Initialisierungsinformationen - Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um Informationen zu Ihrem spezifischen Video-Tracking-Konto zu erhalten:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84">
 <tbody>
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
  <tr>
   <td colname="col1"> Besucher-Tracking-Server-Endpunkt </td>
   <td colname="col2"> Die URL des Backend-Endpunkts, der eine eindeutige Kennung für den aktuellen Video-Viewer bereitstellt. </td>
  </tr>
  <tr>
   <td colname="col1"> Herausgeber </td>
   <td colname="col2"> Dies ist die Herausgeber-ID, die Kunden von ihrem Adobe-Support-Mitarbeiter bereitgestellt wird. <p>Tipp:  Diese ID ist nicht nur eine Zeichenfolge mit dem Namen der Marke/des Fernsehgeräts. </p> </td>
  </tr>
 </tbody>
</table>

So konfigurieren Sie das Video-Tracking in Ihrem Player:

1. Instanziieren und konfigurieren Sie die VisitorAPI-Bibliothek.

       Beachten Sie die folgenden Informationen:
   
   * Für die Instanziierung ist ein Eingabeparameter für die Marketing Cloud-Organisations-ID erforderlich, der von Adobe bereitgestellt wird.

      Dies ist ein Zeichenfolgenwert.
   * Die einzige Konfigurationsoption für die VisitorAPI-Bibliothek ist die URL des Backend-Endpunkts, der die eindeutige Kennung für den aktuellen Benutzer bereitstellt.
   * Die URL des Besucher-Tracking-Servers entspricht der URL des Analytics-Tracking-Servers.

      Informationen zur Implementierung des Besucher-ID-Diensts finden Sie unter [Implementierung des Besucher-ID-Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-target.html?lang=en).

   ```js
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID");
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”;
   ```

2. Instanziieren und konfigurieren Sie die AppMeasurement-Komponente.

   Die AppMeasurement-Instanz verfügt über viele Konfigurationsoptionen. Weitere Informationen finden Sie in der Dokumentation [Adobe Analytics Developer](https://microsite.omniture.com/t2/help/en_US/reference/#Developer) . Die Optionen im folgenden Beispielcode ( `account`, `visitorNamespace` und `trackingServer`) sind erforderlich und die Werte werden von Adobe bereitgestellt.

   >[!IMPORTANT]
   >
   >Sie müssen sicherstellen, dass die Abhängigkeitskette korrekt eingerichtet ist. Die AppMeasurement-Instanz aggregiert (abhängig) die Besucher-API-Komponente.

   ```js
   var appMeasurement = new AppMeasurement();
   appMeasurement.visitor = visitor;
   appMeasurement.trackingServer = 'URL_OF_THE_ADOBE_ANALYTICS_TRACKING_SERVER';
   appMeasurement.account = 'ACCOUNT_NAME'; // Also known as RSID
   appMeasurement.pageName = 'Sample Page Name';
   appMeasurement.charSet = "UTF-8";
   appMeasurement.visitorID = "test-vid";
   ```

   >[!IMPORTANT]
   >
   >Stellen Sie in Ihrer Anwendung sicher, dass `appMeasurementObject.visitor` ausgefüllt ist, bevor Sie den Videoanalysefluss starten, oder Sie erhalten möglicherweise keine Tracking-Ergebnisse. Diese Ergebnisse werden durch die Meldungen in Ihrem Protokoll angezeigt. Sie können einen leeren Verfolgungsaufruf ( `appMeasurementObject.track`) hinzufügen, die Eigenschaft `visitor` abfragen, bis sie gefüllt ist, und Videoanalysen starten.

3. Initialisieren und Konfigurieren von Video Heartbeat-Tracking-Metadaten.

   >[!IMPORTANT]
   >
   >Sie können das Video Analytics-Modul Midstream anhalten und es bei Bedarf erneut initialisieren. Bevor das Modul neu initialisiert wird, stellen Sie sicher, dass die Metadaten für die Videoanalyse auch auf die richtigen Inhaltsmetadaten aktualisiert werden. Wiederholen Sie die Unterschritte 1 und 2, um die Metadaten neu zu erstellen.

   1. Erstellen Sie eine Instanz der Video Analytics-Metadaten.
Diese Instanz enthält alle Konfigurationsinformationen, die zum Aktivieren der Video Heartbeat-Verfolgung erforderlich sind. Beispiel:

      ```js
      function getVideoAnalyticsMetadata() {
          var vaObj = new AdobePSDK.VA.VideoAnalyticsMetadata();
          vaObj.appMeasurement = appMeasurement;
          vaObj.trackingServer = 'hbTrackingServer';
          vaObj.publisher = 'hbPublisher';
          vaObj.channel = 'sample-channel';
          vaObj.playerName = 'TVSDK-HTML';
          vaObj.appVersion = '1.0.0';
          vaObj.videoName = 'hbFriendlyName'; // this will overwrite the ContextData variable a.media.friendlyName
          vaObj.assetDuration = durationInSeconds;
          // use this to override the default asset length of -1 for live streams
          vaObj.debugLogging = false;
          return vaObj;
      }
      ```

   2. Erstellen Sie nach dem Erstellen einer Medienplayer-Instanz eine Video Analytics-Tracker-Instanz und geben Sie einen Verweis auf die Medienplayer-Instanz an.
Beachten Sie Folgendes:

      * Erstellen Sie immer eine neue Tracker-Instanz für jede Inhaltswiedergabesitzung und entfernen Sie die vorherige Referenz (nach dem Trennen der Medienplayer-Instanz).
      * Die Metadaten, die in Unterschritt 1 erstellt wurden, sollten im Konstruktor von Video Analytics Tracker bereitgestellt werden.

         ```js
         var videoAnalyticsMetadata = getVideoAnalyticsMetadata();
         videoAnalyticsProvider = new AdobePSDK.VA.VideoAnalyticsProvider(videoAnalyticsMetadata);
         videoAnalyticsProvider.attachMediaPlayer(player);
         ```
   3. Zerstören Sie den Video Analytics-Tracker.
Bevor Sie eine neue Inhaltswiedergabesitzung starten, zerstören Sie die vorherige Instanz des Video-Trackers. Warten Sie einige Minuten, nachdem Sie das Ereignis zum Abschluss des Inhalts (oder die Benachrichtigung) erhalten haben, bevor Sie die Video-Tracker-Instanz zerstören. Das sofortige Zerstören der Instanz kann die Fähigkeit des Video Analytics-Trackers beeinträchtigen, einen Video-complete-Ping zu senden.

      ```js
      if (videoAnalyticsProvider) {
          videoAnalyticsProvider.detachMediaPlayer();
          videoAnalyticsProvider = null;
      ```

   4. Markieren Sie den Live-/Linear-Stream manuell als abgeschlossen.
Wenn sich in einem Live-Stream mehrere Folgen befinden, können Sie eine Folge mithilfe der vollständigen API manuell als abgeschlossen markieren. Dadurch wird die Video-Tracking-Sitzung für die aktuelle Videoepisode beendet. Sie können für die nächste Folge eine neue Tracking-Sitzung starten.
      >[!TIP]
      >
      >Diese API ist optional und für das VOD-Video-Tracking nicht erforderlich.

      ```js
      if (videoAnalyticsProvider)
      {
         videoAnalyticsProvider.trackVideoComplete();
      videoAnalyticsProvider.detachMediaPlayer();
      videoAnalyticsProvider = null;
      // Create a new instance of VideoAnalyticsProvider to continue tracking.
      }
      ```
